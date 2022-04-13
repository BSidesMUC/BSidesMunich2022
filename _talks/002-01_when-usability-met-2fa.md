---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: Masters Student, Graduate School of Information Security, KAIST
  handle: false
  name: Hyunsu Kim
  photo: null
- bio: SoftSec Lab in KAIST
  handle: false
  name: Junoh Lee
  photo: null
- bio: .
  handle: false
  name: Kihong Heo
  photo: null
timeslot:
  duration: 30
  end: 2022-05-16 10:30:00+02:00
  start: 2022-05-16 10:00:00+02:00
title: When usability met 2FA
track: 2
---

In this talk, we discuss how recent attempts to enhance security in KAIST, one of the authoritative research institutes in South Korea, lead to an even more serious security risk.
In particular, we present several design flaws we found in the KAIST’s new 2FA system and demonstrate how an attacker could bypass the entire authentication process using the vulnerabilities.
This incident highlights that a seemingly trivial design mistake while emphasizing usability can jeopardize the whole system.
We conclude this talk by sharing a lesson we learned.

KAIST, which is a leading research university in South Korea, has been an appealing target for security threats.
As an example, a recent attack on the library (in 2020) resulted in massive privacy breaches that have affected over 30K KAIST members including former employees and students.
The attack specifically targeted the archive for research data and laboratory notebooks that may involve state secrets.

Such incidents had urged the university to establish an enhanced authentication system with two-factor authentication (2FA).
In particular, the university made 2FA mandatory for every member, which, in theory, will thwart attackers who have access to leaked passwords.

Unfortunately, the university introduced another authentication mechanism, named “easy authentication”, to improve the usability while enabling 2FA.
The easy authentication lifts the burden of the user by providing a smartphone app that helps authenticating the user with their phone’s own authentication mechanism, such as face ID and fingerprint authentication.
It also sends a push alarm to the user to ease the authentication process.

However, we found several critical design flaws in the easy authentication system, which allow the attacker to compromise user credentials without having to know the passwords.

First, the easy authentication was not properly two-factor authenticated.
The login page asks the users to enter only their ID, but not their password.
When a user enters an ID, the system will send a push notification to the registered app, and then, the app will authenticate the user.
This means the system was effectively 1FA, but not 2FA.
While this design enhances the usability, it inadvertently reduces the security guarantees of 2FA.
This design flaw allows an attacker to launch a large-scale exploitation targeting multiple users of the system by simply knowing their IDs.

Moreover, we found that an attacker powered by an IP-spoofed botnet can launch an undetectable DDoS attack on a victim.
Once done, it could prevent the user from logging in to the system.
Last but not least, the newly introduced authentication protocol did not properly check the response from the app, which renders the entire authentication system meaningless.
The web server did not properly check the authenticity of the app’s response, and an attacker could carefully craft a web request to bypass the entire authentication system.
This allows an attacker to login as any arbitrary user ID without having to know the password.
We further found user ID leakage and IDOR (Insecure Direct Object Reference) vulnerabilities, which are all due to the careless design of the system.

Eventually, the design flaw was partially mitigated with the additional confirmation: showing a two-digit number in both client app (browser) and the authenticator app (mobile device).
Several meetings with the institute administration were held to compromise on the middle ground.
The story about the process and the remaining drawbacks will be presented in the talk.

We will conclude this talk by sharing a lesson we learned: properly implementing easy-to-use 2FA without weakening the security can be tricky.
Thus, thorough software testing or formal verification processes shall be associated when designing it.
Employing a new security feature without security in mind can break the entire system.