---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: Connor Morley is a senior security researcher at F-Secure. A keen investigator
    of malicious TTP’s, he enjoys experimenting and dissecting malicious tools to
    determine functionality and developing detection methodology. As a researcher
    and part time threat hunter he is experienced with traditional and ‘in the wild’
    malicious actors’ behaviour.
  handle: false
  name: Connor Morley
  photo: https://pretalx.com/media/avatars/Connor_Morley_F-Secure-684x513_wkPtGH4.jpeg
timeslot:
  duration: 30
  end: 2022-05-16 10:30:00+02:00
  start: 2022-05-16 10:00:00+02:00
title: MacOS Endpoint Security Framework - What it can do and how to use it
track: 1
---

Endpoint Security Framework (ESF) is the new(ish) security auditing tool that Apple has introduced to provide the security industry with a one stop shop for all its telemetry needs.
Released in MacOS version 10.15 in 2019, the ESF is capable of providing real time telemetry for detection and automated defensive purposes without a Kernel Extension.
This talk will provide an explanation as to why this was introduced, how it can be used and some of the real world applications and issues with its use.

This talk will focus on the Endpoint Security Framework (ESF), it’s capabilities, how people can use it and the issues that are involved with its deployment for detection work.


The material will cover an explanation of why the ESF has been introduced by Apple and what purpose they intend it to fulfil.
This will cover the deprecation of Kernel Extensions and an explanation of the other primary audition solution openBSM and its limitations.

After providing an understanding of what ESF and why it was introduced I will explain how this can be used by providing technical insight into its application to monitoring solutions.
By outlining the issues encountered, how they were overcome and the resulting data sets the audience should have a full understanding of the scope of monitoring provided by the ESF.


Finally I will provide a use-case example of the ESF's telemetry against detecting a Meterpreter agent installation and base command executions.
This will highlight the POC created to demonstrate the ESF data collection capabilities and the particular event types of interest for malicious behaviour detection.