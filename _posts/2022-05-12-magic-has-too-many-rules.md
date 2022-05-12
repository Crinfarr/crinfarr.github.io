---
layout: post
date: 2022-05-12 03:01 -600
title: "Making a \"Magic: The Gathering\" rules engine"
---

# This may have been A Mistake.

First thing's first: Yes, Magic Online is going to be a better version of whatever I make.  However, magic online costs Money and doesn't support custom cards, so I will keep my superiority complex, thank you very much dear reader.
Currently there are 3 mainstream ways of playing magic on the internet.
![the mechanically consistent one](/assets/images/20220512/Arena.png)
> MTG Arena, an official and free-to-play online version

|Pros | Cons|
|:----|----:|
|Impressive rules engine|Can be pay2win at times|
|Functional training AI|Alchemy balance passes sometimes ruin the metagame|
|Free2Play with (almost) no consequences|Some matches are very simply unwinnable|
|Non lootboxed cosmetics|No support for custom cards|
|Quest system rewards diverse playstyles|No support for sets released before the game|
|Clean vfx and sound effects|closed source|

![the expensive one](/assets/images/20220512/Online.png)
> MTG Online, an official (and NOT free-to-play) online version

|Pros | Cons|
|:----|----:|
|Impressive rules engine|Expensive to play in non-casual, can cost potentially hundreds|
|Active community|Anonymity leads to inappropriate interactions|
|includes all cards|some interactions can be confusing to newcomers|
| |no custom card support|
| |closed source|

![the confusing one](/assets/images/20220512/Untap.png)
> Untap.in, an unofficial tabletop client

|Pros | Cons|
|:----|----:|
|Very customizable, can theoretically be used to play games other than magic|absolutely no rules engine|
|supports custom cards|closed source|
|thriving community|toxic community, at times|
| |relies on user created lobbies|

## ...but what if there was another way?

Introducing the Ingenuity Engine. A fully open source and fleshed out Magic: The Gathering rules engine written in Haxe.
* Open source backend means anyone can write a custom frontent
* Custom cards are simple, made of almost 100% compressed JSON (and 2 red mana)
* Libless Haxe allows compiling to any platform, including Windows, Mac, Linux, Android, iOS, and HTML5
* Catalogued P2P matchmaking allows for ELO limited matches, if enabled
* Completely free to play with any cards
    * like pr*xies but you won't get banned!

and then the cons list.
* The rule book for Magic is 265 pages long.
* that's a lot of rules.
    * like, a *lot* a lot.
This is a long term project, and therefore will have its own category in this blog.
I've been thinking of making this for weeks now, though, so it's unlikely to end up as yet another idea I ADHDed myself out of doing.

So far, I've written classes for decks, play formats, and cards.
![there's a lot of shit that goes into a single card actually](/assets/images/20220512/cardTypedef.png)
> this is the amount of data that a card contains, according to rule 200.1 in the Magic Comprehensive Rules guide (page 39)

so... yeah. This is where my free time is going.

stubbornly undecided,

[--Farr@722.1a](https://mtg.fandom.com/wiki/Illegal_action)