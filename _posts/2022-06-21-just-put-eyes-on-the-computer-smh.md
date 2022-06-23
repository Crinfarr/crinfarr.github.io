---
layout: post
date: 2022-06-21 18:16 -600
title: "Teaching myself OpenCV 2 in 24 hours because I am NOT a masochist"
---

# 2 MTG related projects in a row! I should get a therapist

![relevant xkcd](https://imgs.xkcd.com/comics/tasks.png)
> Current mental state (c) [xkcd guy](https://xkcd.com)

Do you ever get so lazy you start a college thesis level project? yeah, me too.

Originally, the plan was to hack [Delver Lens](https://www.delverlab.com/) onto a raspberry pi (with a few motors) in order to shuffle through cards and create a list.
Immediately after inventing that plan, I realized a few things.
1. I don't actually have a practical way to use a list of cards. 
    * I would still need to sort through them to find what I need, even if I knew that I had them.
    * Still useful to know what I have or don't have, but significantly less useful than a way to access them.
2. I have no idea how to write image recognition software.
    * yeah... I probably should have thought of that first.
3. I have no idea how to mechanically move cards without very high risk of damage
    * which sucks when cards can cost easily hundreds of dollars.
    * and because I'm an engineering student and I really should know how to do this.

so... yeah. Problems.

# The First Solution
>> or: I can't write transitional paragraphs

After thinking about this for a while, I finally settled on the idea that the robot would have to not only move cards from pile A to pile B, but also from pile A to pile C.  This way, I could use a sort of linear half-selection sort by physically moving the cards from pile to pile.

This does have an efficiency of O(kn), where k is the number of values in [S]∩{min([S])...max([S])} given that S is any given stack of values with repetition.  This would be considerably faster if I could swap cards in place, but unfortunately a stack of cards is a LIFO queue and there is not anything I can do about that.

```py
b = []# random list of numbers (a la numpy.randint(0, 1000, 10000))
a = []
c = []
cycles = 0

while (a!=b):
    c.insert(0, b.pop(0))
    for i in b:
        if i != c[0]:
            a.insert(0, i)
            cycles += 1
        else:
            c.insert(0, i)
            cycles += 1
    b = []
    for i in a:
        if i != c[0]:
            b.insert(0, i)
            cycles += 1
        else:
            c.insert(0, i)
            cycles += 1
    a = []
```
> code to simulate sorting through cards (this took me an embarassingly long time to write)
O(nk) would be bad in most instances, but for the limitations, I think it's fine.\

# The Second Solution
>> or: i love you opencv <3

This turned out to be a little less problematic than I thought it was.  I have a lot of python experience (my first engineering project was a RasPi-based robot) so I originally thought to use Tensorflow and train an AI to recognize cards by artwork. The more I thought about this, though, the worse of an idea it became.  AI is very good at approximation (i.e "[this] is A Magic Card or [this] is A Vegetable) but it's not very good at specifics.

My first idea was to use template matching in order to find an image of the card inside a larger image.

ELI5 explanation: Pattern matching is the process of finding the location of a small image inside a larger image. Think of it like printing the small image on plastic wrap and moving it over the larger image until it lines up.

This isn't a good way of doing this, though.  Pattern matching can be very finnicky in situations with bad lighting conditions, scaling, or any amount of rotation, all of which are problems that *will* occur in this project.  Luckily, I figured this out *before* i spent a week on it.

After dropping that idea, I found Keypoint detection, which is for all intents and purposes Actual Magic.

ELI5 explanation: Keypoints are dark points in an image that are surrounded by lighter points.  If two images have a large number of identical keypoints, it's very probable that they are the same.

ELI15: Keypoints are calculated by choosing a low brightness pixel, then searching the 16 closest pixels to it for brighter colors.  If two keypoints have the same light - dark pattern, they are considered to be identical.  When comparing images, larger numbers of identical keypoints mean a higher chance that one image contains the other.

The only problem with this approach is that calculating a large number of keypoints takes a very large amount of processing power and time; and in a game with 65 thousand unique cards, even 100 milliseconds of processing time becomes almost 2 hours to brute force.

# The current state of this project
>> or: i have spent too much time on this to give up

Currently, I have three ideas on how to improve the detection time.
1. Train a neural net to identify card colors
    * This will allow me to divide the saved keypoints by color and cut the time by approximately 85 percent
    * However, this would have to have **100% accuracy** to be strictly better.
2. Use a text recognition neural network to identify card names
    * Only the first few characters have to be actually recognized in order to significantly reduce the processing time
    * This could be very difficult, since the magic font is both very weird and variable over time.

# oh yeah i forgot the robot part

probably just gonna put a cam on a servo and turn it left or right to flick cards into piles, then use worm gears to move the stacks up and down.

it's stupid but it works.

2-AM-ily, 
    [Crinfarr@1200 lines of code](https://pastebin.com/raw/PRG5P75k)