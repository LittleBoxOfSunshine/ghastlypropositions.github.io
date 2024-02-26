---
layout: post
title:  "New Edge Shows Where Open Source Works and Where It Doesn't"
date:   2024-02-14 12:00:45 -0800
categories: business
author: "Chris Henk"
---

`Demand for your product increases when the price of your complements decreases`

Microsoft Edge is dead, long live Microsoft Edge. Why did Internet Explorer perish? In its heyday it was a near and total monopoly. Most consumers didn't even really understand the concept of a "browser" if they hadn't used other operating systems and Internet Explorer was viewed as the "internet" program. When Google eventually came along with Chrome, they had to do heavy marketing not just to increase awareness of their offering but of the class of product entirely.

In short, because you can't fight economics.

## Complement Products

One of the failings of my education was that my school prioritized macroeconomics over microeconomics courses. While not all schools do this, it's common to exit your schooling without even a basic understanding of the topic. I suspect this is why people at large are so confused over the basics of what markets are, what they can do, and what they can't.

What's relevant to us today is the concept of a complement. A complement is a product or service that you tend (or even effectively must) buy together with another product or service. These don't have to be purchased in a single transaction. Examples:

- Cars and Gasoline (a must be paired example)
- Hotels and Flights (a commonly paired example)
- Apps and an Operating System
- Browsers and Web Apps

In essence then, you can conceptualize these items as singular purchases. When I buy a new computer, I'm not buying it for the joy of owning a license to an Operating System. I'm buying it because it's necessary in order to run the software I actually want to use, which itself is just a means to some broader aim. We can think of them as part of the same purchase in the same sense as it's meaningless to buy a bike without any bike tires. Without both, the other item is useless.

Sure, there are exceptions. What if I'm doing art? What if I already have one of the components? At scale this doesn't tend to matter though. It's quite clear that these items are inextricably linked.

When I want to do something, I have an amount of money I'm willing to spend. I don't set a budget for each part. For instance, if I need a bike I can compare options:

1. Buying a new, ready to use bike
2. Buying a used bike, new tires, new brake pads, and the cost in time or money to install the new components

From a budgeting perspective there's no difference in how these are evaluated. As a result, if the price of a complement to a bike like tires drops it will increase the demand for the other components like the bike frame.

This is why companies offer things for free. They're looking to make their complements a commodity item, which will in turn increase demand for their core product and thus their revenue.

> Most of the time if it's free, you're the product. But not always. Google isn't making money off the open source portions of Android and Chrome. At least not directly. Releasing these parts for free buys good will, increases their user base, and most critically commodifies the elements of the system they aren't making any (or as much) money on. Chrome makes money off your search history and default search engine setting. The biggest threat to Chrome isn't reskinning their browser, the biggest threat is if web developers stop targeting it, harming compatibility. By making it easy to reskin Chrome, you're further increasing the market share of the underlying platform and mitigating this threat.

## How To Lose Your Monopoly Status

Google had a firm understanding of complements when they launched Chrome, but Microsoft didn't. That might seem weird at first. Internet Explorer was also free. In fact, it's freeness as a complement was what drove anti trust complaints. But there's more to making a commodity than simply its price. Especially once total cost of ownership and all parties to the commodity are considered.

### Microsoft's Strategy: Embrace, extend, and extinguish (EEE)

This strategy was applied to numerous products with varying degrees of success. It's not entirely without merit. If you do have the dominant market position, you have more freedom to lean on everyone else. However, the more you do so the more you erode your position. Like everything else, it's a balancing act. Any time a monopoly is dethroned naturally it is because they failed to strike this balance. Typically we consider failure to innovate, but it's also possible to actively undermine your advantage with hostile behavior.

The plan is as follows:

1. Embrace. Create a competitor that's more or less compatible
2. Extend. Offer extensions that add value in some way, but only would work on your product
3. Extinguish. For any dominant extension, weaponize this to suppress the competition.

I think Bill Gates' 1998 memo to the Office division best captures the idea:

