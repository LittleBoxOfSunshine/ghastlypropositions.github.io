---
layout: post
title:  "Eventual Inconsistency: How best effort ruins everything"
date:   2023-04-24 25:00:45 -0800
categories: software
---

`Cannot connect to PostgreSQL database`

That was the innocuous title of one of the most bizare service incidents I've ever worked
on. It took nearly a dozen teams to track down the root cause and while the issue wasn't
novel, the ludicuous way in which is presented itself inspired this discussion.

Functions, algorithms, or APIs are often described as "best effort". In the face of a
problem or uncertainty, the implementation will make a guess at what it should do. A 
face value this seems fair enough. Why condemn your user to failure when there's a 
chance you could succeed? You miss 100% of the shots you don't take after all. ( ͡° ͜ʖ ͡°)

This approach is generally useful in life and even in most user facing applications,
but it's maladaptive when applied to distributed systems. It's critical to distinguish
between times when failure is acceptable from it isn't. While that seems obvious, it's
not always clear when it isn't.

## Hypotheticals

With user facing information, it's typically acceptable to present stale or partial 
data. Ideally it has a disclaimer, but either way the person can evaluate whether or
not what they've been given is usable. How often have you opened an old tab on
your phone where the content is present, but the tab tries to refresh and fails destroying
the content that was just there? Clearly it's better to reserve the stale cache here.

The rest of the engineering world often snubs the concept of "software engineering" and
they've got a point. We do a lot of shoddy work that would never fly in the physical
world, but we're not restricted by it either. However it's easy to get lost in the layers
of abstraction. For this reason, I am a big fan of physical analogies to sniff test.

Imagine that you're on the 18th floor of a building and you learn the steel girders were forged with 
best effort™ practices. They *might* be load bearing to spec, but they also might not be. 
Clearly the logic from before that giving the customer *something* is better than giving
them nothing has broken down here. It is utterly unacceptable to have this part fail 
because other parts in the system (the floors above) are dependent on it working.

When you're working in distributed systems, you're in the skyscraper.

## Eventual **In**consistency

Most engineers are exposed to the concept of eventual consistency when they learn about
NoSQL databases. If we want to scale high enough, it isn't possible to have a fully 
consistent system in which all parts agree on the current state. This is fine in databases
because it is well defined and the clients are written with the concept in mind. 
Individual nodes may behave differently at times, but the overall long term state of the 
system is determinisitic.

What's considered less is how eventual consistency presents in services.

## This Is Why We Can't Have Nice Things

## Application


