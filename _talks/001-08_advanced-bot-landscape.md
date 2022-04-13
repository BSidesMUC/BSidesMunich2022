---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: Yohann Sillam is a researcher from Imperva. He continuously monitors cyber
    security attacks detected in the wild, publishes blog articles about hidden ones
    and finds innovative ways to tackle them. He has more than 3 years of experience
    in cyber security, especially in malware analysis.
  handle: false
  name: Yohann Sillam
  photo: null
timeslot:
  duration: 30
  end: 2022-05-16 16:00:00+02:00
  start: 2022-05-16 15:30:00+02:00
title: Advanced Bot Landscape
track: 1
---

Bad bots traffic represents around a quarter of Internet traffic today and is predicted to increase.
This traffic includes website content scanning, stolen credit card checking, denial of service, inventory...

In this talk, we describe how as a security company we tackle this variety of threats, how we started our research, the challenges we faced and the solutions we provided.

This talk includes an overview of the general trend in terms of popular bot programming languages, software development frameworks.
Then, practical examples will be taken from the most prevalent bots from the OWASP top 10 automated threats.
The general architecture of those bots will be displayed.
The main components explained before drilling down to the key features they include to remain undetected.
How do they evade captcha systems ? How do they avoid fingerprinting ? From the naïve approaches we will introduce you to the most stealthy features.

- Intro, simple slide about who I am and the purpose of my work
- Introduction about advanced bots 
        > Types of most popular bots sold in forums(scalping, scraping, password checkers ...)
        > Market ( popular Youtube channels, Discord channels with > 100k people, > 100 bots regularly sold on botbroker.io, huge prices of popular bots ...)
        > How we achieved to collect the source code of many advanced bots  
        > Funny copping video showing bypass of PerimeterX in real time (https://youtu.be/9MK6IO5FYEk)
- The internal structure of an advanced bot
        > Explanation of the graph of the main components of a bot (Proxy management system, Automatic captcha solver, human like mouse motion system ...)
        > Step by step description of the procedure flow of an advanced bot.
- How advanced bots evade detections 
        > Meddling with HTTP headers and user agents
        > Simulation of human mouse motion via combination of Bezier curves.

        > I illustrate with snippet of codes, pseudocode to make my point understandable.
- How to overcome those evasions techniques as a security solution
        > Concrete case based on the flaw of a snippet of code
        > It's a cat and mouse game but analyzing the source code of the opponent is a great advantage.