---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: Claudia works as penetration tester at NVISO where she focuses on web and mobile
    application security. Apart from spotting vulnerabilities in applications, she
    enjoys helping and training developers and IT staff to better understand and prevent
    security issues.
  handle: false
  name: Claudia Ully
  photo: null
- bio: null
  handle: false
  name: Dominik Holzapfel
  photo: null
timeslot:
  duration: 240
  end: 2022-05-15 13:00:00+02:00
  start: 2022-05-15 09:00:00+02:00
title: 'Going Against the Flow: How to Build and Break OAuth 2.0'
track: 2
---

Be it an API, web service or mobile application – by now OAuth 2.0 has become the most commonly used standard when it comes to granting access to protected resources to third-party applications.
Over time, additional security controls and flow types have been introduced to meet the needs related to different authorization scenarios.
Although built for security purposes, the OAuth protocol still leaves us with some backdoors for exploitation if they were not properly closed during implementation.

This workshop aims to shed more light on the inner workings of OAuth 2.0.
Following a hands-on approach, we will first build our own OAuth environment and the start breaking it.
By the end of this workshop, you will not only be able to tell all kinds of tokens apart but know how to spot and target OAuth in the wild.

The workshop is comprised of three parts:

**1.
Understanding OAuth**

Why do we need OAuth at all; which problems does it solve? And how does it solve them? – The first part will provide answers to these questions and covers all the nitty-gritty of OAuth 2.0.
We will see that it is not as complicated as it may seem at first glance.
And which better way is there to actually understand how everything works together by just implementing a simple OAuth environment ourselves.

**2.
Breaking OAuth**

The second part focuses on an attacker’s perspective on OAuth.
We will look at different ways how to steal tokens, hijack accounts and identify all weak spots in our own implementation.

**3.
Making OAuth more secure**

The last part covers additional security controls and more recent developments that intend to close the backdoors we have seen in OAuth so far.