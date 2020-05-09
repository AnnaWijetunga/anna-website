---
title: "Take a Ten Minute Walk"
date: "2020-05-07T22:40:32.169Z"
template: "post"
draft: false
slug: "take-a-ten-minute-walk"
category: "JavaScript"
tags:
  - "Code Newbie"
  - "Codewars"
  - "JavaScript"
description: "Codewars challenge of the day! Diving into JavaScript."
socialImage: ""
---

My 8-hour coding days at Flatiron are a thing of the past (quietly sobbing, brb), but, as with learning any new language, practice or lose it.

Practice it is! I dipped into [Codewars](https://www.codewars.com/) again today. I was rusty, but here goes.

Today's challenge (JavaScript):

**You live in the city of Cartesia where all roads are laid out in a perfect grid. You arrived 10 minutes too early to an appointment, so you decided to take the opportunity to go for a short walk.**

**The city provides its citizens with a Walk Generating App on their phones -- every time you press the button it sends you an array of one-letter strings representing directions to walk (eg. ['n', 's', 'w', 'e']).**

**You always walk only a single block in a direction and you know it takes you 1 minute to traverse one city block, so create a function that will return true if the walk the app gives you will take you exactly 10 minutes (you don't want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.**

**Note: you will always receive a valid array containing a random assortment of direction letters ('n', 's', 'e', or 'w' only). It will never give you an empty array (that's not a walk, that's standing still!).**

It's often hard to dive straight into code, so I pseudo-code instead:

```
// 1 block = 1 minute
// if walk = 10 minutes, true
// otherwise false
// must return to starting point
// if paths start with 0, then increment/decrement
// then, if a path ends again with 0, return true
```

The idea is forming, now let's get closer to code with the details:

```
// ns (north-south) should equal 0 
// we (west-east) should equal 0 

// if the direction is north, north-south add 1
// if the direction is south, north-south subtract 1
// if the direction is west, west-east add 1
// if the direction is east, west-east subtract 1

// if the length of the walk is equal to 10 
// and ns is 0 and we is 0, return the walk length

```

Format is coming together, let's build out that function:


```
function isValidWalk(walk) {
  let ns = 0, we = 0; 
    for (let dir of walk) { 
      if (dir == 'n') ns += 1; 
      if (dir == 's') ns -= 1; 
      if (dir == 'w') we += 1; 
      if (dir == 'e') we -= 1; 
    } 
    
    return walk.length == 10 && ns === 0 && we === 0; 
}
```

The thing I love after submitting a solution is seeing what other people submitted. Here were other clever solutions!

Clever Solution 1 (and most popular):
```
function isValidWalk(walk) {
  var dx = 0
  var dy = 0
  var dt = walk.length
  
  for (var i = 0; i < walk.length; i++) {
    switch (walk[i]) {
      case 'n': dy--; break
      case 's': dy++; break
      case 'w': dx--; break
      case 'e': dx++; break
    }
  }
  
  return dt === 10 && dx === 0 && dy === 0
}
```

Clever Solution 2:
```
function isValidWalk(walk) {
  function count(val) {
    return walk.filter(function(a){return a==val;}).length;
  }
  return walk.length==10 && count('n')==count('s') && count('w')==count('e');
}
```

Clever Solution 3:
```
function isValidWalk(walk) {
  const north = walk.filter(item => { return item === "n" }).length;
  const south = walk.filter(item => { return item === "s" }).length;
  const east = walk.filter(item => { return item === "e" }).length;
  const west = walk.filter(item => { return item === "w" }).length;
  
  return walk.length === 10 && north === south && east === west;
}
```

After too many hours (yes, that's plural) of working through this, it's time to go on a real 10-minute walk. 

Thanks so much for reading, and great work to you if you worked through this one!