> One thing we have got to change in our strategy – allowing Office documents to be rendered very well by other people's browsers is one of the most destructive things we could do to the company. We have to stop putting any effort into this and make sure that Office documents very well depends on PROPRIETARY IE capabilities. Anything else is suicide for our platform. This is a case where Office has to avoid doing something to destory [*[sic](https://en.wikipedia.org/wiki/Sic)*] Windows.

This is true and it isn't. Gates was pretty ruthless and effective. This also tracks with most people's mental ideal of what an evil monopoly capitalist would do. Yet, they lost their monopoly so apparently it didn't work! What gives?

The strength and weakness of this approach is that it's an all in strategy. You make finding substitute products as hard has possible and maintain a degree of quality such that the increased benefits from the substitute product are outweighed by the cost of switching. The more products you have integrated in this way, the stronger the strategy. While I'm no Gates, I suspect this is why he pushed it so hard. He was capitalizing on their wider dominant product portfolio.

Whatever his exact reasoning was, this is precisely why Internet Explorer was stable right up until its complete demise. The all in strategy works well right up until the moment it doesn't.

### Google's Strategy

Google on the other hand recognized what it would truly take to make the web browser a commodity. As web application developers themselves, they were well positioned to see where the opportunities were:

1. As the browser platform owner, you really only benefit from
   1. Control (feature development + defaults)
   2. Access to data such as browsing history
2. The user wants
   1. Speed
   2. Security
   3. Maximum compatibility
3. Web app devs want
   1. Max install base
   2. Cutting edge platform features
   3. Good tooling
   4. Minimal vendor lock in

Microsoft wanted to trap their users and developers into their platform, Google was going to make their platform the obvious choice for both with particular emphasis on developers.

This was the genius of Google's strategy. They were going to attack Microsoft's hostile behavior on 2 fronts. The users *and* the developers. The hardest part about any new platform is the chicken and egg problem. Users won't use it if there are no applications, and developers won't target it if there are no users. But unlike with other platforms, there was very little in the way of "extensions" or anything overly specific. Despite Microsoft's best efforts, the web was an open standard.

This meant Google could focus narrowly on making the fastest browser with the best developer tools. By making it easy to support, developers would target it. They would also quickly realize it made developing their apps easier and thus it quickly became their *primary* platform to do development in. Now their web apps didn't just work in Chrome, they worked *best* in Chrome.

Open source played directly into this. The open standard is what allowed the product to exist in the first place, so encouraging more and more openness in the space only served to benefit them. It wouldn't cost them really anything either. They were going to write this code and give it in compiled form for free anyway. It also addresses the vendor lock in. While it's no easy task to fork a foundational open source project, it's at least possible to do so. If Google is too tyrannical, the world can respond much more easily than what it took for Google to dethrone Microsoft in the first place.

> That's worth dwelling on. If you're being crushed under the foot of a tyrannical monopoly, an effective strategy is to permanently weaken the ability of such strong monopolies to form in the first place. Google Chrome is effectively a monopoly at this point and they still get the same benefits. But by being easier to overthrow they were also more easily able to seize their position in the first place.

### Apple's Strategy: EEE 2 Electric Boogaloo

A brief detour if I may. Funny enough, Apple in this respect is today's Microsoft. In fact their anti-competitive monopolistic behaviors are even more powerful because Apple has a stronger hold on the platform. Bill Gates became the richest person in the world because he commodified hardware by selling software on its own that runs on lots of different hardware. This inherently put a limit on the degree of control he could exert.

Apple on the other hand hit it big in an embedded category (phones). Here the market had no expectations of running custom software. In fact, the App Store was that first large scale offering that even could. But, the OS was always still 1:1 with the hardware and this is what allowed Apple to sneak in an idea they can't on MacOS. You can only install custom software that they bless. They nailed EEE here. They embraced phones with ARM based CPUs. They extended it with killer features like the touchscreen, the UI, and most critically the App Store. They extinguished the competition by banning any app that competes with anything they offer. Unlike the browser, there's no open standard for how phones work. You can't quickly spin up an iOS competitor that runs iOS apps.

> An even if you do, get ready for a fight. Google did use this strategy to enable Java on Android, and Oracle engaged in over a decade of legal action to try to stop this

