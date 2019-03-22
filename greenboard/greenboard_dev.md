---
layout: page
title: GreenBoard Developer's Guide
permalink: /greenboard/developer/
---

# Overview
Thre GreenBoard program is a very early stage implementation of an ECU simulator. We hope that in the future this software could be used to help learn new commands or act as a sensor simulator.


# Contents
{: .no_toc}
1. TOC
{:toc}

# Testbench Use
To operate the test bench you will need to connect the CANable board and the jCOM ECU simulator board or the “GreenBoard”  to each other as shown in the following picture. Make sure the terminating jumper on the CANable board is set in the position facing away from the micro-usb port:
   
![Testbench Setup](/images/testbench.jpg)

Once you have the two boards connected you should be able to transmit and receive logs between then as if you were connected to a tractor. This is very useful for verifying that all software/hardware is working before trying to interact with the tractor. 

One tool that we have used when wanting to check proper operation of the CANable board is to use a different windows application for connecting with the GreenBoard. This is the windows application that is free to use by the manufacturer of the board and can be downloaded [here.](https://copperhilltech.com/jcom1939-monitor-sae-j1939-monitor-analyzer-and-ecu-simulator/)

This tool is useful because you can send specific packets right in the windows application without needing to modify a log file. Making for a great resource for quick testing!

Note: by default this application won't display any commands received, in order to see all command seen you will need to click on the “Filter” tab, and select “Pass All”, then “Save”. Then click on the radio button “Enable All” that is above the command log window. This should now should you all CAN traffic received by the board.

# Limitations Of GreenBoard
There are two main limitations with the GreenBoard, that it sometimes will get locked up during operation, and that it will drop some packets while it is receiving packets.
 
When the board gets locked up the 3 status green lights stay on and the application loses all communication with the board. The only solution to this we have found is to unplug the board, wait about 5 seconds then plug the board back in. This should reset the board back to an operational state.

Another limitation is that it drops more packets then the CANable board. After we got the CANable board to listen on the CAN bus we found that in the same amount of time we received many more commands. In about 10 seconds with the GreenBoard we would receive about 400 commands, however in the same amount of time we get about 700 commands. We can verified that the GreenBoard drops packs under a high transfer rate in our Testbench testing. As there is no way to know if a command is dropped we recommend using the CANable board whenever you are trying to capture packets from the tractor. Without an even faster board we are unable to confirm if the CANable board drops any packets.

# Advantages Of GreenBoard
The GreenBoard in comparison with the CANable board has its disadvantages, however it does have a distinct advantage. The GreenBoard has the CAN j1939 standard implemented natively on it, whereas the CANable board only has the CAN protocol. We had to develop the j1930 CAN protocol on the CANable board ourselfs. In order to verify our software we tested the CANable board with the GreenBoard in our testbench. This let us debug our software much faster then attempting to debug when connected to a live tractor. GreenBoard is also designed as an ECU simulator, which means it should be able to execute more advanced firmware than CANable.
