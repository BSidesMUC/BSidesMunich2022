---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: '[Andrey Konovalov](https://xairy.io/) is a security researcher focusing on
    the Linux kernel. Andrey is a contributor to several security-related Linux kernel
    subsystems and tools: KASAN — a bug detector and a security mitigation, KCOV —
    a coverage collection subsystem, and syzkaller — a production-grade kernel fuzzer.
    Andrey also found and exploited a number of vulnerabilities in the Linux kernel.'
  handle: false
  name: Andrey Konovalov
  photo: https://pretalx.com/media/avatars/profile_mZulaNw.jpg
timeslot:
  duration: 30
  end: 2022-05-16 12:30:00+02:00
  start: 2022-05-16 12:00:00+02:00
title: Fuzzing USB with Raw Gadget
track: 1
---

This talk is about fuzzing Linux kernel USB drivers via [Raw Gadget](https://github.com/xairy/raw-gadget) — a new interface for the Linux USB Gadget subsystem.
Compared to other interfaces like GadgetFS, Raw Gadget provides more control over USB communication allowing the fuzzer to explore unusual paths within USB drivers.

The talk briefly covers the Linux kernel USB subsystem architecture, explains how Raw Gadget is integrated into the subsystem, and shows how Raw Gadget is used to fuzz USB drivers with the help of [syzkaller](https://github.com/google/syzkaller) — a production-grade kernel fuzzer.

[I assume that Description is intended for the review committee.]

I already [presented](https://docs.google.com/presentation/d/1z-giB9kom17Lk21YEjmceiNUVYeI6yIaG5_gZ3vKC-M/edit?usp=sharing) [[video](https://www.youtube.com/watch?v=amEMG63ebQM)] parts of this work at OffensiveCon 2019.
You can find the description of that talk [here](https://www.offensivecon.org/speakers/2019/andrey-konovalov.html).

However, back then the work was unfinished and focused mainly on the syzkaller parts.
This talk focuses on Raw Gadget instead.

The plan is to cover what's mentioned in the agenda and also show-off a few bugs at the end.
The cool part about Raw Gadget is that it allows generating hardware reproducers for the found bugs, so the demos will crash actual Linux machines.
I don't want to put this part into the abstract to keep it as a surprise.