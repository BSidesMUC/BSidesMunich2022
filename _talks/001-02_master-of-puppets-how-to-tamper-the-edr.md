---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: Daniel Feichter works since a few years as red teamer and penetration tester
    in Austria. His focus is on Windows environment red teaming, pentesting and research.
    Among other things, he is intensively engaged in AV/EDR systems under Windows
    OS. At the end of 2021 he decided to start his own company which is called Infosec
    Tirol (https://www.infosec.tirol), with which he focus on product independent
    offensive security services to improve the IT-Security in companies in Austria.
  handle: false
  name: Daniel Feichter
  photo: https://pretalx.com/media/avatars/Daniel_E5D_3295_copy_mVSI7w0.jpg
timeslot:
  duration: 30
  end: 2022-05-16 11:00:00+02:00
  start: 2022-05-16 10:30:00+02:00
title: 'Master of Puppets: How to tamper the EDR?'
track: 1
---

Despite admin privileges an EDR product in Windows can be very annoying from red team perspective.
Therefor we search ways to disable the EDR without relying on a uninstall password, Windows security center etc.

A talk about strategies how to tamper EDR products under Windows.
Also as administrator it isn't always as easy to find a way to bypass good EDR products.
For example, you were able to comprise your first host in the target network and you also where able to escalate to a local admin.
On the host you see, that there are open high integrity processes from an domain admin and you want to steal the token of the domain admin or dump the lsass process.
But also as admin you are note allowed to disable the EDR because it is password protected.
Instead of bypassing the EDR we try to find a more or less general path to tamper EDR products in user space and kernel space, that we as red teamers are able to avoid prevention, detection, telemetry collection by the EDR, host isolation by the EDR and EDR repairing of a partly tampered EDR system.
To learn about the strategies we have a closer look at the different components from EDR products in user space and kernel space under Windows.
We try step by step to understand the relationship between the different components (processes, services, reg keys, callbacks, drivers etc.) and by that we try to find a way to completely disable an edr product by tampering necessary components from the EDR.