---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: Cyber Security Researcher
  handle: false
  name: Hido Cohen
  photo: https://pretalx.com/media/avatars/profile_au6ASHJ.jpg
- bio: Security Researcher
  handle: false
  name: Arnold Osipov
  photo: https://pretalx.com/media/avatars/2AD2B9E2-D2DC-4D6D-9610-759319CAD243_xTffIj3.jpeg
timeslot:
  duration: 30
  end: 2022-05-16 12:30:00+02:00
  start: 2022-05-16 12:00:00+02:00
title: From a simple log to sophisticated crypter
track: 2
---

As security researchers we always strive to find the next piece of malware no one else has seen before.
For this, we use our telemetry and research skills to understand a threat and the story behind it.


In this talk, we share our research about an emerging threat we’ve dubbed the Babadeda crypter.
From what looked like an anomaly in our telemetry, we slowly identified more details about this sophisticated crypter.
We started with a deep dive analysis of the crypter’s inner workings, and discovered its handful of usages in the wild.
This led us to reveal its use in major campaigns targeting NFT communities and Ukrainian companies.
The evidence we collected along the way led us to attribute this to a Russian actor.

1.
Who we are?

We are part of Morphisec’s Research Team.

Arnold Osipov has been a security researcher at Morphisec for the last three years.
He specializes in malware research and threat intelligence.
 
Hido Cohen has been at Morphisec for the past year.
Before that, he served in an elite Israeli intelligence unit where he was introduced to the amazing world of cyber security and malware research.

2.
Encountering an Unknown Crypter 

We explain how we investigated a simple log in our systems which revealed a much more sophisticated crypter.
This was used to deliver multiple malware families such as Amadey, Cryptbot, Ursnif, Remcos, and more.
This crypter stayed under the radar for a long time because of its low detection rate.

3.
The Crypter’s Internals 

Before talking about the campaigns using this Crypter, we need to understand how it works, and what makes it so evasive—and in some cases fully undetectable (FUD).
We explain each component of the crypter:
- The installer that impersonates a legitimate application
- The DLLs used for persistent loading and payload loading
- The shellcodes that perform the actual payload decryption and injection

4.
The Crypter’s Uses, Including an Ongoing NFT Campaign 

After our technical analysis, we show the most impactful uses of the crypter.
We also reveal how we discovered an ongoing campaign targeting the NFT community.
We provide details about our research:
How we utilized Discord for threat intelligence and to contact victims
How we tracked more victims, and how we stay up to date with new attack waves
Breakdown of the attacker’s infrastructure and evolution over time
How we attributed the threat actor

5.
Babadeda Against Ukraine 

The most significant recent use of the Babadeda crypter is in a campaign targeting Ukraine.
We show how the crypter is used to deliver Outsteel—a malware used by the Lorec53 group reportedly attacking Ukrainian state organizations.

6.
Summary and Questions