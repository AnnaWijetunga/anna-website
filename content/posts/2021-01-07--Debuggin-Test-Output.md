---
title: "Debuggin Test Output"
date: "2021-01-07T22:40:32.169Z"
template: "post"
draft: false
slug: "debuggin-test-output"
category: "Code"
tags:
  - "Code"
  - "Code Newbie"
description: "Tests are slippery things."
socialImage: ""
---

**An Explanation**
Tests are slippery things. Because code is constantly being updated, a test that passed with flying colors one day may fail with the latest merge.

Because of that, we're always looking for failures, but also for warnings.

Besides taking up space, warnings indicate an issue bubbling up. Best to figure it out now.

**The Scene:**
Test output for JavaScript(Vue).
All tests pass but output shows Vue *warnings*.

**The Problem:**
The warnings are bulky and clutter test output.
The issue behind the warnings needs to be fixed.

**The Solution:**
Think fast but GO SLOW.
Work through the warning, and trace it to the root.

**Off to the Races - Where's My Horse?**
Having learned to *write* tests only months ago, debugging test output seemed important and exciting but I was at a loss for how to solve this.

I channeled my inner Alan (test expert on my team) and knew I first had to slow down. Before I even *thought* about fixing anything, I had to find the test with those warnings.

**1. Where are the warnings coming from?**
From the CLI output, it *looked* like the warnings originated from this test:
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/p24ivae46bnx2ym93y6p.png)

But locally, that test had no warnings. Boo hiss.

I re-ran the tests, scouring the output as it was emitted, and I found the warnings under a different test:
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/zfk4i343wjh1qsrtzwxf.png)

**2. Trace back the warning message.**
The warning: `WARN: '%cUnhandled rejection Error: cancel`

I did two things here. 

First, I read through the warning message (which was at least a dozen lines long) slowly and thoroughly, looking for any clues. Second, as another expert on my team says, I did some Googles. 

From what I'd seen and read, I surmised that the warning had to do with promises.

**3. Phone a friend.**
Writing tests with promises is tricky business, so I called in our test expert, Alan. His experience and exposure to test writing has made him an incredible source and teacher.

We looked at the tests together and noticed a few methods: open() and cancel(). 

We traced them to the component itself (vs the test):

```
	methods: {
		open() {
			if (this.modalOpen) {
				return this.deferred.promise;
			}

			this.modalOpen = true;
			this.deferred = this.createDeferred();

			return this.deferred.promise;
		},

		cancel() {
			this.modalOpen = false;
			this.resetForm();
			this.deferred.reject(new Error("cancel"));

			return this.deferred.promise;
		},
```

cancel() caught Alan's eye - specifically this part:

`this.deferred.reject(new Error("cancel"))`

*This* was our problem. Our warning message (`WARN: '%cUnhandled rejection Error: cancel`) contained the word "cancel" and that word was coming directly from within our cancel() method.

Finally, connecting the dots!

The other piece Alan knew (that I did not) was that for this particular test, we were using Bluebird (a third-party promise library). 

And because of Bluebird, we know that an error will always be thrown.

And, we need to DO SOMETHING with that error - primarily catch it - or Vue will scream at us.

**4. Mini celebration - we (ahem, Alan!) found the root issue.**
Yay!

**5. Back to the test.**
There did not seem to be one perfect solution but many ideas to test out.

We first settled on wrapping our expect statement in a catch block:

```
app.vm.deferred.promise.catch( () => {
	expect(app.vm.hasError).to.be.false;
	done();
});
```

We re-ran our tests, et voila - warning messages disappeared.

**6. Yee old refactor.**
Although we did not end up refactoring, it's worth mentioning that there was great deal of discussion about possibilities. To avoid the chaining, to make the code cleaner, to stick to standards set elsewhere. All up for consideration.

In the end, the best solution remained our first solution, but it was a great lesson for me - there will always be pros and cons to the way we code/test.

**Big Sigh, Happy Day**
No two warnings are the same and debugging this stuff will always present a challenge. But there is hope. As test-expert-Alan kindly and wisely always says, "It's just a matter of practice."

Cheers to practice and cheers to more challenges.

If you have great practices for test debugging, comment below and let me know! And thanks so much for reading.

[Get in touch](/pages/contacts) any time.