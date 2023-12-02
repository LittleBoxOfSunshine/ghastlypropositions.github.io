---
layout: post
title:  "Truly Minimum Books for Software Engineers"
date:   2023-11-29 12:00:45 -0800
categories: software
---

> As with all things in life, keep the 80/20 rule in mind

As a child, I was a voracious reader and it served me well. I'll confess that as and adult I read much less. As I get more experienced, less and less still with respect to professional books. I think this checks out though. Once you have your base fleshed out, what you really need are dense, specific material. These days I find I read blogs, white papers, and standards documents. I'm still learning, it's just that the best medium for me has changed.

But when I was getting started my first few years as a professional developer, these books were very formative in expanding my world view and changing how I approached things. I firmly believe that everyone should read them. That's why the list is short, it's hard to find something that *everyone* should be doing despite how different they are from one another.

The list, which I recommend in order:

1. [Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship-ebook/dp/B001GSTOAM/ref=sr_1_1?crid=I2HAIMHSI9W&amp;keywords=clean+code&amp;qid=1701498174&amp;sprefix=clean+cod%252Caps%252C274&amp;sr=8-1&_encoding=UTF8&tag=ghastlypropos-20&linkCode=ur2&linkId=d3b1317b50f58b183ff03464d56a4606&camp=1789&creative=9325)
2. [The Design of Everyday Things](https://www.amazon.com/Design-Everyday-Things-Revised-Expanded-ebook/dp/B00E257T6C/ref=tmm_kin_swatch_0?_encoding=UTF8&amp;qid=1701498408&amp;sr=8-1&_encoding=UTF8&tag=ghastlypropos-20&linkCode=ur2&linkId=9a4bd7a7f9bafb73beb39e262d1d7dec&camp=1789&creative=9325)
3. [Cloud Architecture Patterns](https://www.amazon.com/Cloud-Architecture-Patterns-Using-Microsoft-ebook/dp/B009G8PYY4/ref=sr_1_1?crid=1Z19TII6U9MVD&amp;keywords=cloud+architecture+patterns&amp;qid=1701498489&amp;sprefix=CLOUD+ARCHITEC%252Caps%252C177&amp;sr=8-1&_encoding=UTF8&tag=ghastlypropos-20&linkCode=ur2&linkId=4392ab419e2e309e63faaf56589d422c&camp=1789&creative=9325)
4. [Extreme Ownership](https://www.amazon.com/Extreme-Ownership-U-S-Navy-SEALs-ebook/dp/B0739PYQSS/ref=tmm_kin_swatch_0?_encoding=UTF8&amp;qid=1701498537&amp;sr=8-1&_encoding=UTF8&tag=ghastlypropos-20&linkCode=ur2&linkId=bd33d09e6830305c3030a0cd81b33537&camp=1789&creative=9325)
5. [Building Microservices](https://www.amazon.com/Building-Microservices-Sam-Newman-ebook/dp/B09B5L4NVT/ref=sr_1_1?crid=EJN8JS45JGG0&amp;keywords=building+microservices&amp;qid=1701498602&amp;sprefix=building+microservices%252Caps%252C142&amp;sr=8-1&_encoding=UTF8&tag=ghastlypropos-20&linkCode=ur2&linkId=a7a380c058973d3801d72f4362f4e3e0&camp=1789&creative=9325)

## But Why?

Books are a great way to build a base of knowledge. It's a broad survey of a topic that's still detailed. Most importantly, it requires dedicating time and space to the topic. When you're starting from 0 on a topic, you need to create the right environment to take it all in.

Ok, but why these specific books? I think they cover topics that are critical to your success: 

1. How to write code. This is the core of what you do, you can't just be good at it. You need to be excellent. 
2. How to design, work with others, diagnose issues, and lead. It's a team sport. With modern tech small teams can do a lot but you need teams. For the most interesting work, you need many teams
3. Introduction to modern concepts. School just doesn't introduce you to cloud architecture well, and most products are poorly constructed shoddy nonsense. Many of your colleagues have never worked on a modern product. If you don't seek out the introduction, you can miss it for years. Maybe even for a career. 

The order is weighted by importance/roi but also alternates between technical and non technical to keep things from getting stale.

### Clean Code

This is a widely renowned book, but also is controversial to some. Keep in mind, this book is ideological in nature. It will present all the ideas in their extremis. Just because you won't want to follow every recommendation out of expediency (a choice I support and follow myself) doesn't mean the core ideas are wrong. 

This book isn't really presenting anything you don't already know. Don't repeat yourself, keep things decoupled, organize properly. The book is codifying and exploring the implications of these principles you already know and believe and challenges you to ask if you're living up to them. Are you consistent? Or have you been lazy and complacent at times? To get the most out of it, you should already have a few years of experience (school counts here) before reading it.

I don't follow everything to the letter (try / catch topic is one such example), but I'm a strong adherent. This book really is pitching two claims:

1. Single Responsibility Principle
2. Name things properly

If you follow these two ideas, everything else naturally follows. Any design pattern is just a method of achieving these goals.

### The Design of Everyday Things

Design isn't just UX in a web app, it's a general set of tenets for how to make better products. Approaching this topic from a non software point of view crystallizes this and builds a foundation in accordance with the theme of my recommendations. Moreover, many of the examples are design flaws and enhancements that are derived from postmortems and root cause analysis on failures and accidents.

*The Design of Everyday Things* isn't just a set of design principles. It shows how to think about failures, and how to build better systems . We have a natural desire to find the *person* to blame, but Norman encourages you to look deeper. When we blame *systems* and *incentives*, not people, we build better systems and create a better working environment that makes work more pleasant and encourages people to contribute and engage honestly.

### Cloud Architecture Patterns

The book is a little dated in some ways, but it's less dated than your school curriculum! What I value about it is that it's a short survey of the fundamental principles of cloud computing, and how to think about failure, scaling, and architecture in the modern world. Sure, you can do everything yourself. But when you learn what tools are available to you, you can accomplish great feats with remarkably little effort.

For newer offerings not covered, the principles underlying them are the same. With this foundation it's easy to read product docs and pick up additional offerings as needed.

### Extreme Ownership

Jocko Willink is among the most accountable people you will meet in life. His world view focuses on a blend of ownership, discipline, and service. Individualism and meritocracy can be dirty words these days, but the reality is there is still a lot of mobility in America. *Extreme Ownership* encourages you to look within. Sure bad things happen that are out of your control, but did you respond correctly? Did you exercise the amount of control you do have? Are you waiting for others to do what they should or are you jumping in, taking the initiative, and leading by example?

Much like *Clean Code*, this book does a good job stating core internal beliefs you probably already have and then challenging you to think them through to their conclusions and ask if you're truly living up to them.

### Building Microservices

Now that cloud services exist and can abstract away much of what is involved in the infrastructure of high scale systems, the micro services pattern is more effective than other. Beyond the technical merits and the alignment with off the shelf offerings, I personally believe the most underrated aspect of micro services is that they align so well with [Conway's Law](https://en.wikipedia.org/wiki/Conway's_law).

Even when working in a monolithic product, the type of thinking that is involved still improves your design and reasoning skills, which will lead to better monolithic products. After all, the monolithic is an illusion. It's abstraction all the way down.

## Seriously, That's It

No bulleted list you need to scroll to read, no broad sweeping recommendations along 12 verticals with multiple books per vertical. There's nothing wrong with going deep, but I don't think it's wise or accurate to pitch here's the mountain of reading you need to do to achieve basic competence. This is a foundation, and you should explore more topics and additional resources to meet your growth needs as they occur.
