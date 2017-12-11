---
layout: post
title:      "Creating a CLI Gem"
date:       2017-12-11 00:36:30 +0000
permalink:  creating_a_cli_gem
---


It was fun getting to choose the domain model I wanted to work with for this project. I knew it would be helpful to choose something interesting to me, I love listening to Ted Talks so creating a list of the most popular talks with details on each sounded exciting.

The most helpful resource for me was watching Ari's walkthrough (https://www.youtube.com/watch?v=lDExWIhYKI). I used it more or less as a code along, writing the classes and scraping methods for my application while he wrote his. The most challenging part of this project was actually setting up my work environment. I had been using the Learn IDE but working in the temp directory with an unstable internet connection felt like a bad idea. I decided to copy how Ari was working in the video so I setup Atom along with the terminal on my MacBook. I took a while to get used to working this way, figuring out how setting up my repo, creating a local folder and making sure everything was pushing to Github correctly. 

The next big challenge was setting up require and require_relative in my files correctly. I was used to this being given in the lessons and hadn't paid much attention to how it worked. After testing different combinations and doing some Google searches, I finally got things working. It was challenging to look for answers on my own without the help of a technical coach but when I did figure it out, it was more satisfying and I feel I understand it more than if someone had explained everything to me right away.

Once everything was set-up, the worked flowed pretty easily. I started by setting up my CLI to perform the way I wanted it to and built out from there, hard coding at first until I had each piece live and working. When I first started, I had my scraping code inside my main Talk class. Once it worked, I moved it to it's own class, but then I realized I was sending hashes to the CLI class and the requirements said to make sure to build full objects. At that point I reworked my Talk class to read and write the values of each attribute rather than sending an array of hashes and printing out keys and values in the CLI.

If I had more time, I think it would be neat to go back and create a Speaker class that would belong to the Talk class. I could provide more details on each Ted talk speaker like bio and website and allow the Talk speaker attribute to carry more info than just a string with the speaker's name. Another thing that bugged me was the way I named the repo - toptedtalks rather than top-ted-talks. I let it go imagining I could go back and fix it but by the time I had my environment set-up, it seemed daunting to figure out how to fix everything that would break if I tried to make the change. Next time I'll be more careful when I'm naming a repo.

Feels great to have planned and completed this project on my own, looking forward to receiving feedback. You can find the repository for this project at https://github.com/sherryptk/toptedtalks_cli_app.
