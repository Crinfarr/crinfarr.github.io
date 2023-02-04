---
layout:  post

title: Playing God

date: 2023-02-04 03:02 -0600

tags: haxe physics biology chemistry code

categories: code haxe
---
# Once upon a time I wanted to do chemistry

...but it's never that easy.  I searched for realistic chemistry emulation kits (I don't want to make actual sodium metal in my kitchen ~~yet~~) but all of them are either enterprise-grade, expensive, or just way beyond my needs. So I went to bed and apparently spoke directly to god.

I dreamed of writing code that could simulate the universe perfectly down to the smallest possible detail, strictly typed and modular down to the individual quark. so I started writing it today.
So far, I have written a typedef for the atom:

```haxe
interface Atom {
    var neutrons:Int;
    var protons:Int;
    var electrons:Int;
    public var halflife:Null<Array<Float>>;
}
```

This is very basic but I think you get where I'm going with this. 

Originally I was going to start with quarks and the standard model and work my way up (I even wrote a function to simulate [weak interaction between quarks](https://en.wikipedia.org/wiki/Weak_interaction "Wikipedia"),) but then I realized that maybe it wasn't such a hot idea to write quantum physics on a binary computer...
So I decided to start at atoms instead.  Some day I may even get to biology, once I finish writing functions that compute every property of every isotope of every element and how they interact.

This is an unimaginably ambitious project that I probably won't ever finish, but it's just too cool an idea for me to not do; so I've made the decision to [make this repository public](https://github.com/Crinfarr/Everything.hx) as I work on it.  I'll look through all pull requests and I'll take any help I can get. ~~yes, even from you.~~

The current goal is to have a construct of the periodic table with all attributes of the atoms filled out.  Reacting atoms will be done through the AtomTools class, which currently only has `isPrimordial` and `isStable`.


yeah I know this is a stupid idea

--[Crinfarr](javascript://alert("you expected a rick roll, but it was me! DIO!") "https://www.youtube.com/watch?v=dQw4w9WgXcQ")

p.s I know this is a short blog post with none of the pretty pictures I usually add. I'm tired and my brain is fried.  Update when I figure out how to even begin thinking of how to track progress on this.
