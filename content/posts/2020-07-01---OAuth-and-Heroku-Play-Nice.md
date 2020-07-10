---
title: "OAuth and Heroku Play Nice"
date: "2020-07-01T22:40:32.169Z"
template: "post"
draft: false
slug: "oauth-and-heroku-play-nice"
category: "OAuth"
tags:
  - "Code Newbie"
  - "OAuth"
  - "Herkoku"
  - "Rails"
description: "The time has come for OAuth to work while hosting my Rails app on Heroku. Deep sigh of happiness."
socialImage: ""
---

Hosting my Rails app on Heroku was A Lot. But that story ended in success!

And yet, when I tried to log in using Google, no dice. My OAuth authentication that worked seamlessly prior to hosting on Heroku was now broken.

I won't tell you *exactly* how long it took for me to address this issue, but I will approximate: 2 months, shame on me!

My ever-patient-and-generous friend Noah helped me get the ball rolling, and I owe this guide and this knowledge to him. 

In the event you are in a similar spot and need to get your OAuth authentication working on your hosted app, Godspeed and may this help.

##Assumptions

1) You have built a Rails app with third-party authentication using OAuth.

2) You've already gone through the initial setup of Google APIs and created your original OAuth Client IDs - which you used within your app.

3) OAuth authentication is working when you host your app locally.

##Start here

1) Go here: [Google APIs](console.developers.google.com).

2) In the left-side menu bar, click on **Credentials**.

3) There you should see the header, **OAuth 2.0 Client IDs**.

4) Create a new URI (and keep the existing).

`https://your-app-url/auth/google_oauth2/callback`

6) Save your updates.

7) You'll then need to set your google client id and secret, and you can do so within your terminal. 

Run the following two commands:

`heroku config:set GOOGLE_CLIENT_ID=yourclientid`

`heroku config:set GOOGLE_CLIENT_SECRET=yoursecret`

It will set the id and secret and after each, restart the app.

8) Thought that would do it! But, login via Google continued to fail, and this time I received a semi-helpful error message about cross-site request forgery (csrf).

To combat this, I added the following to both my Users Controller and Sessions Controller - both of which deal with login:

`skip_before_action :protect_from_forgery, raise: false`

And that did the trick. 

If you've given this a try, or even if you've figured out how to do this already, sure would love to hear about your experience!

[Get in touch](/pages/contacts) any time.

Thanks so much for reading - until next time.