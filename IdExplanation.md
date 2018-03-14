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

Foremost, the bit numbers being used are under the "CAN 29 BIT ID POSITION" 
label.
A breakdown of each field is as follows:

* Priority (28-26)- establishes the arbitration priority, highest priority
  being 0 and lowest is seven
* EDP (25) - Extended Data Page: combined with DP to identify different 
  message definitions
* DP (24) - Data Page: combined with EDP to identify different message 
  definitions
* PDU Format (23-16) - helps to define the parameter group the message
  belongs in. Distinguishes what type of data is being sent
* PDU Specific (15-8) - the address of the message's destination device
* Source Address (7-0) - the address of the message's source device

The parameter group number (PGN) is an identifier that differentiates between
types of messages. The messages that share the same PGN are related to each
other in some way. The PGN is made up of the PDU Format and PDU Specific 
concatenated together and converted to decimal. A lookup table of PGNs and 
SPNs is available as J1939AD from the SAE, another lookup table of ISO CAN Bus
standard items can be forund on [isobus.net](https://www.isobus.net).

All basic SAE standard information about ID format can be found through the 
[Serial Control and Communications Heavy Duty Vehicle Network - Top
Level Document](https://saemobilus.sae.org/content/j1939_201308)
