---
accepted: true
details: true
keynote: false
layout: talk
speakers:
- bio: I am a vehicle security researcher at Desay SV, Singapore. I have a master's
    degree in Information security from Carnegie Mellon University.
  handle: false
  name: Sivaranjani Sankaralingam
  photo: https://pretalx.com/media/avatars/pp_ejJx4gC.jpg
timeslot:
  duration: 30
  end: 2022-05-16 12:00:00+02:00
  start: 2022-05-16 11:30:00+02:00
title: 'Keeping Electric Vehicles Secure: the need for a CAN security framework'
track: 2
---

Vehicle security has gained traction ever since the infamous 2014 Jeep Cherokee incident.
Electric vehicles are widely acclaimed as the future, and with the rising fuel prices and the need to escape the use of fossil fuels, we are in the midst of a massive transition from mechanical to electric vehicles.
Vehicle security becomes a necessity in this climate.
In this presentation, I will first introduce you to the Control Area Network (CAN)  protocol that governs these electric vehicles and outline its inherent security challenges.
I will then take you on a tour through my experience developing an Intrusion Detection System for CAN through different stages.
Finally, I will talk about an encompassing CAN Security framework design that ties it all together.

**1.	CAN Protocol introduction**

A Controller Area Network (CAN) is a message based protocol designed to facilitate communication between the different Electronic Control Units ( ECUs) /components of the car.
To understand a bit more on the protocol, lets breakdown the CAN message frame.

For the sake of brevity , I am omitting the basic message frame details of CAN here in this description.

During the presentation, I plan to pictorially depict the classic CAN frame and highlight the key fields : the identifier , the data length code and the data field itself.
I will briefly introduce the concept of arbitration, which is the allocation of priority to messages which is primarily based on the message identifier.
The lower the ID, the higher the priority of CAN message.
Hence 000 would hold the highest priority in a CAN bus, for example.
Then I will touch upon CAN-FD ( Flexible Data Rate) which has the option to send a larger amount of data in one frame as opposed to the classic CAN.

*Periodic and Event triggered CAN messages* : periodic messages are the ones sent periodically at set intervals to get the current status whereas event triggered messages are the ones sent when an event occurs ( eg: door lock/unlock).

**2.	Security challenges in CAN**

