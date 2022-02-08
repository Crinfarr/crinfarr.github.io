---
layout:  post
title: I love javascript so much
date: 2022-01-26 16:04 -0600
tags: js library biology code
categories: code js
---
So update: this is valid javascript:
```js
var a = ["", ""].map((_, index) => {
	return [...new Set(b.map((type) => {
		return ([...type][index]);
	}))];
});
```
where b is any valid 2d array.

This is a part of the `Square` class of Mendel.js, my genetics npm library (wip).\
It's used to find the parents of a flattened punnet square, which is made using this:
```js
/**
 * @function
 * @arg {Array<*>} arr
 * @description removes duplicates from an array
 */
function deduplicate(arr) {
	return [...new Set(arr)];
}
```

so that's what I'm doing now.

too many .map functions to reasonably think about.


--[Farr](https://www.youtube.com/watch?v=dQw4w9WgXcQ)