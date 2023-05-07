---
layout: post
title:  "Eventual Inconsistency: How \"best effort\" ruins everything"
date:   2023-05-03 25:00:45 -0800
categories: software
---

`Cannot connect to PostgreSQL database`

That was the innocuous title of one of the most bizarre service incidents I've ever worked
on. It took nearly a dozen teams to track down the root cause and while the issue wasn't
novel, the ludicrous way in which is presented itself inspired this discussion.

Functions, algorithms, or APIs are often described as "best effort". In the face of a
problem or uncertainty, the implementation will make a guess at what it should do. At 
face value this seems fair enough. Why condemn your user to failure when there's a 
chance you could succeed? You miss 100% of the shots you don't take after all. ( ͡° ͜ʖ ͡°)

This approach is generally useful in life and even in most user facing applications,
but it's maladaptive when applied to distributed systems. It's critical to distinguish
between times when failure is acceptable from it isn't.

## Hypotheticals

With user facing information, it's typically acceptable to present stale or partial 
data. Ideally it has a disclaimer, but either way the person can evaluate whether or
not what they've been given is usable. How often have you opened an old tab on
your phone where the content is present, but the tab tries to refresh and fails destroying
the content that was just there? Clearly it's better to re-serve the stale cache here.

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

## What is best effort?

Computers aren't smart. They're exceptionally dumb. Yes, even chat-gpt[^1]. Unlike human users, they are *not* capable of evaluating
whether or not the data they've been given is usable. Inputs must conform precisely to the expectations of the receiver or the behavior
will be undefined. There is no escaping this, as it's fundamental even down to the arrangement of the individual transistors in your
processor[^2].

Failure can be a part of our expectations though. Indeed in cloud architecture patterns you write code that *expects* failure and handles
it gracefully. This raises the question, what's the difference between best effort and fault tolerance? A fault tolerant system can be a
system in which their is redundancy such that if a single sub-component fails, another is in place to fulfill its responsibilities. We see
this in systems where many servers are behind a load balancer. Another type of fault tolerance is the ability to detect a failure and place
the system into a deterministic state. This is the type we are concerned with.

There are many ways to remain deterministic. Bad requests can go to a poison queue, you can log an error and return an 5XX status code, you can pass
the error through to the next layer in the chain if it makes sense to[^3]

This is the critical distinction between fault tolerant and best effort. Best effort may or may not succeed, and failures are not guaranteed
to be marked or communicated. This term is often misused so you may have encountered a function that describes itself as best effort, but
returns a failure signal. This isn't a good description. If you are consistent you would describe almost everything that your program does is best effort.
Even if you disagree, let's proceed with these definitions.

## Eventual **In**consistency

Most of us are exposed to the concept of eventual consistency when we learn about NoSQL databases. If we want to scale high enough, it isn't possible to 
have a fully consistent system in which all parts agree on the current state. It might be tempting to say that this is best effort then, but it isn't. The
rules of the came are clear. If data is written, it takes `X` time to replicate. If multiple conflicting writes occur, they resolved using resolution `Y`.
There is never undefined behavior, errors are predictable (data missing, or stale). We can design our software to account for any faults that occur.

DNS is also eventually consistent, but it doesn't have a formal model in the same way a database does. There is a conflict resolution method in that the data
is centralized by register, but in terms of replication their are no guarantees. This is why you can have issues with DNS. If you register a new domain, one
computer may notice it almost instantly while another may take several days to do so. The data is relatively static though, so the consequences of this are
generally insignificant.

Compare this to provisioning a VM in a public cloud. A server receives the request and writes a new record into a central data store. This store may or may
not have internal eventual consistency. Additionally a provisioning service will get the request and pick a physical server to put the VM on. This is going
to be written in yet another store with it's own delays, and then that change needs to propagate to the host. The host then needs to take time to respond to
the change and actually create and configure the new VM. This is a gross oversimplification of the process and yet we can see it is replete with eventual
consistency.

These are dozens of services coordinating across the world. It's all custom software, so there's no inherent coherency model or application we can export
responsibility to. If you want a database, you can outsource to Cassandra. You can't outsource this, because this is the very product that's being sold to
abstract away difficulty. If you don't create a coherent data model at every layer in the stack, errors will creep in. If you allow for best effort, they will be issues in the skyscraper. It is critical that errors are detected and explicitly handled less you poison the system.

In the same way that an issue with the plumbing under your home can cause the second floor shower to flood, errors lower in the stack will result in 
confusing errors downstream. I like to call such systems "eventually **in**consistent". They work most of the time, but everything is best effort. Eventually
those efforts will fail and introduce inconsistency into the system that it isn't designed to accommodate.

## This is why we can't have nice things

Going back to PostgreSQL, why was the customer unable to connect to their database? The first issue was the database IP address was configured to use the 
second NIC of the VM, which didn't exist. Provisioning took the first look and determined that the information they had been provided by the platform was
corrupted, there was no second NIC. This behavior couldn't be reproduced after provisioning though, responses from the platform always had the full data.

