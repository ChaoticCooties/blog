---
title: DownUnderCTF Write-up
thumb_img_path: "/images/obgolnld_400x400.jpg"
date: 2020-09-20
layout: post
content_img_path: ''
---

> Note that this less technical than a typical CTF write-up and is more focused on the OSINT parts.

### Background

I am an undergraduate student currently undertaking my Bachelor's of Computer Science in the University of Queensland. Although this was my second semester in UQ, we (UQCyberSquadB) managed to achieve top 10 global ranking as well as a 2nd place in the Top Australian Secondary/Tertiary scoreboard. A huge shoutout to Falzar, Tye Bryant, Pyro, and Hawko as this wouldn't have happened without them.

## Challenges

### A turn of events w/ some REALLY bad OPSEC

This was my favourite question throughout the entire CTF since it involved less guesswork  and a variety of searching around. Also, this was our team's one and only first blood.

> We have identified the key suspect in multiple crimes, with authorities in pursuit. The suspect has been placed on the Interpol red list, and is believed to have already escaped the country through some unknown form of transport. Locating the transport the suspect took will be vital, and with lives on the line, time is of the essence. Provided attached is the evidence collected in this case.
>
> ![](/images/suspect-file_au00045733.jpg)

By carefully reading through the redacted document and doing a bit of guessing, we can deduce a few important points:

* The perpetrator is a Female.
* **Last location was near something.**
* MAC address on a burner phone.
* **possession with gelato(?) and has a cat named Alexandros.**
* **Supposed to leave at 2020-09-18**

