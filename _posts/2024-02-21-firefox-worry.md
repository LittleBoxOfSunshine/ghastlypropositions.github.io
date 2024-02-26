---
layout: post
title:  "I'm Worried About Firefox"
date:   2024-02-21 12:00:45 -0800
categories: software
author: "Chris Henk"
---

`Nowadays you're about as likely to see Firefox as you are a Linux desktop`

I've been using Chromium Edge for a few years now and really enjoyed it until recently. It wasn't *quite* as obnoxious with the stalking as Chrome (it stalked but would fight against websites stalking), was a little faster, and was shipping useful new features at a better cadence. A few things have changed though. I'm revisiting aiming higher on privacy. I'm not liking some of the features, the number of dark patterns has been increasing, and I'm concerned about Chrome's dominant from an ecosystem health standpoint.

Finally, I have used Firefox in the past on Linux + lately I've been poking around Mozilla's work as a result of my last few months of working with Rust. It's truly a phenomenal language, though I think people fixate on the wrong aspects for why it's great. More on this in the future. I firmly believe in the value add of the language in OS and browser development. So it was a plus for Firefox that over time I could (all else equal) expect its quality and security to outpace Chrome.

## The Search

### Trying Firefox again

I played around with it, and unlike in the 2016-2018 days the performance wasn't bugging me. I also wasn't having issues with websites not rendering. Everything was looking good, and my last test was to see the current market share. After all, with more and more browsers built 

### What about Safari?

Couple issues. I don't only use a Mac. I've never found Safari pleasant to use. Most importantly, it's engaged in the same anti-competitive behavior Microsoft was in the late 90's. It's borderline criminal that the government has yet to crack down on App Store policies and I'm not interested in voluntarily using the browser on my computer when I'm forced to use it (as a subcomponent) of my browser of choice on my phone.

Don't use Safari. It's the Internet Explorer of our era.

### What about other Chromium based options?

The biggest downside is that it doesn't address the issue of Chromium being too dominant or the desire to use something written in Rust[^1]. Google has at a few times forced or tried to force in bad changes that harm the open web and consumers more generally. As is always the case, the monopoly position they hold takes root and a corruption spreads. Beyond that, it's a lack of research issue. I will be looking into them next, but my goal would be to find one that's offered by an equivalent to a Mozilla. By a foundation or by a company whose model fully incentivizes maximum privacy.

## Now I'm Worried

According to [Statcounter](https://gs.statcounter.com/browser-market-share), Firefox is down to 3.3% market share. That's truly alarming, because that would mean that nowadays you're about as likely to see Firefox as you are a Linux desktop. That also wouldn't surprise me though. I never see it used outside of developer circles, and I think that bias has made it easy for us all to miss just how catastrophic the market share decline has been over the years. In fact, the only challenger to Chromium in any way is Safari. As mentioned above though, I consider that purely artificial. The moment the government does their job that will collapse.

This is alarming because we are increasingly at the whims of a single company Google. While Google was well situated to champion the open web, their nearly purely web based business made it a win-win, they are not well situated to push for privacy. In fact, it's an existential threat to their business which is still shockingly dependent on Adsense revenues. They're also willing to play nice with media giants for a variety of reasons, which results in their willingness to play ball with DRM regimes that harm consumers and security.

## How Do We Fix It?

If I could wish upon a star, it would be from Google to recognize that Chromium has grown beyond their desire to collect data and challenge Microsoft's monopoly. It's become a critical piece of web infrastructure in the same way that Linux, git, or Nginx have. It's simply not viable to be so dependent on an easily corruptible body. Eventually, it will probably result in a fork. So why not do what Mozilla did and transfer the project to a foundation?

Alternatively, the wisest Google that still acts purely within self interest would carefully manage this issue and intervene less frequently than they currently are. They would aim to slowly resolve the issues as they slowly adapt their business model. It's not like they don't need to already anyway, the AI boom threatens search revenue as well. So does the increasing popularity of integrated ad-blockers in reskinned Chromium builds.

I suspect they'll do neither and instead opt to kick and scream though, as most monopolies inevitably do. They'll make it more painful until finally the other chromium browsers do fork the browser and set it up in a fully open way. In the same way that that Chrome undermined Microsoft's monopoly by being more open, I suspect that Chrome itself will be undermined by competitors that make Chromium more open.

### Why Doesn't A Reasonable Chromium Product Exist?

I discuss the principles more thoroughly in [this post]({% post_url 2024-02-14-edge-open-source-works %}), but the key challenges here are that:

1. A browser that isn't doing extra stuff and/or invasive can't easily be monetized
2. Packaging Chromium into something useful requires maintenance and servers

Signal manages to exist despite these challenges because it has sufficient donors. That could work here. In principle, this is a cheaper offering than signal is. However, it requires big donors to get the ball rolling at a minimum.

Chromium is published, but it has deficiencies. It has no ability to sync settings and it's missing codecs unless you compile it yourself. These are big enough hurdles to make it unusable for most people. So what we need is to publish a complete version (easy enough with volunteers) and we need to add in sync features with funding for the back end.

One interesting idea I had was for the sync feature to piggy back off the user's cloud storage. Duplicati adopts this model if you'd like to see an example. This solves a lot of issues:

1. No ongoing cost to the publisher
2. No vendor lock in
3. High privacy, vendor can't see your data 

So there's my call to action. Make a Chromium release that's full featured. Either:

1. Get enough donations to offer free sync like Firefox does
2. Offer integrated sync for a small fee (same concept as Obsidian Sync)
3. Offer integration with personal cloud storage (the Duplicati method)

Better yet, offer a mix of these! Making it easy to self host the data is a value add even if there is an integrated sync option.

This is something I feel strongly enough about I would eventually like to pursue it. However, for at least the next 6 months my plate is too full so I'm putting the idea out there. I'm also happy to contribute towards anyone that gets it going. 

[^1]: Yeah, yeah I hear you. I know "X, but in Rust!" Is a meme and I agree it's silly. However, the browser / OS is the workload that inspired the language in the first place. If ever there was a time to want the software you're using to have been written in Rust then clearly it's here. Chromium is aware of the issues they face, they just also have issues integrating with Rust in their current state. I don't think it's unreasonable to suggest that Firefox has a better long term roadmap for defending against these issues. Just [look at](https://www.chromium.org/Home/chromium-security/memory-safety/#:~:text=The Chromium project finds that,prevent such bugs at source.) the degree of effort and number of hoops devs jump through to keep Chromium safe.