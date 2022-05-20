---
accepted: true
code: W9SSVK
details: true
keynote: false
layout: talk
speakers:
- bio: I'm doing professional software development since 1992. Since 2001 I'm working
    at genua GmbH, a german producer of security products for public sector, critical
    infrastructure and other sectors. After 10 years of developing firewalls and 8
    years of security research, my focus as a technology fellow is now strategic development.
  handle: false
  name: Steffen Ullrich
  photo: null
timeslot:
  duration: 30
  end: 2022-05-16 15:00:00+02:00
  start: 2022-05-16 14:30:00+02:00
title: MIME is broken
track: 1
recording_uri: https://www.youtube.com/watch?v=yhDPLZOTd2g
slides_uri: 
---

MIME is basically a container format to serialize structured textual and binary data so that they can be presented wiithin the restriction of the original mail, i.e.
unstructered ASCII text with limited line length.
Similar to standards like HTTP,  MIME and related are full of unneeded flexibility and complexity.
It is easy to construct MIME which will be interpreted in different ways by different implementations.
This makes it possible to bypass security systems like mail gateways or antivirus, but also to change messages which deemed to by cryptographically protected with DKIM.