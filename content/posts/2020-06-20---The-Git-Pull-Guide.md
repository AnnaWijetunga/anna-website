


GitHub is powerful and often magical.

But learning the ins and outs has been *stressful.*

Recently my programming partner and I started building an app and realized, we had no idea how to contribute to a shared repo.

OH BOY.

A *lot* of trial and error led us to push and pull requests like we were born to do them.

Mostly to remind myself how to do this again (full disclaimer), but also to be a guide anyone else learning (kudos to you!), I present:

##The Git Pull Guide

First and foremost, [this guide](https://opensource.com/article/19/7/create-pull-request-github) was my saving grace.

But the reason I'm writing my own is that I varied from the above guide in a few ways to make it work for me.

Here's my take.

**1) To fork, or not to fork?**

The author of the original guide would advise you to first fork the original repo.

This caused me to pull my hair out (when I eventually tried to push changes to the original repo), so I do not recommend doing that. 

But keep in mind, that is a viable option.

**2) Clone the repo.**

`git clone https://github.com/<YourUserName>/demo`

**Note:** when cloning, use the `https` version of the repo, not the `SSH.` I wish I knew why (do you know why?) but it does matter.

**3) Switch into your new directory.**

`cd cool-app`

**4) Create a new branch.**

`git checkout -b new_branch`

**5) Create a new remote for the upstream repo.**

`git remote add upstream https://github.com/name/appname`

Here, "upstream repo" refers to the original repo.

And now, you should be in that branch.

**6) Make a change to the code and push it to the new branch.**

`git add .`

`git commit -m "Add readme"`

`git push -u origin new_branch`

If that goes through successfully, you'll see a message similar to this:

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/9la8z0i2wzfitsi2rhac.png)

*Photo credit to Kedar Vijay Kulkarni*

**7) Head over to GitHub the repo itself. The green `Compare & pull request` button will appear in the original repo.**

Click it and you'll see the `Open a pull request` page. 

There, you'll see another green button, this one says `Create pull request` and you can do just that.

**8) From now on, you can make a change and push that change via this command:**

`git push origin new_branch`

And create a pull request from there.

Tears of joy, applause, so happy. 

Thanks so much for reading, catch you next time!