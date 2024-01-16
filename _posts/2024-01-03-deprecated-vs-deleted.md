---
layout: post
title:  "Deprecated vs Deleted"
date:   2023-01-03 12:00:45 -0800
categories: software
author: "Chris Henk"
---

> Precision matters. Semantics matter. A rich vocabulary allows us to communicate concisely.

In software, deprecation means that a particular feature, API, or offering is discouraged from being used and *may* be slated to lose support and/or be removed in the future.

The key thing to keep in mind is that deprecated offerings are merely discouraged. They aren't removed, and it's possible to disregard the author or owner's recommendations and keep using it anyway.

If you are removing a feature (including making a breaking change), you aren't deprecating it. It's important to get this right. A deprecation is a notice for future work that ought to happen at some point. Even if you are announcing end of life for an offering, the moment the notice is given the offering is immediately considered deprecated. This type of deprecation may even mean that action is *required* by a certain date. But it's erroneous to say that end of life date itself is the deprecation point, and you will confuse your users by calling it one.

Examples include:

- An operating system past it's support date
- Features in the standard library of a programming language that will or may be removed in the next language version
- A particular version or field in a REST API

## Should Deprecated Offerings Be Used?

Deprecated offerings can be ok to keep using. It's not practical to always be on the latest version of everything you depend on. If no suitable substitute exists, then it's not even possible to do so until that is first remedied. 

Try to avoid:

- Taking *new* dependencies on a deprecated offering. A good way to do this with a linter that fails builds that use deprecated features. When turning this on or upgrading to the version that causes the failure, do a one time suppress of each existing warning. This has the added benefit of clearly labeling your debt.
- If the dependency has reached end of life, try your best not to use it. If it's past security end of life absolutely don't use it, but even if security updates are still being published this unmaintained dependency is a time bomb. Eventually it will be incompatible with something new you need, bug out, etc.

Best Practices:

- If there is a suitable replacement / upgrade path, don't delay. A good rule of thumb, I have never seen a reason for any update to be delayed more than a year. Ideally, updates are delayed no more than 6 months.
- Evaluate each issue as it comes in. Use linters and scanners to ensure you're aware of all issues. Be sure it's possible for your software vendors to notify you of deprecations and that you have people and process in place to react to these notices.
- Have a plan in place. Know approximately when you will migrate and what you will migrate to. If it's not possible to migrate, start finding a suitable replacement now. If someone else is going to release a replacement before end of life, make sure you're regularly checking in on their progress to ensure the replacement is on track. If they miss their dates, will you face issues?

## Semantics More Generally

Accepted terms have accepted meanings and often even a set of best practices that accompany them. When you label something according to a piece of jargon, you're precisely identifying a concept the listener is aware of that they can deploy their relevant expertise towards. If you're mislabeling things, you're lying to your colleagues or customers. Their relevant expertise is now a trap, where they will take the wrong actions in response to what you have told them.

Precision matters. Semantics matter. In the same way that the distinction between a nullable and non-nullable type matters in production at runtime, the accuracy of human level terms matters just as much.
