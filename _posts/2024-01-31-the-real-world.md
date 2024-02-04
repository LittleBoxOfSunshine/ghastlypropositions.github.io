---
layout: post
title:  "The Real World"
date:   2024-01-31 12:00:45 -0800
categories: business
author: "Chris Henk"
---

> In that big scary place called *the real world*, no one is going to pay you to solve a problem that's already been solved. - Dr. Mark Fontenot

One of my clearest memories from college was during the introduction of the first lab assignment in my Data Structures class. At my school, data structures was the weed out class. Not because it was C++, not because the tasks were harder and more abstract, but because it was the first class where you were given a *problem* to solve rather than told *what* to do. It was the 3rd CS class and where the training wheels finally come off.

In the second week of the class our professor was introducing the first programming assignment. He went over the prompt, which described the user scenario. A company was migrating a permission system from one product to another, and the settings files were of different formats. You were given a sample input file, a key that explains how to decode the numeric permissions (think Linux file system permissions), a sample output file.

Keep in mind that up until this point any assignment a student had received, even in CS classes, was one where the procedure was clearly outlined. You were told what to do, how to do it, and probably even given an interface or starter code to target. The room was pretty quiet. There wasn't dread or concern, but it was clear that most were waiting for more. After a pause one student spoke up and asked what the starter code would look like. We were told there is no starter code. Then they asked what strategy we should use to solve the task, and we were told that's the purpose of the task.

This repeated once more in different words, then the student asked a third time. We didn't know our professor well, but you could tell that there was some biting of the tongue as he reset for the next wave of young minds. He looked from left to right, scanning up the rows as he does so. Rather than addressing that student directly, he simply stated to the room "In that big scary place called the real world, no one is going to pay you to solve a problem that's already been solved". And that's how the class ended.

## The Real World

This wasn't a profound statement, we all intuitively knew it to some extent. But something about the delivery of it stuck with me. In a single sentence he had concisely laid out the way the world works and the skill set you need to acquire to succeed in it. There aren't tests to take or figures to regurgitate. You're going to be given novel work and expected to figure it out. If you don't know how to do it, well then you need to go solve that problem first. You need to learn to learn.

After all, if it isn't novel, well then why the hell am I paying people to do it? The lesson applies in the reverse as well. As a business owner, manager, or project lead, if you're paying people to "solve" solved problems, there's something fundamentally wrong with the way you are structuring your business and products. 

> As a clear example, in my early days working on Azure IMDS I did some serious refactoring of the product and wrote a custom REST microframework in C++. The fact that it was good, highly valuable work was a major smell. Clearly that software wasn't being developed correctly if that just now was happening, and why was there no suitable way to use an off the self solution for a problem (REST routing) when there are literally 100's of existing options?

If you're just getting started in your career or trying to get ahead, you'll hear lots of advice like:

- Go the extra mile; but set boundaries
- Make yourself irreplaceable
- Do the job no one else wants to do

This is all good advice, but if we peel down another layer the fundamental skill is you need to learn how to learn. Often times the "hard" work people are avoiding is only hard because they don't know there's a better way to do it. A person that learns the tough, rare skills is indispensable. Someone who learns on the job is ahead of their peers and has the leverage to draw boundaries where needed as a top performer. Problem solving itself is a learned skill. The better you get at coding the better you get at making a kitchen more efficient and vice-versa.

## How School Fails You

Unfortunately, you spent the first 20 or so years of your life doing the exact opposite. You're given a list of things to memorize, or a clear procedure to follow. Even in the more abstract classes like math, you're not really applying critical thinking until you get to around Algebra, and even then nothing you're doing requires being novel. Your given formulas, or a set of formulas, or a set of patterns, and told to repeat the action. In the harder cases, you need to figure out which predefined procedure to follow.

Think of the difference between learning a difficult song on the piano vs composing one of your own. Even just following procedure can be hard with enough complexity, but it isn't going to translate into you being able to compose your own music now. Learning proofs in geometry is getting a little closer to what programming is. You are given a bunch of tips and tricks where someone else did the hard work to "compose" this new pattern you can then apply to other problems.

The issue in programming is just that your toolkit is so small, that you tend to occupy a weird middle ground that I haven't encountered in other disciplines. Most problems you will solve aren't actually hard. Nothing "novel" is being contributed to the field of computer science as a result of your day to day work. However, it's also not quite as trivial as which patterns do I need to use either.

### Undoing The Damage

Getting on the right path is straightforward but uncomfortable. You need to work on general problem solving skills and this just comes down to practice. It's going to be hard at first. Any skill that requires novelty will partially transfer to others though, since that pattern of thinking is common to each problem just with different considerations and base inputs. You will need to practice your specific skill at some point, but you'll notice the more of these you acquire the easier the next one is.

The other skill to keep in mind is self learning. Remember, most of the work done in the world is in that "semi-novel" space, no one has done exactly what you need to do, but your also not trying to make any breakthrough discoveries or produce work that's reusable by others in most cases. Focus on learning how to ask questions, do research, and to repurpose learnings or ideas from others.

### Learning to Learn From Your Peers

A lot of advice here is kind of like telling you the way to learn to fly a plane is to get in, then fly it. That's because these are big topics, a short blog isn't going to fully address them. The other reason is while you can find a map, you still need to make the journey yourself. My goal here today is to bring it to your mind, provide a framing that I found really resinated with me, and to get those factors to push you into following this call to action.

That said, here are a couple pieces of concrete advice I find myself giving often:

1. When you join a new team, project, or area, start the obvious way by reading documentation, getting overviews from experienced people. Make careful notes, with extra focus any time an assumption, rationale, or non-obvious claim about the system is made. As a new person, you have a unique advantage. You're totally free of the group's status quo bias and blind spots. You can interrogate the code (or other project) as you work through it, finding inconsistencies, gaps, or unexpected behaviors. Bringing these items to the group improves overall quality, increases your understanding, and builds the type of investigative and connect the dots type skills you need to succeed in self learning.
2. When asking your peers a question, include the context of what you've tried. Mention what you've considered or if you've narrowed down to some potentials list them and explain why you consider them potential contenders. This makes communication easier and by showing effort your peers are more willing to invest in you. Demonstrating to those around you you're worth investing in yields more investment which yields greater personal growth.
3. This is advice I often give to mid-level or even senior developers when they're underperforming in this area or lacking the degree of independence that is expected. Some of this is more so how to collaborate better, but I consider that on topic because these items where unwarranted confidence is deployed leads to this type of underperformance. If you're off on your own and doing things your way, often when it comes time to merge it's all wrong.
   1. Keep your ego in check. If you're new to a topic or area, you might be a beginner again. Your prior knowledge isn't as (immediately) transferable as you might think it is
   2. Adopt the scholarly mindset from #2 and try to frame things in how your prior experience approached things versus the current to make neutral factual compare and contrast. Don't assert which is better. Create space for input, new information. They might be ignorant of your better way, you of yours, or both are valid and context (that you probably lack) dictates why one is preferred over the other here.
   3. Check in across levels, not only with your peers and those ranked higher than you. You miss out on a lot, but of special significance here is any contradictions between those of varying levels of experience they're unaware of
   4. When your plans don't work out or you miss schedule, pause and do a retrospective. What went wrong? What was different in this new environment that was incompatible with the way you've been successfully approaching things earlier in your career? Is it a temporary issue caused by the learning curve, or is there a permanent lesson to be gained?
   5. Check in early and often. You should always do this, but it's extra important during the transitionary face when your probability of error is much higher.