When it was designed in 1983 by Robert Bosch, the primary goal of CAN was to create a priority based message system that can facilitate communication between the nodes( ECUs) in a real time environment.
With a lack of authentication and encryption, CAN Protocol inherently doesn’t address security issues ,as they weren’t a concern back then.
Since it [lacks](https://www.mdpi.com/1424-8220/20/8/2364) confidentiality, integrity and availability , CAN protocol isn’t secure by design.

So what next? CAN protocol would continue to be dominant in the near future so addressing this problem is quite an important one.
There are many solutions that have come up in recent years that tries to address the problem in question.
Secure Onboard communication by AUTOSAR in particular is a secure component/module that can be added to the system to ensure security and minimize illegal attacks/messages from malicious ECUs.
However there is a caveat: SecOC uses almost 2.5 times more bandwidth than CAN and is best suited for only classical CAN.

That brings us to the next option (which can be applied to all versions of CAN): Developing an Intrusion Detection System to detect attacks on the CAN bus.

**3.	Developing an IDS - Phase 1 : Prototype(what worked/why it was a “failure”)**

Designing an IDS is not straightforward.
I tried to breakdown into categories and decided to work towards designing a simple prototype for detecting CAN bus abnormalities.
The goal was to create a working prototype with data that is publicly available.
I chose a highly cited academic [paper](https://ocslab.hksecurity.net/Dataset/CAN-intrusion-dataset) which broadly classified the attacks into three categories.
1.	Denial of Service ( DoS) : Injecting messages of ‘0x000’ CAN ID in a short cycle
2.	Fuzzy Attack : Injecting messages of spoofed random CAN ID and DATA values
3.	Impersonation attack : I skipped this one
The data was collected from KIA SOUL vehicle and used a message request/response based system.
If the DLC field was zero, its a request and the response had a DLC of 4 or 8 and had the same message ID as the request.
For Fuzzy attack , the authors had used any one of the random responses as the original and the other(s) as attack.

Based on this I created a prototype : I first implemented the models mentioned and then decided to generate more attack data using [VECTOR’s](https://www.vector.com/int/en/products/products-a-z/software/canoe/#c60442) CANoe simulator.
I also used some Machine Learning and had a colleague add a Deep Learning feature to this prototype.
We tested the results on a PC and the numbers looked good : 85% - 94% detection rate.

So its good news right? But there was a turning point : When I asked for some sample in-vehicle data from our business units, I noticed that they did not follow the message request-response format.
It turns out that even though this IDS prototype seemed like a good starting point, I was dealing with what turned out to be a corner case.
Furthermore the logic for choosing attack packets needed more depth.
So it was back to the drawing board.

`Lesson Learned`: Always ask for real data before modeling a prototype! Corner cases have to be added at the end and not the beginning.

**4.	Developing an IDS - Phase 2 : PoC/ Proof of Concept (testing with proprietary data on an ECU)**

This time around I gathered 3-4 hours data from a colleague who performed different operations on a car and gathered the in-vehicle data.
Another important information is to get a list of registered/accepted message IDs from the OEMs( in the form of a CAN database file or DBC).
At this stage, I have gathered this information from the data that has been collected.
Then, I set out to design a compact solution that takes less processing power and memory on [IPU03](https://en.desaysv.com/index.php?id=4842) ECU(whose primary function is not an IDS), without compromising on detection efficiency.

The idea is to only consider the message ID and the timestamp(often called as flow based IDS) , analyze the normal patterns by monitoring the sequences in which IDs are sent through the CAN bus, and then develop algorithm(s) that detects abnormalities.

The threat scenarios were as follows :
1.	`Denial of Service` : Sending packets continuously at very small time intervals with the aim of rendering CAN Bus invalid or trying to get highest priority.
2.	`Fuzzing` : Sending packets that model the original one but injected in a different sequence ( think replay attacks).
This is relevant in scenarios where the attacker is carefully crafting an attack packet with the same payload as the original, but doesn’t take into account message probability distributions and sequences.
This applies to both period and event triggered messages.
3.	`Frequency attack` : Similar to fuzzy but only applies to periodic messages.
In case of generating attack packets with CANoe, we changed the frequency distribution from the original and fed it to the algorithm.
4.	`Alien ID` : Any ID not found in normal CAN tracelogs/registered with DBC.

Along with a colleague, I used an CANoe simulator to generate the necessary attack datasets.
I used a probability based statistical algorithm to detect the denial of service and non registered/Alien ID attacks.
I tested out some Machine Learning algorithms (and a colleague on Deep Learning) for frequency and fuzzy attacks.

`Numbers` : The detection rate for the DoS averaged around 82 percent and Alien ID from 98-100 percent.
Deep Learning was the clear winner in AI category , between 82-98 percent efficiency.

`Challenge`: The initial idea was to deploy the probability based algorithm(low performance/memory) on an Micro Controller Unit (MCU) so that it can weed out the most common attacks like DoS for instance.
But since I found out there is no straightforward way to get the data I need (timestamp, ID) to the algorithm, because the MCU strips off these fields to only pass the payload or actual data packets.

`What's next?`: This PoC addressed the gaps the prototype did not and fared well in the target ECU.
However the attack data is simulated and I do not know how well it would perform in a live environment.
There could be instances of legitimate packets arriving a bit later than intended in a natural environment.
Real/live data often isn’t perfect and there are additional challenges that come with it , that an IDS should be able to handle.

**5.	CAN Security Framework (the thing that ties it all together)**

It consists of :
1.	`IDS Solutions/algorithms`.
2.	`Simulated attack data via CANoe` (can consider a short demo depending on time limit/availability of tool)
3.	`CAN testbed setup for live environment` (CAN wire harness, nodes, interface to read/send/receive CAN signals) - will provide details in presentation.
4.	`Software message injection toolbox` that generates attack packets (similar scenarios as PoC) especially for 3.
(It’s a preliminary design and would ideally be under development during the time of the conference).


I will present relevant information for each of these points in the framework, as necessary.


**6.
Key Takeaways**

Highlight some of the lessons learned , and why I think a hybrid based IDS would be the best bet (flow based combined with payload/data based).