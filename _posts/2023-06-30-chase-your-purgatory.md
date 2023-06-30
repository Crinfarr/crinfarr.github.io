---
layout:  post

title: Things I learned from programming at a corporate level

date: 2023-06-30 13:52 -0600

tags: haxe corporate code

categories: code haxe
---
# It's been a minute.

Surprise! I'm the head of the (one-man ) IT department at Apotech now.  This is gonna be a really text heavy article, so if you're here to look at screenshots of code I would recommend literally any other post instead. genius.

In short, here's 5 bullet points and 325,000 subpoints I've learned. After these I'll talk more personally about it.

1. If you're lucky enough to get "full creative control" of a project, run with it like the fucking wind.
2. Everything NEEDS TO BE MODULAR.
   1. E V E R Y T H I N G.
   2. You'll inevitably have to add a feature to a control panel, or introduce a new backend logging point, or something in that degree.
   3. if you get asked to create a webpage that's functionally the same as another one you already did, and it takes you more than an hour, you failed.
3. Nobody really knows how code works except you
   1. Get used to summarizing things like you're talking to people that know nothing about your job
   2. because a lot of people know nothing about your job.
4. ERROR LOGGING
   1. ERROR LOGGING ERROR LOGGING ERROR LOGGING.
   2. If you wake up one day and your entire backend has been looping a crash overnight, you need to know why within the first 5 minutes of showing up at the office.
5. You're wrong about how fast you can write code.
   1. If you think it would take you 1 week to write an api endpoint or a blog page or something of the sort, it will take you 3.
   2. Something will always go wrong, and it will be in a brand new way that nobody on earth has ever seen before.

Anyway, on to my experiences (spaced the same way as these bullet points.)

## Always take full creative control

I started at this company as a low level NOC staff, basically just pretending to be a sensor data probe so that the company can say 24/7 on its brochures (and to SOC/HIPAA auditors.)  The only reason my job exists is that I made it exist.

One of the steps in a normal data collection round includes copying data from a webpage to an excel sheet, which really felt... dumb? redundant? redumbdant? to me.  So I taught myself Selenium, since Python can be installed from the microsoft store as a non admin user and VENV can put pip modules wherever you want.  This is absolutely the least efficient way of doing this, but it was the only way I had access to at the time.

Jumping forward a while, I headed the migration of the ticketing system from something proprietary to Jira. My performance on that got me put on 9-5 (while still legally being noc staff,) which let me talk with my corporate overlords more.  I used this as an 'in' to show off the metric logging software I had written on overnights out of boredom, which eventually landed me my current role (after I also headed a full microsoft cloud migration, but that's not the point of this post.)

On to bullet point number, uh, 2.

> this is going to take a while.

## Everything needs to be modular

My original backend for the metric logging software, codenamed Iridium (because I like naming things after elements and for absolutely no other reason,) was a really fucked up combination of python, node.js, html, and java.  I hate it and if someone tried to make me do it like that again I would kill myself in front of them.

This weird conglomerate was completely unmaintainable.  Every time I made a database change to the server, I would have to rewrite the logger (in python,) the frontend (because my genius megabrain wrote the api in RAW FUCKING SQL,) the backend (in nodejs,) and literally everything that relied on any of it.

This ended up culminating in a frontend that looked like this:
![why](/assets/images/20230630/Screenshot%202023-06-30%20141610.png)

> that graph is not on a canvas.  it's an image that's dynamically rendered to a file on the backend EVERY TIME THE PARAMETERS CHANGE.

which is.. not good.  so modularized it in my new version.

Rhodium (because it's iridium but lighter :)) contains 2 languages (typescript and Haxe,) both of which are strictly typed. The typescript backend is even more finely modular (main.js is 10 lines long) and contains 16 modules in 5 distinct folders. If I want to add a new api version, I can just create a folder in /api named 'v3' or 'v5' or 'v46290' and it will serve itself as an express router function instantly.

## nobody knows how code works except you

This isn't so much a story or an experience as something people seem to forget.

There's a reason you work for a company to write code, and it's because nobody there could do it. Corporations don't hire for positions they don't need to fill.

You can do things whatever jank esolang bullshit way you want to as long as the app gets done.

## ERROR LOGGING ERROR LOGGING ERROR LOGGING

Multiple times this month i've come in to work and found that the test logger I set to run overnight had crashed some time in the 16 hours between me leaving and coming back.  After the third time this happened, I started writing discord webhooks into my programs that send messages to my private server when they either succeed (with log data) or fail (with a little 🙁 in the name.) There's definitely better ways, but none of them are this funny to me.

![his name is jack](/assets/images/20230630/jack.png)

>  this guy is the pinnacle of my skills

Anyway, on to the most important thing I learned:

## EVERYTHING WILL TAKE 3X LONGER THAN YOU EXPECT

Deadlines were invented by the government to sell more energy drinks. Never say you'll be done with something by a date unless you *already think the app is finished.*

No matter how much time you spent on writing api error catching or backend type checking, SOMETHING WILL HAPPEN.  A database will roll out a breaking change, or your VM infrastructure won't support the protocol you use, or some other (totally bullshit) reason.  Even when you're done, YOU ARE NOT DONE.

Anyway, I gotta figure out what to do with my life now.

Maybe I'll make a programming language, or finish one of the 7 unfinished projects on this blog so far.

or maybe i'll take a nap.


(with  corporation accent)

--[Crinfarr](crinfarr.zip/zip/notsus "dont even worry about it")