Safari has a surprisingly high market share. This is directly a result of their anti-competitive behavior. Apple requires that any browser on iOS must use Safari's internals. In this way, they artificially increase usage of Safari and thus web app devs must support it or else they'd lose too much market share (all iPhone users). Where users able to choose, I suspect Safari would suffer the same fate as Internet Explorer. Developer satisfaction was a key element to Chrome's success. I doubt there's a company on Earth developers are more averse to vendor lock in with than Apple.

## Trying Again, But From "Zero"

Microsoft finally accepted that Internet Explorer's condition was terminal, but they still hadn't learned their lesson. They created Edge by forking the internals of Internet Explorer. Really, it was more of a reskin to avoid the bad brand of IE than it was a new browser. There were other improvements and certain items were made from scratch, but all in all it was IE just better.

That was too little, too late. And Edge became a total meme whose primary purpose was to download Chrome.

## If You Can't Beat Them, Join Them

Finally in 2019 Microsoft learned. They accepted that the internals of the browser had become further commodified under Chrome, that Chrome's implementation was a defacto standard, and they refocused on what they really gain by being the browser owner. Instead of trying to compete in the thankless world of browser rending engines, they reskinned Chrome.

I was there at the time, and predictably a lot of internal people were unhappy about this. It was a mix of aversion to admitting defeat and cries of those from the *Not Invented Here* era that was hostile to open source. But, just like how they were wrong about embracing Linux they were wrong about this too.

At first, it really was just effectively the same browser but with Microsoft styling. They focused on compatibility and not giving you reasons to dislike it. With that foundation laid, they sought to innovate on the user side. It integrates with Windows Hello, which can be a huge boon for enterprise users[^1], added UI features like vertical tabs, and consumer features like coupons lookups.

All the while it cashed in on what Microsoft really wanted. To be your default browser, with the default search engine set to Bing. Nowhere is this fact more telling than in recent changes to Windows making it harder to change your default browser. Remember from before? They've made the benefit of the substitute (Chrome) smaller and made the cost of switching (screwing with the settings) higher. New Edge is very compatible with Chrome, it can even use the same extension store. Yet, there's this weird gap in the settings sync. All of your settings *except* for default search engine are synced with your account. *What a strange omission, directing more traffic to their other product*. Recently it has started pushing Bing Co-Pilot hard (even with dark patterns).

Overall adopting this model has been a smashing success. What remains to be seen is if Microsoft can resist the urge to fall back into its old tyrannical ways.

## How This Applies to Open Source

Open source software works best and is most competitive when it's one or more of:

1. Developer facing products
2. Building platforms
3. Building infrastructure, in particular interconnects and security topics
   1. For example, we're all better off if we all have the best encryption
4. It is a complement, commodity, with low or no monetization opportunity
5. It requires little ongoing maintenance
6. It doesn't require a back end / servers 
7. Bank rolled by wealthy people that are motivated to solve a prisoner's dilemma in infrastructure 

While this may not be complete, it's pretty accurate. Seriously, try to find an exception. Any great open source software I can think of passes these tests. Anything that remains proprietary and/or centralized fails it.

#### Great Open Software

