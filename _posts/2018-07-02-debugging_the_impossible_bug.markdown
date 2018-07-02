---
layout: post
title:      "Debugging the impossible bug"
date:       2018-07-02 14:33:34 +0000
permalink:  debugging_the_impossible_bug
---


Ever think you’ve finished a project, only to realize you have a nasty bug that definitely shouldn’t be a bug? That ends up taking another 6 hours to figure out? That was me this weekend.

I had finished my Rails with jQuery project and realized there was an issue signing up through Devise. This was something that I had working, so why it was suddenly broken felt especially annoying and unnecessary. Once I accepted this was my reality, I got to trying to figure out what was going on. 

When I entered a new email and password on the sign up screen and hit sign up, nothing happened. When I inspected what was going on through Chrome, I saw a post request was being sent to create a new goal (this is a goal tracking app). What made it even more perplexing was the fact that I could sign up and log in successfully through Github using Omniauth. As far as I know, the form to create a new user is supplied by Devise and something I’m not even able to access. So why was the submit button having an identity crisis? (Trying to create a new goal instead of a new user.)

I took a look at all the code I had set up for Devise, nothing had changed since it was working. (And keep in mind, it was still working if you signed up through the Github strategy.) Nothing was changed in my routes either. The specific error in the post request to create a new goal was missing params, so I took require out of my goal_params, but this only broke a bunch of other things. 

I wondered if something in my controller was redirecting in a weird way, jQuery and JSON are newer to me so I could have easily been overlooking something simple. I tried pasting my older goals controller, before I added jQuery to the project, but same issue. After a couple hours of deadend debugging, I decided to pull the last working version and slowly add everything I’ve worked on since then, and see if I could find the culprit.

My process was to add a page from my newer code, launch the server and try signing up. Everything was going smoothly until I added my goals.js page. BINGO! I knew what page it was coming from now. This was somewhat exciting however there was still a lot of code on that page. I started commenting out one function at a time, to see if removing a certain one would get the sign-up to work. And it did. I now knew it was my function on the new goal form that posted the new goal without a page refresh.

While I was making progress, I still had no idea what it was about this function that was ruining everything. I pasted it into the Learn Slack channel and asked for help. A few hours later, someone was kind enough to take a look at it. (Thank you, Lyndsey Dennis!) We went back a forth a few times, covering the basics. Once she understood that the sign-up was working correctly without the function, she had the most wonderful, lifesaving thought. Could there be variables with the same name? Could Devise have named the sign-up form ‘form’ while at the same time my new goal form was named ‘form’?

YES. YES, THAT WAS IT. Looking back, this feels like the most obvious reason possible for my bug. The entire time I wrote this blog post, I was screaming at my older self “how have you not figured this out!” But hindsight is 20/20 and this was a new type of bug for me. Because I persistent and spent so many hours determined to figure this out, the next time I have weird behavior like this, I’ll realize it was duplicate variables way sooner than it took me this time (again, thank you, Lyndsey!) Some lessons are learned the hard way but that’s called the learning curve. My Facebook cover photo is of a man juggling plates in front of an admiring audience. What they don’t see are the dozens of broken plates behind him, the mistakes it took for him to learn how to make juggling plates look so easy. Being a good debugger means many hours debugging, aka, making mistakes. Eventually, the once impossible bugs will become easy to solve.

