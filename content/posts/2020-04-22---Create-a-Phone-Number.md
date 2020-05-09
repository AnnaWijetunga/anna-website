---
title: "Create a Phone Number"
date: "2020-04-22T22:12:03.284Z"
template: "post"
draft: false
slug: "create-a-phone-number"
category: "JavaScript"
tags:
  - "Code Newbie"
  - "Codewars"
  - "JavaScript"
description: "Codewars challenge of the day! Jumping into JavaScript."
socialImage: ""
---

With the intense pacing and curriculum of bootcamp over, it's time to tackle daily coding challenges to stay fresh.

[Codewars](https://www.codewars.com/) it is!

The challenge:

**Write a function that accepts an array of 10 integers (between 0 and 9),
that returns a string of those numbers in the form of a phone number.**

**Example:**

```
createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) 
=> returns "(123) 456-7890"
```

My deer-in-headlights expression (I haven't `join`ed and `slice`d in a few weeks) faded as soon as I started pseudo-coding and breaking this up into small pieces.

First. This is an array of numbers, all separated by commas, and it needs to look like a phone number. Which means, we need to slice as a way of selecting and then grouping certain numbers together.

Big thanks to [w3schools](https://www.w3schools.com/jsref/jsref_slice_array.asp) for refreshing my memory!

The `slice()` method returns the selected elements in an array, as a new array object.

It selects the elements starting at the given start argument, and ends at, but does not include, the given end argument. Syntax looking like so:

`array.slice(start, end)`

In this case:

```
numbers.slice(0, 3)
numbers.slice(3, 6)
numbers.slice(6)
```

To accompany `slice()`, `join()` method returns the array as a string - which we need in order to return the phone number as a string.

Because our array of numbers is separated by a specified separator (fancy speak for a comma), we need to `join` the numbers into the beginnings of a phone number.

This also means we need to use `.slice` AND `.join` methods to take out the values we need from the array, between the specified indexes, and group them together:

```
numbers.slice(0, 3).join('')
numbers.slice(3, 6).join('')
numbers.slice(6).join('')
```

Three more things.

We can use [string template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) to clean up our code. But we'll also need to add parentheses around the first `slice`/`join` statement, and a dash before the final four numbers:

```
function createPhoneNumber(numbers) {
    return `(${numbers.slice(0, 3).join('')}) ${numbers.slice(3, 6).join('')}-${numbers.slice(6).join('')}`;
}
```

And this will return our (xxx) xxx-xxxx phone number!

After reading through the alternate solutions from other Codewar users, I was astounded at the variety that exists. Code can be so versatile (lovely!) but this can make being a newbie intimidating (feelin' that!).

Always learning and looking forward to the next challenge.

In case you made it all the way here and you have your own solution, I'd love to see it!

<!-- 
![Movable metal type, and composing stick, descended from Gutenberg's press. Photo by Willi Heidelbach. Licensed under CC BY 2.5](/media/movable-type.jpg) -->