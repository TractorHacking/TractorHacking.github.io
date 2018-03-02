---
layout: page
title: Future Reverse Engineering Work
---

## JTAG attack on the ECU

Upon investigation of the ECU board it was noted that there may be
JTAG or similar debug pins exposed that have been previously accessed,
likely during the remanufacturing process.  These are pictured below:

![ECU main board with pads circled](/images/ECU-Brain-JTAG-Highlight.jpg)

## Injecting debug commands into the CAN network
The J1939 spec specifies a number of debugging commands that can be injected
into the CAN network to receive back certain information.  It is likely that
this is possible using no more specialized equipment than our SparkFun RedBoard and
CAN-BUS shield.  However this avenue has not yet been investigated.

## Intercepting and filtering CAN packets
If it is determined that certain packets are being used to filter system messages
the lack of integrity checks or encryption (similar to unencrypted UDP) on the
CAN network would allow a physical device to be placed in between a control unit, like
the ECU and the rest of the network to intercept and filter packets that cause
the vendor lockdown.
