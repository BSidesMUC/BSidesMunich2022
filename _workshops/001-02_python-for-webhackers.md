---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: "I work as application security engineer at [REDACTED] and I'm active collaborator\
    \ of OWASP Guatemala chapter hosting the OWASP nights and also as leader of HackTheBox\
    \ Guatemala meetup.\r\nI like code, I'm way better at reading than writing it,\
    \ but I feel competent in python.\r\nI like all-the-things-computers and currently\
    \ I'm day dreaming about becoming a hacker :D"
  handle: false
  name: Diego
  photo: null
timeslot:
  duration: 240
  end: 2022-05-15 18:00:00+02:00
  start: 2022-05-15 14:00:00+02:00
title: Python for webhackers
track: 1
---

This workshop goes beyond your classic python based port scanner...
The workshop focus on automating SQL injection, NoSQL injection,  CSRF bypass, CORS,  bassic fuzzing using python, threads, sockets and the fun stuff that  missed in your "Python for hackers 101".

We will explore use-cases in the form of vulnerabilities/exploits that allow us to leverage the python language for doing fun stuff in an automated way and that allow us to recycle such exploits for other endeavors :

- Case study 1: Multithreaded NoSQL injection exploit Box mango from hackthebox.
    * Learning outcomes: Multithreading, Blind NoSQL injection.
- Case study 2:  Atutor CVE-2016-2555 - SQL injection to RCE.
    * Learning outcomes: Blind SQL injection, automated database enumeration, type-juggling, insecure fileuploads.
- Case study 3:  Netcat-ish implementation in python.
    * Learning outcomes: Sockets, reverse shells, client-server
- Case study 4: Listener for data exfiltration over DNS
    * learning outcomes: DNS servers, base64 encoding, data exfiltration.


Disclaimer: All this content could be learned from different paid and free resources on internet.
The exposition of this information is in the best interest  of the hacking community and I don't own credit for discovering any of these techniques.