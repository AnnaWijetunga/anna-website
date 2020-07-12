---
title: "Imposter Syndrome: That Same Old Song"
date: "2020-05-12T22:40:32.169Z"
template: "post"
draft: false
slug: "imposter-syndrome"
category: "Code Newbie"
tags:
  - "Code Newbie"
  - "Gatsby"
description: "Imposter syndrome, so real!"
socialImage: ""
---

Imposter syndrome. 

They say it's real and that everyone feels it, so don't dwell. Keep moving forward, you deserve to be here.

Oh boy. Somehow that is the hardest advice for me to follow.

Imposter syndrome looks and feels different for everyone, but here's what it is for me.

Just weeks post-graduation from Flatiron, I'd built my website locally (using Gatsby) and wanted to host it using Netlify.

According to Netlify's documentation, it's a gosh darn snap to deploy. 

DELIGHTFUL.

I followed Netlify's steps (so easy!) and got to the final "click" to deploy. 

All too soon, an error:

`Build script returned non-zero exit code: 127`

Sigh. 

Pep talk time.

"Anna, we've been here before. Find the root of the problem and fix it!"

After a few light Google searches and glances through my deploy log, I took a direct flight to the land of imposter syndrome. 

*What even IS this error message? UGH I KNOW NOTHING. Yes, I tried both build commands, that's not it. Shoot, now my site's not loading locally. I AM NOT CUT OUT FOR THIS!*

And folks, it happens *that* fast *every* time.

Hit a bump in the road, the thoughts roar.

Heaven knows I have no solution other than to plow through the noise and keep trying - which is exactly what I did - but it feels so terrible.

Here's how I deployed my website (you see? I *knew* you could do it).

## The Situation

+ 14 tabs open (13 tabs too many)
+ 9 (*covers face in shame*) failed deployments
+ 3+ hours of effort
+ You better *believe* there was sweat

Most of those tabs had Stack Overflow questions loaded, and I also had a lil' Gatsby and Netlify documentation on the side.

## The Process

Reading (so many) Stack Overflow q & a's did not give me the direct solution. 

But.

It gave me context for where to look, which is REALLY HELPFUL.

A lot of people got the same error message but named other errors within the deploy log that I didn't have. 

So, I combed through my deploy log, tried (really hard) to understand what I saw and found what could be the culprit.

`yarn: command not found`

This wasn't a clear "ah ha!" moment, but it sure was a clue.

I put my efforts there, and scoured those Stack Overflow q & a's again, this time focused on yarn. 

Some folks updated their yarn version while others manually pushed their yarn.lock file.

I was shooting in the dark, but I tried everything and anything yarn related.

The last command did the trick. 

Want to know what it was?

## The Solution

Running `yarn install` fixed the issue.

Yup. 

So many eye rolls, face palms, my gosh I can't believe it was THAT, and a heckuva lot of relief.

And I swiftly took a direct flight back to reality.

And yes, it happens that quickly.

Been there? Experienced that? Sure would love to hear about it. And, for what it's worth, you're not alone.

[Get in touch](/pages/contacts) any time.