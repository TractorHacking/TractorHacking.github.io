---
layout: page
title: Benchtop ECU Internals
---

## Components

The following components on the ECU board were conclusively identified:

* MCU: ST10 16-bit Automotive MCU - [Info From Manufacturer](http://www.st.com/en/automotive-microcontrollers/st10-16-bit-automotive-mcus.html?querycriteria=productId=SC1886)
* RAM: Cypress CY62256 SRAM - [Datasheet](http://ecee.colorado.edu/~mcclurel/Cypress_SRAM_CY62256.pdf)
* CPLD: Xilinx XC9536 CPLD (or similar) - [Info From DigiKey](https://www.digikey.com/product-detail/en/xilinx-inc/XC9536-10VQ44I/XC9536-10VQ44I-ND/406927)

The board is conformaly coated and has its own onboard DC-DC converters for a power supply.

Connector ports on the box are Cinch 581-01-60-001.

## High-Res Photos

Click for original size.

[![ECU Processor and Memory](/images/ECU-Brain.jpg)](/images/ECU-Brain.jpg)

Pictured Above: Large IC on left is MCU, square central IC is Xilinx CPLD, identical packages along bottom are volatile memory.

[![ECU Top Down View](/images/ECU-TopDown.jpg)](/images/ECU-TopDown.jpg)

Pictured Above: Full top down view of the ECU.

[![ECU Connectors](/images/ECU-Connector.jpg)](/images/ECU-Connector.jpg)

Pictured Above: Cinch connectors plugged into the male Cinch port from outside the box.
