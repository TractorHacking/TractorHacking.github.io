---
layout: page
title: Technical Notes J1939
---

John Deere equipment conforms to a CAN protocol set by the Society of Automotive
Engineers (SAE) named J1939. This is a standard that specifies the contents of the CAN
message’s ID, as well as what type of data is sent under specific ID numbers.

A bit by bit breakdown of a standard 29 bit  J1939 CAN message can be found below:
![J1939 CAN bits breakdown, reproduced from the J1939 standards specification](/images/idmap.png)

J1939 specifies what data is being sent at each location in the CAN data region. This
includes a description, the data size, and the byte offset in the data packet. This
information is incredibly helpful in decoding the data gathered from the tractor, because it
allowed us to look for specific IDs and observe the numbers changing at a specific point
in the packet.
