---
date: 2018-11-11
layout: post
title:  "A place called home"
---

Hello there!

Recently I started up a server at home for ehm.. research purposes. Totally not for downloading stuff. It has a nice NFS sharing configured, so I can reach some of the files from my local network. Easy to set up, there are plenty of tutorials doing it. When I started to use it, I got frustrated - I wanted to use it like a normal folder, and not to worry about mounting. Surely there are some tools out there that can solve my problem, but I wanted to make a script for myself.

What I wanted to accomplish?
1. mount the data server automatically
2. do not mount the data server if I'm not at home
3. wait for the wifi to be connected

After some googling I found where I can start: need to add a script to the Network Manager's if-up directory. I spent some time figuring out the exact code, checking if my wifi adapter connected to a network, and that network is my home-router. Usually I don't write too much bash script, so I had some troubles, but in the end, it all worked.

Then my flatmate asked me how did I do this, he wanted to do the same. I go back to my laptop, copied and sent the code - and it hadn't worked. Quickly I realized I forget a configuration I had to add somewhere else. Then we have to apt-get a package that is required to do the NFS sharing. All-in-all it was a mess to reproduce what I've already done before.

This is when I decided to create a [Homergrown Scripts][homegrown-scripts-github] repository. I wrote everything down what I had to do to make the NFS sharing work - then I transformed into an install script. It checks if I have installed the required packages (and installs it if needed), creates some script files and places them in the right folder and set up every configs.

I would like to collect all of my magic tricks into this repository, so the next time somebody asks me, how to do this or that, I can just show them without thinking. Also, some of my personal preferences could be saved this way, so I will be able to reinstall my laptop without fearing that I will lose one of my precious configurations I did years ago.

[homegrown-scripts-github]: https://github.com/kiskoza/homegrown_scripts/