To add further confusion, there were multiple layers in the system acting as pass through, all claiming to have sent the correct data. The originator of the
data also claimed to have generated the config correctly. So what happened? Eventually we determined that in one of the subsystems, each of the NICs are
programmed asynchronously and in parallel. As the NICs are provisioned, they arrive at another service that aggregates them and informs a passthrough tier.

<!-- TODO: local file import isn't working -->
<script type="module">
import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10.1.0/+esm'
</script>

<pre class="mermaid">
graph RL
A[NIC Programmer] -->|1. NIC 1| B[NIC Aggregator] -->|NIC 1| C[Passthrough via HTTP]
A -->|"2. NIC 2 (delayed)"| B
</pre>

This mechanism was best effort. The data originator didn't inform the aggregation tier what the expected final state would be, so it had no way of knowing
when it was done receiving data. The pass through layer trusted the other layers to always accurately report data. If it got no data, it would 503. On occasion, provisioning one of the NICs was delayed. Since the VM was sending the request before all NICs had finished provisioning, the pass through tier got partial data which it faithfully returned.

The order in which these would finish was nondeterministic, and the results were not indexed. So the ordering was also best effort. This ended up being the
source of issues in other incidents. Customers suddenly reported that their NICs were being ordered incorrectly in large numbers. Because the leftmost node
had made recent cache changes, it was presumed by the other layers that was the issue. With much effort, it was demonstrated that what actually happened was the NIC provisioning times had been optimized. Previously they were slow enough that they would end up in the right order. Now that they were faster, the race condition that was always present was rearing its head.

The solution was to inform the aggregation tier up front how many NICs to expect notifications for, and to index the notifications to guarantee ordering. If the request comes to early, the aggregator returns an error.

<pre class="mermaid">
graph RL
A[NIC Programmer] -->|1. 2 NICs Incoming| B[NIC Aggregator] -->|NIC 1+2| C[Passthrough via HTTP]
A -->|"2. NIC 1"| B
A -->|"3. NIC 2"| B
</pre>

## Application

While the bugs here are pretty obvious, the point here is the stochastic nature in which they failed. The failure wasn't localized to the actual source, a
synchronization bug in the inner layers of the networking subsystem. Instead it was allowed to propagate all the way through until it presented in a confusing way, requiring immense expenditure to figure out and negatively impacting the customer. Much like the steal girders, they would have much preferred
that we gave them *no VM* by failing on provision that provisioning a corrupted VM they had to debug. Race conditions happen, but best effort is often presented as a feature and not a bug.

Best effort is not a feature. It is poison for distributed systems. It violates invariants, which introduces failures that are extremely expensive to debug. Our goal should be to root it out at every level and remain deterministic. In the examples we reviewed the producer and the consumer had opportunities to address the issue. Here are the strategies each side should have been applying.

### In general

Be suspicious when someone says it's best effort. Be particularly suspicious when it's brought up in the context of explaining behavior during an incident.
In the beginning we considered why you might naively do it on purpose, but in practice it's often unintentional. People will post-hoc try to rationalize what's clearly a race condition they failed to consider properly at time of writing.

### As the producer

1. Set expectations up front
   1. Is data guaranteed to be whole?
   2. What is the latency of any eventual consistency in the system?
   3. How do I tell if I'm getting stale or incomplete data
2. Never lie to your customer. If you can't guarantee accuracy either fail or mark the data
   1. Sometimes you have mixed needs. Some of your users may prefer the best effort data. Others might be sensitive to accuracy like the provisioning example. One way to handle this is to return an error code, but include a best effort response. Then the client can decide to trust it or not. For instance, you could have:

   ```json
    200
    { "foo": "bar" }
   ```

   vs

   ```json
    503
    {
        "error": "Could not fetch latest state",
        "lastKnownState": { "foo": "bar" }
    }
   ```

### As the caller

1. Demand excellence from your producer. If it's an internal team, you're their customer. Make sure they treat you accordingly. Insist on strong, explicit contracts.
2. Figure out your invariants. What expectations do you have?
3. Create strong boundaries for external input
   1. Guarantee invariants. If you're calling to external code or taking user input, you can't assume that it's valid.
   2. Detect when invariants are violated and pick a deterministic failure state behavior. Don't lie by passing it along blindly. If you must pass it along, do so with wrapping (treat it as "inner error" and log the context of the failure).
   3. Force all external data through facades that convert to internal representations that are known good. Never allow bad data in. This will also simplify the rest of your code, because it can trust that input is valid and you won't need redundant checks everywhere.

#### Footnotes

[^1]: Try searching 57686174277320746865207765617468657220746F6461793F on chat-gpt. It will fail to realize it's hex (unless my experiment trained it 😉). If you give that hint, it will figure it out and figure out any future hex prompt you give it. This is *extremely* impressive, but it isn't higher level reasoning. An human programmer immediately recognizes this is hex and will try decoding it first. The point here is even a flexible language model is easily baffled by invariants (in this case not using utf-8 encoding) being violated. If the most advanced flexible input program in the world can't handle unexpected inputs, how is your small application going to?

[^2]: Expect a future post on why this is inescapable, and what it means for "defensive programming"!

[^3]: While common, passing errors through to the next layer is often a leaky abstraction. Tread carefully. (a future blog post will expand on this topic)
