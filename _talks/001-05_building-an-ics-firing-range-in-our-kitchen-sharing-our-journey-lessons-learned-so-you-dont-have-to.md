---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: Nico has worked in IT security for over 15 years as security consultant and
    penetration tester. For the past years, his focus has been on all several aspects
    of OT security. At NVISO Germany, he leads the security assessment team.
  handle: false
  name: Nico Leidecker
  photo: null
timeslot:
  duration: 30
  end: 2022-05-16 13:00:00+02:00
  start: 2022-05-16 12:30:00+02:00
title: 'Building an ICS Firing Range (in our kitchen): sharing our journey & lessons
  learned (so you don’t have to)'
track: 1
---

Aiming to improve our own expertise in ICS security, we went to build our own ICS firing range for internal and external trainings, and hacking demos.
It covers multiple technical aspects about IT infrastructure, PLC configuration and programming, ICS protocols and specific methodologies for red and blue teaming.
Beginning with a bridge operation scenario we planned our approach on implementing the ICS Firing Range addressing all levels of the Purdue Model, from enterprise to physical processes.
We were faced with a variety of practical challenges and challenges specific to the ICS context and prototyping: we learned how to implement ladder logic, how CAD modelling works, how to print 3D models with a 3D printer and how to combine all ICS and bridge components into a single, confined and mobile lab environment.
Lastly, we designed a series of kill chains for our firing range that we use for trainings on a variety of professions such as digital forensics and incident response.

During the talk, we’ll go into detail what motivated us to build the Firing range, why and how we and other can benefit from it.
During the session we’ll show videos or live feeds of the actual lab in action.
Most importantly, we want to share the lessons we learned throughout this journey, so the attendees to our session can hit the ground running building their own ICS environments.
The session is split in four parts:

Introduction:
We’ll touch on the general differences between IT and OT and why experience is crucial before doing any potentially intrusive testing on OT infrastructure.
This addresses the motivation behind the firing range to provide training opportunities in a safe environment for both, the Red & Blue Team.

Demonstration:
We will demonstrate how the Firing Range works & how we can interact with it from a user perspective, prior to diving into understanding how we got to engineering this.

Sharing Lessons Learned building our Firing Range:
Starting with the planning of the lab, we demonstrate the rationale behind decisions, difficulties with acquisition and inter-dependencies of components and software, and the overall design of the lab.
There are several key implementation steps to touch on.
Those include designing the IT and OT network architecture, 3D Printing, PLC Programming.
This concludes with taking a look at the timeline and bottom-line cost.

Scenarios:
The lab should serve purpose to red & blue teams but also be versatile enough to deploy it for R&D or isolated ICS component testing.
We’ll present how different scenarios can be deployed in the lab and walk through a red team kill-chain whereby one of the Bridge’s central PLC’s is compromised by a remote adversary with initial foothold in the virtualized enterprise IT network.