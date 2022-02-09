---
layout: post
date: 2022-02-08 22:14 -600
title: How to accidentally make a minecraft doxxing tool
---
# I wish this was clickbait but I'm actually just dumb

So about a year ago I was scanning the internet for minecraft servers using an app called [Masscan](https://github.com/robertdavidgraham/masscan) when I accidentally stumbled upon the dream smp.
Yes, really.

You see, when you fetch a minecraft server's stats, you also get a list containing things like max players, the favicon and motd, and **a small list of currently online players.**
![woah](/assets/images/20220208/20220208_155334.jpeg)
> yeah, it's legit.

Luckily, it's whitelisted. <sup>otherwise i would be in big trouble.</sup>
However, that got me thinking.

One of Masscan's advertised features is its ability to [scan the entire internet in around 5 minutes,](https://thechief.io/c/editorial/how-to-scan-the-internet-in-5-minutes/) which is unbelievably fast by any standard.  Throttling back the bandwidth to something like 30 thousand pings per second still gives me a *very* high chance of finding every online minecraft server on a given port within a day.

So what did I do? Glad you asked! something awful that will never see the light of day.

I created MCScan3, the descendent of mcscan (a test program from a few years ago that I used to teach myself Websockets,) and mcscan 2 (an unfinished follow-up to mcscan that did all the scanning inside a single node program.)

What does this have over the other two, you may ask?
well,

1. Built in IP/domain blacklist!

![wooah](/assets/images/20220208/configs!!.png)

This list is not created by me, but the person who made it deleted both their github account and their blog, so I'm not quite sure how to credit them.

I guess if you see someone who wrote for a "furiouseagle.net" and seems to know a lot about intensive scanning, tell them I say hi.

2. Built in default scan profile!

![woooah](/assets/images/20220208/configs!!!!.png)

This one actually is by me, but I'm not particularly proud of it (you know, since it's a list of command line arguments)

3. Built in setup tool!

![wooooah?](/assets/images/20220208/seddup.png)

I know it's not impressive, but I usually just decide that the setup for building or running my programs is not my issue.  well, no longer! i learned one thing

3. [WIP] the ability to find out what server any given user is on as fast as your router can spew packets!

..

&nbsp;

....

&nbsp;

........and that is why I will never release this project.

I know it's not particularly difficult to rebuild with enough libraries and/or time, but I don't want to make this accessable to the 90% of twitter and tiktok that would make this tool extremely dangerous, and so I will not be releasing it.  If you have a legitimate use case for this or you just want to talk about it with me, DM me on Discord or Twitter or email me at [contact@crinfarr.io](mailto://contact@crinfarr.io)

Sin Searly, 

[--Farr](https://xkcd.com/285/)

&nbsp;

&nbsp;

p.s. - your routers will thank me.