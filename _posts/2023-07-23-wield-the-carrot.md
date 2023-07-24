---
layout: post
title:  "Wield the Carrot as a Stick"
date:   2023-07-23 12:00:45 -0800
categories: business
---

> *Some prefer the carrot, others the stick. I prefer to wield the carrot as a stick*

Humans are fundamentally lazy and self servingly work avoidant. You intuitively know this to be the case as a software engineer. One of the foundational mantras of the discipline is "Don't repeat yourself". Well written software is extremely modular and infinitely scalable (just copy it). On top of that, the people that write the software are incredibly expensive. It's no coincidence then that the best developers are those that judiciously deploy *net laziness*.

Net laziness, as opposed to greedy laziness, looks over the time horizon and makes the decisions that will result in the minimal amount  of aggregate effort over that given period. This is a form delayed gratification, which software engineers tend to score better at than the average person. Getting a job often requires finishing a degree with unrelated work, and programming has a high initial learning curve. It takes a fair amount of investment before you're skilled enough to do anything interesting or useful.

You would think that means programmers are well positioned to coordinate well in groups, but challenges do exist:

- Undisciplined culture
- Decentralized
  - This is a major net win, but there's no silver bullet and this is one of the negatives.
- Lack of direct incentives
  - What's best for the group may not have not be best for you individually, think [tragedy of the commons](https://en.wikipedia.org/wiki/Tragedy_of_the_commons).
  - Without a clear [price signal](https://en.wikipedia.org/wiki/Price_signal), you may not even realize an action should be taken.
- The [bystander effect](https://en.wikipedia.org/wiki/Bystander_effect)

Contending with these issues of human psychology is a perennial struggle, but I want to share a quaint strategy I've come to rely upon to get teams to complete administrative tasks so that you can focus your attention on the problems that actually matter.

You'll often hear sayings like it's easier to catch flies with honey than vinegar or that negative reinforcement isn't as effective as positive reinforcement is (the carrot vs the stick), but those adages aren't always applicable. Consider tasks that are unpleasant or uninteresting, infrequent or a one-off, and the non-completion of the task has no impact or even selfishly positive impact on the person.

I can't bait them with honey, as the trap is transparently obvious. Positive affirmation doesn't work as the value of the praise is less than the cost of the action. Beyond that, we can't have organizations where unpleasant work is just avoided, nor is it acceptable to expend substantial effort or rewards to coerce or convince people into compliance. At the same time, the psychological limitations exist and running around with a stick beating people into submission isn't going to foster the productive environment we're looking for either.

The carrot or the stick is a false dichotomy. What if instead, we were to wield the carrot as a stick? What if we devise the incentives of the task such that compliance confers benefits and continued non-compliance confers punishments? As an example, one of the projects my team owns is a *massive* legacy product with labor intensive deployments. Deployments are so involved it requires an assigned release manager to spend roughly half their time managing it.

Since that product releases monthly, we assign a release manager each month. The team is so large that you never end up needing to do it twice. Recently we changed the queue so that people are automatically added as a part of onboarding. This meant we needed to do a one time cleanup to get people who were missing in the last year of hiring onto the list.

Going through a list of 100 people is a phenomenal waste time, and it wasn't possible to get all the information. Instead I sent an `ACTION REQUIRED` email marked important requesting people self identify that they haven't done this really unpleasant task that provides no career benefits. As expected, that didn't work well, and I only got 3 responses. 

Some might say well people miss emails! I didn't buy that as the full explanation. Plus, call me a hardass, but I expect you to keep your email inbox in check. After 2 days I politely bumped the task, thanked the people who responded, then said:

> As an incentive / reward for not making me hunt you down, the earlier you respond the more favorable your scheduling will be 😉 

And sure enough, within the hour I had a dozen more responses and I got quite the amused response from bystanders. As effective as it is, you must do it correctly or else it will backfire in other ways. When done correctly, this is a powerful method to get groups of people to do administrative tasks.

Keys to success:

- For the initial period, all who comply must be treated equally. Otherwise you create a toxic competition between team members, and lead to inefficient outcomes such as constantly checking your emails for new tasks.
- Make the outcome and incentives painfully clear, preferably in a way that scales with time for continued non-compliance. If the first round was via email only, make sure this one is also in your messaging app (this has the added bonus of incentivizing people to keep better email hygiene).
- Keep edge cases in mind. If someone is on vacation, don't punish them for not responding.
- If you're trying to build a list of assigning work to, make sure it's not possible to escape by remaining silent. Most people will comply promptly, but other actors will wait and see. It's extremely important that is not allowed to happen. Not doing so was a mistake in my example above. Either:
  - Have a full list in mind, knowing then who didn't answer
  - Request all people to take a survey, where they should demonstrate why they are exempt (make it opt-out). In my example above, you could ask people to list when their rotation was and anyone who fails to do so will be assigned again.