1. Linux (platform)
2. Git (dev tool; note git is free and open but GitHub isn't!)
3. Chromium (as a platform)
4. VLC Media Player (little maintenance, runs locally)
5. Signal (bank rolled)

#### Where Open Fails To Compete

1. Social media e.g. Twitter (requires servers and high degree of effort around moderation)
2. Video games (large monetization potential)
3. Email Hosting (protocols are open; but servers are required to run your own email)

#### Mixed Success Open Projects

1. Specific Linux desktop distros such as Ubuntu (good: dev facing; bad: commodity with high substitution cost + low monetization potential)
2. Purely open Android variants / Chromium (as a browser) which are too hard to use and too low monetization to justify making them easier[^2]
3. Firefox (used to be in "great" but has declined. My suspicion is because the ratio of monetization to monetization potential is so low. Google is highly incentivized to assign many engineers to improving Chrome and to market it.)

## What Open Source Can't Do

It can't resist capitalism or market forces. I'm getting a bit tired of hearing these childish takes. We are not in a "post scarcity" world because now I can send a book as 1's and 0's instead of mailing you a tree. Internet isn't free. Servers aren't free. Software devs can't write code if they can't pay rent or feed themselves. Opportunity cost exists. The list goes on, but the worst part (and why in my mind it's an exceptionally stupid take) is because it fails to consider why the book is worth money in the first place.

The book isn't valuable because someone cut down a tree. It's valuable because of the time and unique contributions of the author. There's a reason developed economies transition more and more to services. Manufacturing is important. In a survival sense it's more important. But we're not in survival mode. Manufacturing is a commodity, same as farming. There just isn't nearly as much value in producing the product as there is designing it.

If you aren't meeting the list of conditions above, you're not going to disrupt a for profit proprietary application.

### Individual Benefits

The reason I find this particular brand of naiveté so harmful is because those who promote it are unwittingly propping up their corporate overlords they claim to be resisting. In the right places, open source is just good business. The fact that thousands of people around the world are willing to offer their labor for free is just the cherry on top that further helps the bottom line.

One of my jobs at Microsoft is to increase Rust adoption because that community did great work that would benefit our systems programming. It's cheaper and better for us to contribute back upstream where there are gaps in our needs than it is to compete or fork an internal version. For a small investment (donation effectively) I can capture the value all those other people have created free of charge! Additionally, we use other people's software and hire developers. A world with safer, efficient languages that lots of people are familiar with benefits us as well.

To be clear, I'm not saying don't contribute. I contribute to open source both on my personal time and company time. But don't delude yourself into thinking you've somehow escaped the system.

When individuals can work in the open, their work can be seen. Their work can be taken with them to new companies, it can be expanded upon by clever ideas from other users. You can build reputation to further advance your career. Most of all, you're making your work easier. There's fewer things you have to do, tools are higher quality, you're less beholden to your management's views, and when you switch jobs you don't have to relearn everything.

## Viewing Open Source Broadly

Markets can't do everything. Neither can shareholder held corporations. The most optimized world acknowledges this reality, and assigns tasks to the regime that best handles them. I believe that certain elements of software are domain specific infrastructure. For the same reasons private infrastructure doesn't work well with roads and utilities, they also don't work in software. The difference is simply the scale.

There are more options than just private and public or private and socialized. Electrical wiring can't vary house to house. We can't have competing standards or implementations of the same standards in the same place. So the government ought step in and select one. Software infrastructure isn't quite so restricted. Yes, it's better for us to standardize where we can but it's also not impossible to have multiple competing options. And thus, we shouldn't mandate anything we should let that competition play out.

However, sometimes there's no clear financial incentive and/or keeping the intellectual property closed undermines the very value we're trying to capture. This is where open source has a roll to play, a unique and important economic niche. I don't think it's a coincidence that most impactful large scale open source is managed by foundations, which themselves are a legal construct that fills a middle ground niche where for profit companies can't handle the situation well but it also isn't necessary or desirable to have the government handle it either.

There is no escape from markets. So long as there is scarcity and the absence of coercion, incentives and choice will form a market. This is true from deciding which candy bar to purchase to which employee to promote. From which policy a representative should vote on to where a new road should be routed.

You're much better off embracing and studying the realities of the world than imagining a utopia where the incentives are different. Instead, learn the incentives and learn the different systems that are available to us. You can even try to create new ones, but you can't create new facts of the world. The way to seek the change you want is to structure the system such that the underlying desires of people will be incentivized to do the right thing.

So in closing, open source is important. It makes the world better. More companies need to engage in it. But it's not magic. We haven't overcome scarcity, and it can't do everything.

[^1]: It's worth noting that this is prime territory for EEE to kick in, as it's coupling aspects of your web app with Windows. At least here it's mainly coupling Entra, not your app directly, but it's still worth being skeptical of.
[^2]: For Chromium, and to a lesser extent even Android, I believe this is a [solvable problem]({% post_url 2024-02-21-firefox-worry %}).
