---
date: 2021-01-14
type:
- post
- posts
title: Hello World!
weight: 10
---

## New year new blog
After what seemed like ages since my first (revised) blog post on my first CTF writeup, I've decided to
move my blogging platform to a new [domain](https://0x4.dev) and do another makeover. This would be the third
iteration of my blog as of this date, however I am confident that this will be my final major revamp of the website for awhile.

## My issues with an all-in-one CMS
Originally, the previous versions of the blog were developed with [Stackbit](https://stackbit.com). Although this was a trivial
way to generate a JAMStack website, The tight coupling of the stack prevents much tinkering around without a full knowledge
of how the stack operates. For example, after understanding how the hugo template works, there is still a danger of desyncing
with ForestryCMS if one is not careful enough. There were also occasions where I encountered a desync between Stackbit and 
ForestryCMS, which was a huge pain to diagnose and fix.

## Towards the future
In the end, I went back to the basics and went with a clean hugo install and a template. No more CMS will be implemented in this
version of the blog since it's more trouble than it's worth, especially since 
I know my way around hugo already and don't need anymore desyncs. Once again, Netlify would be used to host the static web page.
Aside from the DUCTF writeup posted on the previous blog, all previous posts will be deleted and new content writeups 
will hopefully last here for the foreseeable future. I plan to implement a menu bar for quick navigation within the article as well as some
automation to build my website once a change in the repo is detected. Images will soon be hosted on [ImageKit](https://imagekit.io)
to maintain the JAMStack serverless approach. 

## A better 2021
2020 has been tough and I personally experienced one of the biggest highs and lows of my life during this unsettling period. 
As I continue to blog my adventures and grind University in the confines of my room due to the lockdowns in Malaysia and Australia,
I wish everyone a better 2021 and to stay healthy and safe. Cheers.
