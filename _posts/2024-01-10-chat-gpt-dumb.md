---
layout: post
title:  "ChatGPT Isn't Intelligent"
date:   2024-01-10 12:00:45 -0800
categories: software
author: "Chris Henk"
---

> ChatGPT isn't profound, but it's impact will be.

A fun, but less covered type of bias is *Anthropomorphic Bias*. Anthropomorphic bias is the tendency to ascribe humanlike characteristics to things that don't actually have them. It's most commonly applied to human concepts of thinking, reasoning, and motivation. I believe the world's response to ChatGPT has been the single greatest example of this phenomena to have saturated our culture.

ChatGPT is capable of truly impressive Natural Language Processing. It has more or less a full mastery of the English language, can perform complex search queries, solve problems with math or even by generating computer code. It's capable of keeping track of conversation over time, and most critically can understand and react to hints given by the human. It does all of this at high speed, and as a result it can do things that many of us can't do, or in some cases can but at equal or worse quality despite how much slower we are.

## Echoes of the Past: The Turing Test

It's no wonder then that we're blown away by this. Alan Turing famously proposed "The Turing Test" as a methodology to assess a machine's ability to exhibit intelligence that is indistinguishable from human intelligence. This has even made it into the culture somewhat, as many layman are aware of it. The idea is you have a person ask written questions and put them into two slots. Behind one is a human and the other a computer. If the person asking questions can't tell which is which, then the computer has passed the test.

Let's get something clear though, the Turing Test demonstrates that the intelligence, with respect to this task, is *indistinguishable* from a human **not** that is it *equivalent*. This is an exceedingly common misunderstanding. If I search "how do we measure intelligence in computers" into Google, my first three results are all making this mistake[^0]:

