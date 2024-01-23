---
layout: post
title:  "Should Recoverable Errors Be Recoverable?"
date:   2024-01-17 12:00:45 -0800
categories: software
author: "Chris Henk"
---

> Just because you *can* do something doesn't mean you *should*. If there's no upside to allowing something, no matter how small the downside is, it shouldn't be allowed.

Errors are everywhere, lurking. The only way to wholly avoid them is to never interact with the outside world. This isn't a good solution, it'd be like making sure your website isn't hacked by shutting it down. While education focuses a lot of the mechanics of error handling systems in code, there's less emphasis on how to interact with them.

Let's go back to basics today, and think through what classes of errors exist and how we should respond to them. This article is inspired by debates I had while designing a library for some systems software at Microsoft.

## Recoverable vs Non-Recoverable Errors

At the highest level there are two types of errors you can encounter in software, recoverable and non-recoverable. Recoverable errors are those that can be handled, safely ignored (this is generally bad to do!), or otherwise leave the system in a known good state and thus it's acceptable to continue. Whereas non-recoverable errors leave the system in an undefined, ambiguous, or otherwise bad state where it's impossible to take any action at all or it's not possible to safely take one.

Modern languages do a good job reinforcing this concept by having different error handling mechanisms for each class of error. For example, in the programming language [rust](https://doc.rust-lang.org/book/ch09-00-error-handling.html) there is the Enum `Result<T, E>` for recoverable errors and the macro `panic!` for non recoverable errors. `panic!` will halt execution and go to a global handler or just terminate the program. The key element is that you're exiting the normal flow of execution. Whereas `Result` is just a normal type that is returned by a function and normal processing continues.

The part you have to contend with as the programmer is accurately classifying the type of error you're working with. The main mistake people make is overclassifying errors as non-recoverable. Let's say you have a website where the database connection fails or a command line program where user input is bad. Neither of these are non-recoverable errors even though it's impossible to fulfill the requested action. Remember, non-recoverable errors put you in a non-deterministic state. There's nothing non-deterministic about a connection failure or bad input, you can detect this error and handle it by reporting a failure back to the caller.

This is why the design of modern languages is good, using the non-recoverable mechanism is uncomfortable, tedious, and doesn't really let you add code to handle the panic. This is steering you in the right direction. If you're errantly classifying an error as non-recoverable then go to add some handling code, it's not really going to work. This steers you to use the recoverable mechanism like you should be.

### But is it *Really* Recoverable?

The opposite problem can also arise in two ways. Either an error appears recoverable even though it really isn't or it's easy to determine a handled state and therefor a handler is implemented even if it would be better not to. This is where the mechanics of a modern language can actually lead us astray, particularly when consuming library code. A library author can't know if the fault is recoverable or not, it depends on the consumer's use case. In general it's best practice to treat errors as non-recoverable in library code and leave the decision to the caller.

However, that's still a decision you need to make! Just because you are given a recoverable error, doesn't mean it should stay recoverable. When might we want to convert recoverable errors to non-recoverable ones?

## Human Error? No, Bad Design

As mentioned in my [recommended books]({% post_url /_posts/ /_posts/2023-11-29-minimum-books %}) post, I'm a fan of Don Norman's [The Design of Everyday Things](https://www.amazon.com/Design-Everyday-Things-Revised-Expanded-ebook/dp/B00E257T6C/ref=tmm_kin_swatch_0?_encoding=UTF8&qid=1701498408&sr=8-1&_encoding=UTF8&tag=ghastlypropos-20&linkCode=ur2&linkId=9a4bd7a7f9bafb73beb39e262d1d7dec&camp=1789&creative=9325). In that book, there are chapters explaining that most of what is chalked up to human error is really in practice a consequence of bad design. The idea we are concerned with today is the notion of *Constraints* in design:

> Constraints powerful clues, limiting the set of possible actions. The thoughtful use of constraints in design lets people readily determine the proper course of action, even in a novel situation. - Don Norman

One of the most effective mechanisms good design can employ are *Forcing Functions*, a type of *Physical Constraint* prevent or stop the continued improper use of a system. Examples include Interlocks, Lock-ins, and Lock-outs. Interlocks are sequences of actions that are required to happen in order (maybe continuously) in order for something else to happen. It's common for trains to have a "dead man's switch" where the operator must hold a lever to continued advancing. Thus, if the driver collapses for some reason, the train will automatically begin to slow down and come to a stop.

What are some heuristics we can deploy to find instances where forcing functions should be implemented? A litmus test I strictly follow is that if there is no possible upside to an action, it's outcome can be only neutral or negative, then it must never be allowed to occur no matter how small the negative consequence is. This is a simple test of cost vs benefit.

You're already employing this line of argumentation whether you recognize it or not because it underpins common coding best practices. When considering encapsulation, you want the inner state of an object to be private whenever possible and as the default. Same applies for functions on a library. If there isn't a current requirement, neither is made accessible to consumers. This is because it increases opportunity for error and increases maintenance surface area (e.g. public library functions can't have breaking changes).

Still, this often feels pedantic to people in practice. If it's small then why does it matter? I'm not saying you should always go back and fix items that already exist that fail this test; that should decision should be weighed against the cost of making the change. However, when constructing new things why allow such cases to be introduced? The argument at PR or design review time usually goes something like "*sure, I guess that's accurate, but it's not a big deal and I already did it this way*".

There are two flaws with this argument. First, you only *think* it's a small negative possibility. By definition, you haven't actually evaluated that with any rigor if you're employing this response. Otherwise you'd make an *affirmative argument* (meaning you'd argue why it *should* be this way instead of pushing back against arguments why it *shouldn't* be this way). Second, in game theory terms this is a repeated game. You will make future changes. Even if the cost of fixing it is higher than the cost of it remaining, it's better to fix it. The developer will learn and has a strong incentive to think this through up front next time, in which case the better outcome materializes without additional cost.

Recoverable errors are one such case. Just because you can make it recoverable doesn't mean you should.

## Application to Recoverable and Seemingly Recoverable Errors

At Microsoft, my main responsibilities are working as the technical lead for the Azure Instance Metadata Service ([IMDS](https://aka.ms/azureimds)) and as a contributor / maintainer for an internal open source SDK for systems programming targeting [Azure Boost](https://learn.microsoft.com/en-us/azure/azure-boost/overview). 

### Falsely Recoverable Errors

Several years ago I realized that there were situations where different IMDS targets had different configuration files with errors in them. The reason this would go unnoticed was because the executable also had default values for settings, so even if one is missing a value could be selected.

This is an example of an error that *appears* recoverable, but really isn't. Or at least wasn't recoverable in the way it was being attempted. When you deploy a configuration, that's an atomic operation. There's no situation where you're getting a mix of config from document N and document N+1. But this mechanism operated on a per value basis, meaning that if something was missing the system would operate on a combination of the implicit *default* document embedded in the executable and document N provided in the production environment.

That's not a situation you want to be in. While not in the literal sense, from your perspective this is **undefined behavior**. It's a scheme you never considered, nor tested for. This is a case where something started recoverable (a json library returned key not found) but it shouldn't have stayed recoverable. Either you need to change the mechanism or you need to accurately classify the failure. My solution was the latter. I removed the defaults from IMDS and crash if there's anything wrong with the configuration file. More on why this is ok in a massively distributed service below.

### Potentially Recoverable Errors

As a hypothetical, let's consider the configuration example but implemented in a way where the default document is applied atomically. That is, if anything is missing or wrong with the input file, none of that file is used and instead all baked in defaults are used. In this scenario, it truly is a recoverable error. Why did I opt for the solution above instead of just doing this?

When you have a situation where you can recover, you still shouldn't if you meet these criteria:

1. The error is a result of an error made at author time (notice, I didn't say compile time).
2. Crashing increases visibility and/or acts as an interlock preventing deployment.
3. The impact of the decision to fail unrecoverably is contained.

In the case of configuration, there's no valid reason for that error to ever occur. If it does, it's because someone messed up. The code was written incorrectly, or a corrupted config file was deployed. Thinking back to our litmus test then we should strive to prevent this from happening.

Those familiar with operating a system at scale may note that seems fine in theory, but in practice production is complicated and all sorts of errors might occur. If we're crashing, that can lead to an outage. At least if we utilize a default configuration the system keeps running.

I believe this line of thinking makes two mistakes. Firstly, it assumes an implicit failure is ok. It isn't. If I deploy config X and config X isn't actually be applied to my fleet in whole or in part, that's a major issue. Secondly, it doesn't cause an outage if your infrastructure is properly designed.

#### Safely Forcing Recoverable Errors to be Non-Recoverable

In Azure we have a set of rules called [Safe Deployment Practices](https://learn.microsoft.com/en-us/devops/operate/safe-deployment-practices) (SDP). This is because Azure is a giant, complex system. Failures are going to happen, and we need to make sure that when they do they're contained. For our purposes today, the aspect that's relevant is that we deploy changes (to code and configuration) slowly and in stages. There are test clusters, canary clusters, and even with full production clusters it goes slowly region by region, automatically halting if there's an increase in failures.

What's nice about leveraging application crashes as our failure signal is that nothing special needs to be built. Every part of your process already has to account for application crashes in some way, this is reusing that infrastructure.

For those of us working in environments where this mechanism exists, it's something we should lean on. We can do better than detect issues after we enter an unpredicted or non-deterministic state, we can make them *impossible*. By crashing when this problem occurs, we cover all of our bases:

- A dev on their local setup will have their change immediately break them.
- A PR build or release build running as part of continuous integration with bundled configuration will fail before it's merged or published for deployment.
- A bad out of band configuration roll out will not be allowed to continue, it will fail on the first possible stage due to an increase in crashes.
  - I want to make it really clear, the reason this is ok is because it's impossible to rapidly roll out a config change that's resulting in crashes in Azure. If your organization makes it possible to rapidly deploy things out of band without safe guards, crashing is not the right answer. Instaed you must have a mechanism that puts you back into the last known good state and raises the alarm.

For all these reasons, the configuration library and deployment system we use in the internal Azure Boost SDK is implemented in the same way IMDS is. If the configuration is bad, we crash.

#### I Don't Have SDP-like Automation, What Can I Do?

A tried and true method is to use conditional compilation with debug asserts. Have the debug assert crash, but only in your test builds. In this way you still detect issues that happen as a part of normal development work. However, if you have an issue caused by changes to production you respond by operating in a suboptimal state instead of with an outage.

The production implementation of debug assert still needs to be highly visible. When it triggers, it should be automatically creating a high severity incident according to whatever process and tools you use to monitor service health.

Again though, really consider if this is actually "better". If you're going into the last known good state / rollback, then sure. If you're not, it's suspect. Is applying some arbitrary state really solving the issue, or are you just trading one set of bugs for another? Have you tested that this mechanism actually behaves the way you think it does? As discussed in my first post on [eventual inconsistency]({% post_url /_posts/ /_posts/2023-05-10-eventual-inconsistency %}), this might not be the better path you're envisioning it to be.
