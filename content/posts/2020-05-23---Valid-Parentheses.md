---
title: "Valid Parentheses"
date: "2020-05-23T22:40:32.169Z"
template: "post"
draft: false
slug: "valid-parentheses"
category: "JavaScript"
tags:
  - "JavaScript"
  - "Code Newbie"
  - "Codewars"
description: "The outcome of my first technical interview."
socialImage: ""
---

I completed a technical interview this week and received specific feedback:

**"Get faster."**

I have a process, the process works, the process is **slow**.

The best way I know to get better at something is to practice, so I'm upping the ante. 

Codewars, giddy up.

**The Challenge:**

Write a function called that takes a string of parentheses, and determines if the order of the parentheses is valid. The function should return true if the string is valid, and false if it's invalid.

```
Examples
"()"              =>  true
")(()))"          =>  false
"("               =>  false
"(())((()())())"  =>  true
Constraints
0 <= input.length <= 100
```

I carry a great deal of hesitation and doubt about getting started with any problem. What if what I write isn't perfect? What if it's embarrassingly wrong? So I freeze.

My shiny, new goal: put pen to paper and start writing as if there's a clock ticking. Progress not perfection.

So here goes.

**My Soon-To-Be-Much-Faster Process:**

1) Understand what's being asked. What's valid vs invalid?

```
// string of open AND closed parentheses = valid
// just open OR just closed = invalid
```

2) Think about the method - loops are handy, if you want to run the same code over and over again, each time with a different value. Let's use a loop!

Code newbie here, so I still have to check if my syntax is correct - so I check the [documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration) to confirm the template:

```
for (i = 0; i < 5; i++)
```

3) Let's add our own variables to customize the loop:

```
let n = 0;
for (let i = 0; i < parens.length; i++)
```

4) Now we have to specify what's valid/invalid in terms of our parentheses:

```
for (let i = 0; i < parens.length; i++) {
  if (parens[i] == '(') n++;
  if (parens[i] == ')') n--;
  if (n < 0) return false;
}
```

We're incrementing and decrementing when there are open AND closed parentheses, this equaling 0 - which in our case is valid/true.

If we end up with less than 0, we know we're missing a parenthesis, and we return false.

5) Put it all together, and don't forget our final return:

```
function validParentheses(parens){
  let n = 0;
  for (let i = 0; i < parens.length; i++) {
    if (parens[i] == '(') n++;
    if (parens[i] == ')') n--;
    if (n < 0) return false;
  }
  
  return n == 0;
}
```

It works! Happy with the results, but I have work to do.

I ended up going over my time limit. 15 minutes wasn't enough, but I got more accomplished than I expected. I guess a lil' fire under the buns helped.

After submitting my solution, I love browsing through other solutions. Here is one that stood out to me because of how concise it is:

**A Clever Solution:**
```
function validParentheses(parens){
  let indent = 0;

  for (let i = 0; i < parens.length && indent >=0; i++) {
    indent += (parens[i] == '(') ? 1 : -1
    }
  
  return (indent == 0);
}
```

Always more to learn, and here's hoping this type of daily coding with a time limit helps me boost my confidence and gets my speed up to par.

Did you code along? Have a different solution or a tip for improvement? Sure would love to hear about it :).

[Get in touch](/pages/contacts) any time.