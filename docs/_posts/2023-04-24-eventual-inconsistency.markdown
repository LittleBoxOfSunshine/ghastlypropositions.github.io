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
they've got a point. We're not restricted by the physical world, so we rightfully do a 
lot of shoddy work that would never fly there. But it's also easy to get lost in the 
abstract world and build things that don't make sense. Physical analogies can bring us
back to reality.

Imagine that you're on the 18th floor of a building and you learn the steel girders were forged with 
best effort™ practices. They *might* be load bearing to spec, but they also might not be. 
Clearly the logic from before that giving the customer *something* is better than giving
them nothing has broken down here. It is utterly unacceptable to have this part fail 
because other parts in the system (the floors above) are dependent on it working.

When you're working in distributed systems, you're in the skyscraper.

## Eventual **In**consistency

Most of us are exposed to the concept of eventual consistency when we learn about
NoSQL databases. If we want to scale high enough, it isn't possible to have a fully 
consistent system in which all parts agree on the current state. This is fine in databases
because it is well defined and the clients are written with the concept in mind. 
Individual nodes may behave differently at times, but the overall long term state of the 
system is determinisitic.

Eventual consistency is also present in places like DNS. When you change DNS records, there are layers of caching from the registries themselves down to individual devices. This is also how cloud computing works. When you provision a new VM, a server will update a database tracking VMs and a provisioning service target a host for it. The host then must take time to create and configure the VM. 

There are lots of tricks to decrease this time, but at the end of the day the provisioning will always be a delay where the system is inconsistent. The VMs in the targets will not match those provisioned in the datacenter. But where are the constraints to ensure that consistency is acheived? There is no consistency model, no parameters to tune. There is no contract between each layer in the stack or application you can deploy to abstract away the problem.

In practice this was a gross oversimplification of the process. There are dozens of services involved in this change events and a mix of code from different companies. Every layer must understand the guarantees its depencendies offer to determine what guarantees it can offer and the performance will be reduced to that of the lowest common denominator. Best effort is nothing short of poison in this environment.

Let's be clear on definitions. Best effort is not fault tolerant. A fault tolerant system understands what externally can fail and includes strategies to reduce the impact of failure. If those mechanisms then fail, it will still land in a *well defined* state. This could be a poison queue of events or simply returning 5XX error code in a REST API. 

Best effort lands in an *undefined* state. When this happens in a distributed system, the failure will ripple up the dependency chain in unpredictable ways. When you violate the invariants of your dependents, they too enter a state of undefined behavior. 

## This Is Why We Can't Have Nice Things



## Application


### As the producer


### As the caller


