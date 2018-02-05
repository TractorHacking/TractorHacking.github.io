---
layout: page
title: CAN ID Explanation
permalink: /IdExplanation/
---

The SAE J1939 protocol requires a specific format for the CAN message's 
identifer. The ID can consist of 11 bits, or optionally 29 bits in the 
extended format. According to the data gathered and John Deere documentation,
the extended 29 bit format is being used.


![SAE J1939 Identifier format](/images/idmap.png)
Figure 1: A breakdown of the SAE J1939 CAN idenfier format

Foremost, the bit numbers being used are under the "CAN 29 BIT ID POSITION" 
label.
A breakdown of each field is as follows:
<ul>
 <li>Priority (28-26)- establishes the arbitration priority, highest priority
 being 0 and lowest is seven</li>
 <li>EDP (25)- </li>
 <li>DP (24)- </li>
 <li>PDU Format (23-16)- helps to define the parameter group the message
 belongs in. Distinguishes what type of data is being sent</li>
 <li>PDU Specific (15-8)- the address of the message's destination device</li>
 <li>Source Address (7-0)- the address of the message's source device</li>
</ul>


