---
layout: page
title: Technical Notes J1939
---

John Deere equipment conforms to a CAN protocol set by the Society of Automotive
Engineers (SAE) named J1939. This is a standard that specifies the contents of the CAN
message’s ID, as well as what type of data is sent under specific ID numbers.

Useful Terminology:
* Parameter Group Number (PGN) - Each message falls into a group based on where the message is coming from, and
what type of data it contains. J1939 protocol organizes similar messages into groups. SAE has requirements for what 
data specific PGNs should carry. Taking advantage of this fact was the main method of attack to identify messages sent.
The PGN falls into two formats, both two bytes in length. 
	* PDU1 - The PGN's MSB is the PF field, and its LSB is 00.
	* PDU2 - The PGN's MSB is the PF field, and its LSB is the PS field.
* Protocol Data Unit (PDU) - Term for the fields that make up the PGN, plus the data being sent.

The J1393 protocol mandates a specific format for the message identifier sent with each data packet. There are 
two formats of identifier, the standard 11-bit, and the extended 29-bit. The John Deere tractors we have researched
so far use the 29-bit extended format. An image breaking down the id is shown below.
![J1939 CAN bits breakdown, reproduced from the J1939 standards specification](/images/idmap.png)

The identifier contains multiple parts that are important to the message.
* DP/EDP - Data Page/Extended Data Page, used to specify the page the specified PGN lies on
* PDU Format (PF) - Makes up the most significant byte of the PGN, plus acts as a specifier for the format of the PGN. 
If the PF is 0xF0 or greater, then the PGN falls in the PDU2 format. If it is less than 0xF0, it is the PDU1 format.
* PDU Specific (PS) - In PDU1 format, the PS acts as the destination address. Used if the message is meant for a specific controller only.
In PDU2 format, the PS is appended to the PF to form the complete PGN.
* Source Address - Specifies the controller the message originated from.