The bolded points were what caught my eye judging from the 4th point we know for almost certain that it was Emily Theresa Waters (refer to by Petstagram write-up at the bottom if you don't know who this is). Going back to her instagram profile, I noticed her latest's instagram post had a located tagged:

![](/images/untitled23-3.png)

Initially, we thought that there was a significance to the number dial in the background but after a few attempts at decoding and trying various methods, we figured that it was just a false flag.

A quick search of Gelateria on the Docks shows us that this restaurant is located in Melbourne. I initially assumed that she escaped by plane but a teammate mentioned that it was close to a body of water and so that a boat was more probable. ![](/images/untitlasdgfyed-4.png)

Prior to the updated challenge, the perpetrator was said to have left by **2020-09-12** however all free online databases only had port calls records up to **2020-09-18**. I then eventually gave up on finding the port call records until...

The challenge was then shortly taken down for a "fix" and the new redacted document was put back up with the updated date of **2020-09-18**. Right away, I knew that I was right on its trail and found the boat.

Flag: DUCTF{SWHR_CAP_VICTOR}

### Outback Stakeout (482)

> My favourite place to grab a snack. Where is this and, how many dishes are there?
>
> ![](/images/dont_dish_out_what_you_cant_take.jpg)

Judging from the title and the picture, I knew that this was in the Outback and instantly fired up Google Earth to try and find a slightly similar landscape:

![](/images/untitledzxc2.png)

I first thought that the Macdonnell ranges was the answer which was close sounding to "McDonald's" and attempted that as the flag. In hindsight, we call them Maccas here so that was a blunder on my part. It did make me crave for Maccas for dinner though.

After a bit of thought, I remembered about SETI and tried searching for any satellites in Macdonnell range and found this interesting post:

![](/images/untitled-21245.png)

Searched up Pine Gap and it was very similar to the aerial photo the CTF question gave. So I attempted it as a flag and it got accepted.

Flag: DUCTF{pine_gap_38}

### Off the Rails 3 - LOCOmotive (486)

> There are 2 sections/segments to the flag, each of the sections have two points of data that require you to actually solve rather than by guessing. Each section, each different point and space of the flag is separated by an underscore _ . All of these are Australian places.
>
> **Section 1:** Someone took the challenge name to heart, where was it coming from and the military time that it happened?
>
> ![](/images/section_1.png)
>
> **Section 2:** We don't all live downunder(ground), and when we do its at 1134. What is the colour of the previous occupant's car and the name of the cereal?
>
> ![](/images/section_2.jpg)

**Section 1:** The first section was solved by my teammate Falzar. Presumably from the challenge title, he searched for any train derailment accidents/reverse image search and solved the first section with ease.

![](/images/untitled-5-copy.png)

Section 1: Railton_0909.

**Section 2:**

I first did a reverse image search and noticed that the similar images were actually real estate postings.

![](/images/untitled-12e4.png)

I then searched for "rental 1134" in Google and scanned the listings and stumbled upon this weird/cursed real [estate](https://www.realestate.com.au/sold/property-house-sa-coober+pedy-117234243 "Real Estate"). ![](/images/main.jpg)

Looking into the pictures, we find the exact image that was listed in the CTF question. Also through the pictures we find exactly what we need:

Nutri Grain under the kitchen counter

![](/images/image4-2.jpg)

White Car

![](/images/image13.jpg)

On a side note, this estate looks wack and I wonder how the CTF organisers even found this.

Flag: DUCTF{Railton_0909_white_Nutri_Grain}

### Off the Rails 2: Electric Boogaloo: Far from Home (336)

> Okay so I'm starting to think I _may_ have got on the wrong train _again_ and now it's snowing so hard I have no clue where I am ?. Thankfully, I managed to snap this pic before the storm started. We seem to have stopped at this station.. can you tell me it's name?
>
> ![](/images/no_pain_no_train.png)

Right off the bat, we notice a snowy mountain landscape as well as a rather peculiar red train station. I quickly deduced that it was somewhere Scandinavian (specifically Swedish or Norwegian) and initially thought that it was the same train line as Finse station since they share the same peculiar red railway station. A teammate then pointed out that since Finse railways had overhead catenaries, this was impossible. I then tried pulling up the Norwegian railway lines from [Wikipedia](https://en.wikipedia.org/wiki/List_of_railway_lines_in_Norway "Norwegian Lines") and going through the stations one-by-one. After  a while, I stumbled upon Dunderland: 

![](/images/440px-dunderland_stasjon.jpg)

Since this was strikingly similar to the CTF image, I tried DUCTF{dunderland} and the flag was accepted.

Flag: DUCTF{dunderland}

### In a pickle (200)

> We managed to intercept communication between und3rm4t3r and his hacker friends. However it is obfuscated using something. We just can't figure out what it is. Maybe you can help us find the flag?

The simple way to obtain the flag in this challenge was to just import the pickle library for python and load it.

    >>> import pickle
    >>> print(pickle.load(open('data', mode='rb')))

However, I will extend this section by explaining my personal manual (dumb) way of solving it as I didn't know this solution at the time.

I initially removed all of the newlines from the file and ended up with this

    (dp0I1S'D'p1sI2S'UCTF'p2sI3S'{'p3sI4I112sI5I49sI6
    I99sI7I107sI8I108sI9I51sI10I95sI11I121sI12I48sI13
    I117sI14I82sI15I95sI16I109sI17I51sI18I53sI19I53sI
    20I52sI21I103sI22I51sI23S'}'p4sI24S"I know that t
    he intelligence agency's are onto me so now i'm u
    sing ways to evade them: I am just glad that you 
    know how to use pickle. Anyway the flag is "p5s.

I then noticed that each chunk was incremented by 1 in the format I\[i\]\[ascii\] with the exception of the ones that already have text as they start with the format p\[i\]\[ascii\].

By slowly decoding them with the ascii table, I end up with the flag.

Flag: DUCTF{p1ckl3_y0uR_m3554g3}

### Badman (200)

> We have recently received reports about a hacker who goes by the alias und3rm4t3r. He has been threatening innocent people for money and must be stopped. Help us find him and get us the flag.

I first did a simple google search for und3rm4t3r but to no avail. With a simple google search out of the picture, I used [https://namechk.com](https://namechk.com "https://namechk.com") to see whether the username appears anywhere else on the net.![](/images/untitled-1-copy.png)

I then went onto Twitter and noticed that the profile is awfully suspicious:

![](/images/untitled-2-copy.png)

Also, the profile was retweeting DUCTF posts so I figured this was it. Analysing the posts, one of them caught my eye almost immediately:

> whew that was close.... put out a tweet that contained personal information... well im glad we have a delete button

I then used Wayback Machine to see whether a snapshot was made and there was one snapshot suspiciously made on the 23th of July.  Looking at the snapshot, we can find the flag.

![](/images/untitled-3-copy.png)  
Flag : DUCTF{w4y_b4ck_1n_t1m3_w3_g0}

### Welcome to Petstagram (100)

> Who is Alexandros the cat exactly? And who is this mysterious "mum" he keeps talking about?

Judging from the challenge title, I searched instagram for "Alexandros the cat" and found the first step to the flag.![](/images/untitled-2.png)

Scanning through the posts, one of the first notable thing to check was the cat mum's Youtube page posted.

![](/images/untitled-3.png)

However, the Youtube page had nothing significant in its videos and about page and was written off as a dead end.![](/images/untitled-4-copy.png)

I then checked the people who liked the cat's posts as well as the followers list and noticed an interesting profile ![](/images/untitled-6.png)

Great! We found Alexandros' Mum's instagram! So we went and inserted DUCTF{emily_waters}. However, this was rejected. I then realised that Emily Waters has a middle name, judging from her business inquiry email address **emilytwaters92@gmail.com** which starts with a 't'.

After a few minutes of pondering, a teammate of mine decided to email the business inquiry address and this automated response was given :

> Hello,
>
> I will be out of the office from Sunday, September 6th onward.
>
> If you need immediate assistance during my absence, that sounds like a you problem. Otherwise, I will probably respond to your emails as soon as possible if I return.
>
> Kind Regards,
>
> Emily Theresa Waters.
>
> P.S. I recently made Alexandros an Instagram account. [https://www.Instagram.com/alexandrosthecat/](https://www.Instagram.com/alexandrosthecat/ "https://www.Instagram.com/alexandrosthecat/"). Please go check it out and give a follow.

Flag: DUCTF{emily_theresa_waters}

# Wrap Up

To summarise everything up to this point, I'll state down the key important points that I've learned from this CTF (especially for OSINT):

1. Pay attention to the number of solves and solve time of the other participants as it's arguably a better way to gauge difficulty than the question tags since every author have their own varying measurements for difficulty.
2. Paying attention to what has changed/fixed by the organisers is a dirty way to keep track of what's important.
3. Nothing is trivial to solve a clue. Every move you deemed stupid might be the key to the flag.

Overall, this CTF was a huge success especially since a couple of us were beginners and even first timers. This is the first CTF where I did somewhat well and the second significant cyber security competition that I've participated in (the first being BountyCon 2019). Once again, huge thanks to my team mates and I hope to participate and post up more CTF write-ups in the future.
