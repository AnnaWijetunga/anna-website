---
title: "JavaScript Closures"
date: "2020-06-04T22:40:32.169Z"
template: "post"
draft: false
slug: "javascript-closures"
category: "JavaScript"
tags:
  - "Code Newbie"
  - "JavaScript"
description: "What are closures, anyway?"
socialImage: ""
---

Like learning any new language, your knowledge can drip away when your focus shifts.

My focus did indeed shift over the past month - from intense language learning (JavaScript!) to interview prep to strictly coding practice.

What I really needed, silly me, was a sweet lil' mixture of coding and concepts. 

Reviewing JavaScript basics, most concepts soaked right back in - except for one.

##Closures

Originally a mathematical concept, from lambda calculus (did you know that?! me neither!). But for our purposes here, we know a closure to be a behavior of functions.

And *only functions*.

An object cannot have closure.

Nor does a class have closure.

**Only functions.**

For closure to be observed, a function must be invoked.

*And*, it must be invoked in a different branch of the scope chain from where it was originally defined.

##Closure Simply Defined

Each reference from an inner function to the variables in an outer scope is called a closure.

##Closure's Purpose

A closure gives you access to an outer function’s scope from an inner function. 

The closure is a function that remembers the variables from the place where it is defined, regardless of where it is executed later.

Many (and I mean *many*) other authors claimed to explain closures simply, but I believe Dmitri Pavluti did it best:

[Simple Explanation of Closures](https://dmitripavlutin.com/simple-explanation-of-javascript-closures/)

Here's hoping this helped you hear about closures in a way that helps. Thanks so much for reading.

[Get in touch](/pages/contacts) any time.