1. [What is the Turing Test that determines if computers can think? - ABC News (go.com)](https://abcnews.go.com/US/turing-test-determines-computers/story?id=101486628#:~:text=The%20Turing%20Test%20is%20arguably,learning%20for%20several%20years%20beforehand.)
2. [What is the Turing Test? \| Definition from TechTarget](https://www.techtarget.com/searchenterpriseai/definition/Turing-test)
3. [The Turing Test: What Is It, What Can Pass It, and Limitations](https://www.investopedia.com/terms/t/turing-test.asp)

While I'm not familiar enough with Turing's work to say if he thought it could measure both or not, I concur with philosopher John Searle that the test can't demonstrate consciousness or an equivalence to human thinking. If you'd like an explanation for why, his thought experiment the [Chinese room](https://en.wikipedia.org/wiki/Chinese_room) argument gives an excellent logical breakdown.

> If you really want some existential dread, you can take it further and apply the same type of logic to human brains themselves. For those that find the argument unconvincing, consider this. A digital computer is just doing math, following an algorithm. If it can be conscious, than if I perform the same math in the same order on a gigantic sheet of paper, does that paper and/or the markings become conscious? If neither can be, well then what's so special about your mushy brain that allows it? It seems either all of them must be possible, none are, or we don't yet understand a mechanism that would allow for some to be true and some to be false in a way that's consistent.

There are more fundamental challenges as well. The test uses written text, not speech, so that the quality of the computer generated voice isn't a give away. This belies a significant point, that understanding speech is more difficult than reading is. Firstly, understanding speech is just language + parsing the sound to extract the words. The computer gets the words given in perfect form and is doing a subset of the work. A retort could be well reading with your eyes still requires this first step! But even then, that's still easier. The number of ways the character A can be written is simpler and fewer in number than the number of ways it can be spoken.

> *If the human brain were so simple that we could understand it, we would be so simple that we couldn't*. - A Paradox posed by Emerson M. Pugh

## What Does it Mean to be Intelligent?

This is a hard question. It quickly gets into the "what is truth?" wing of philosophy. So much has to be taken for granted to even begin evaluating the question rigorously. Spend some time thinking how to answer the question "what is a chair?" after considering the basic ideas of [Mereological Nihilism](https://en.wikipedia.org/wiki/Mereological_nihilism) (which would posit that there are no chairs) to get a good feel for what I mean if you're never been exposed to Epistemology before.

Let's not get bogged down there though, and just presume it's fine to start off at the level of Cognitive Psychology. One concept from that field is [g factor](https://en.wikipedia.org/wiki/G_factor_(psychometrics)) or general intelligence. The idea that people have a general level of intelligence that will be predicative of their capacity across a wide number of unrelated activities. There is debate over if such a correlation really exists and if it does how we would measure it.

But again, let's operate under the premise that g factor is real. After all if it weren't, then what does it even mean to ask if ChatGPT is intelligent? *Is it good at lots of individual things?* That's surely not the question, cats are good at lots of things and so are worms.

Raymond Cattel hypothesized that there were two types of human intelligence: [^1]

- **Fluid Intelligence** - "[T]he ability to perceive relationships independent of previous specific practice or instruction concerning those relationships." [^2]
- **Crystallized Intelligence** - Facts and knowledge acquired from prior learning or experience.

I firmly believe that when we discuss this topic colloquially we're describing the concept of fluid intelligence. The holy grail of AI, general intelligence, is AI with human-like capacity to reason, be novel[^3], and to self-teach. Machine learning has always operated under the paradigm of crystalized intelligence. We feed a computer program a ton of data and it builds big linear algebra problems from it. This allows it to find patterns in the data, which it deploys to solve previously unseen problems.

This isn't fluid intelligence. No new "reasoning" occurs. If there isn't a pattern in the data provided, or the input isn't exactly of the form that's tacitly expected, then the program can't generate a reasonable answer. If ChatGPT is intelligent then, it should be exhibiting fluid intelligence and that is what makes it so different than what's come before.

## Is ChatGPT Intelligent?

If we consider true human intelligence to be fluid reasoning and the capacity to combine unrelated things for which no prior observed pattern exists, then no, ChatGPT clearly isn't. To measure this holistically would be quite the undertaking. Instead, let's just consider a simple example.

> Note: This isn't cherry picked, it was literally the first thing that came to mind when I went to find evidence for my argument.

### Primer on Hex (Hexadecimal Numbers / Hex Encoding)

Hex encoding is a way to represent numbers where instead of the decimal system (base 10) each "place" in a number is a power of 16 (base 16). So, instead of a 1's place, 10's place, 100's place (2<sup>0</sup>, 2<sup>1</sup>, 2<sup>3</sup> respectively) you have a 1's place (16<sup>0</sup>), a 16's place (16<sup>1</sup>), and a 256's place (16<sup>2</sup>).

In places where symbols have special meaning like markdown and HTML, one way you can allow for arbitrary inputs including the special characters is by re-encoding to another format. Hex is one such option. Using [a tool](https://www.convertstring.com/EncodeDecode/HexEncode) we can see that the question "*What's the weather today*?" can be represented in hex as `57686174277320746865207765617468657220746F6461793F`.

Once you learn what hex is, your human brain will instantly see and pick out future occurrences. I can't explain why I know hex when I see it, I just do. This can then be applied to new problems. A thing every programmer will eventually encounter when debugging is they're see a bunch of hex they weren't expecting or didn't know was present behind the scenes. They will immediately think to do something they were never taught: Decode this input I don't understand, and see if it yields something that I do understand.

Surely this is the most basic type of true problem solving and self-learning. So if ChatGPT understands both topics (which it does), then surely if it's intelligent or nearly conscious it can surmount this small challenge.

### Example 1: Hex Encoded Prompt

![image-20240120161613469](/assets/img/chatgpt-is-dumb.assets/image-20240120161613469.png)

We're not off to a good start here...

### Example 2: Hex Encoded Prompt with Hint

Ok, but ChatGPT is pretty clever after all and it can do problem solving to some extent. Let's give it a hint and point out that it already knows how to answer this prompt, it just didn't realize it:

![image-20240120161639506](/assets/img/chatgpt-is-dumb.assets/image-20240120161639506.png)

What this really underscores is just how basic the basic problem solving skills the AI has actually are.

### Example 3: Learning from Prior Hints

But let's not do the people at OpenAI dirty, this is still an incredible feat. And it goes further. Not only was the AI able to do something with minimal prompting, it's now learned a new pattern. When I prompt in the same chat with new hex encoded questions, it deploys this lesson on its own initiative:

![image-20240120161806104](/assets/img/chatgpt-is-dumb.assets/image-20240120161806104.png)

Now what's really interesting is when I open new chat windows without the prior context. Did the AI learn my hint? Mostly yes! The examples below were tried months apart in some cases, so the model versions were different. I couldn't find a consistent pattern to what it would do. Sometimes it did everything in one step, sometimes it identified the steps and asked if it would like me to proceed, and sometimes it would suggest what some potential steps would be. 

![image-20240120161806104](/assets/img/chatgpt-is-dumb.assets/image-20240120161806104.png)

![image-20240120161817420](/assets/img/chatgpt-is-dumb.assets/image-20240120161817420.png)

![image-20240120161752546](/assets/img/chatgpt-is-dumb.assets/image-20240120161752546.png)

To be clear, it has consistently learned the concept. What's inconsistent is how it chooses to deploy that new understanding. Remember though, as impressive as this is even if it always worked this still is demonstrating crystallized intelligence, not fluid intelligence. The AI didn't come up with this on its own, I taught it. This is no different at a thinking level than how the people at OpenAI taught it its baseline knowledge. 

## A Reality Check: We're Not So Special

In this sense then, there's nothing new about Large Language Models (LLMs) like ChatGPT. They're not demonstrating a new type of computing, they're not making some substantial leap towards general AI or artificial consciousness. The distinguishing factors are primarily the scale that it operates at (both training and in deployment), the ability to hold a "train of thought" over the course of multiple interactions, and the ability to pull in more data then perform pattern learning on the fly.

This isn't critical thinking, this isn't true problem solving, this isn't the AI being novel in any way, but it doesn't need to be. Even the most basic degree of problem solving where it responds dynamically to new data / patterns leads to ground breaking model performance the world has never seen.

At long last, this is where we come back to anthropomorphic bias. Speech is a major part of the human experience. Yes, other animals communicate, but not like we do. Bees have sophisticated communication where they describe 3D navigation and vote on the best place to start a new hive. But they aren't "thinking" and can't communicate outside of this highly specialized regime. Whereas for humans, our entire world is processed through speech. It's how we interact with others, the environment (written language), and even how we reason / perceive ourselves internally.

I think that's what leads so many of us to overstate what's going on in the computer. ChatGPT is closer to the bee than it is to you or me. If you highly specialize, the system for performing a specific task tends to be quite simple. The reason the human brain is so complicated isn't because it can do speech or navigation, it's because it can do that and more. It can generate new capabilities on the fly as the need arises without any external prompt.

The harsh reality that LLMs lay bare is that most of what you do is simple. Your capacity to learn skills is what's impressive, the skills themselves generally aren't. Again, recall that bees can give 3D navigation directions (entirely from memory) to their peers. In the same way that it's a lot easier to automate soda can production than to build LLMs, building LLMs is a lot simpler than building seemingly trivial things like a general purpose robot hand that can grasp things the way humans do. Think about that! We've been building robots far longer, and yet this success came first.

> Just because we are self aware and experience the world through language doesn't mean that language is so complicated it requires an entity capable self awareness to understand language.

## Replaceable Parts for the Abstract

The progress of AI leads many to focus on the wrong topics. We discuss if we're approaching general AI or artificial life even though we're clearly not. We then discuss the consequences of that, will AI go rogue and destroy the world? I've always found this to be short sighted way of thinking, ironic given that it's considering the far future. Elon can wax poetic about it as much as he wants, but the first order concern with AI isn't general AI[^4].

ChatGPT shows that AI can already do the "simpler" tasks that we do faster and sometimes even with higher precision. Precision is a sore spot, but that only gets better with time. For many tasks, it's close enough that it's better to replace a team of 10 workers with ChatGPT + 2 workers checking the output. If you're looking to worry, that's far more concerning than a Terminator scenario.

One of the most important developments of the industrial revolution was the advent of replaceable parts. Once machinery was precise enough, it was possible to create the same piece the same way at scale, where it can be swapped out with any other previously manufactured piece. Suddenly, very hard tasks that required years of craftsmanship skill building where extremely easy. Building an early gun or engine was slow and expensive as a result. With replaceable parts not only is it easier, in areas where precision matters the quality can even be higher as well. There's just no human on earth that is going to make a perfectly smooth piston for your car's engine.

This concept (breaking down a problem into smaller, simpler parts that can be done at scale by cheaper means, be they automation or lower skill workers, is what builds our modern economy. Notice I said *problem* not *product*. The same ideas of interoperability and simplification apply to the abstract domains as well. The entirety of computer programming is built on the idea of ever increasing layers of abstraction that make problems easier and more efficient to work with.

Basic automation and leveraging cheaper workers devastated the rust belt. AI is this same thing on a whole other level. It takes time and money to build factories. I can deploy or upgrade software instantly and for essentially free. As AI improves it will have a profound impact on the world, because it's the thinking equivalent to the first machines and factories of the industrial revolution.

Just as they changed the world and forced its people to adapt, so to will ChatGPT and the rest of the LLM revolution.

[^0]: The articles all might go on to explain properly, I didn't read them. I just found a snippet with the wording I described.
[^1]: [How General Intelligence (G Factor) Is Determined (verywellmind.com)](https://www.verywellmind.com/what-is-general-intelligence-2795210)
[^2]: [Age differences in fluid and crystallized intelligence - ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/000169186790011X?via%3Dihub)
[^3]: It's worth noting, "novel" as a concept is one of those "what is truth questions?". You can make sound arguments humans aren't capable of novel thinking either. So for our purposed, we just mean in the common sense the word is used.
[^4]: Before AI is conscious it will long since have been able to replace all of our jobs, which under our current system would lead to the collapse of society and thus prevent the future concerns. Even if it wouldn't prevent it, we surely can at least agree we need to tackle the more immediate problems first.
