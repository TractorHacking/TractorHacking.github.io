---
layout: page
title: Install
permalink: /install/
---
# How to install PolyCAN 
PolyCAN runs on linux. If you do not have a linux machine, you can use a virtual machine by following this guide:
[Virtual Box for Windows](https://www.lifewire.com/run-ubuntu-within-windows-virtualbox-2202098)
Once you have booted in a linux environment, you should have python 3 installed. If you do not have python 3, download and install the latest version from this website:
[Python3](https://www.python.org/downloads/)
Once you have a linux environment with python 3, open terminal and run the following command:
	
	Kjsdflaksjflkdasdjlkfsdlkfajsldfjasdlkfskjdf

You should see the installation take place. Once it is finished, type ‘polycan’ to run the program. 


# How to install the CANable board
The CANable board works on linux. Before you can connect to the board verify that you have installed net-tools and socketcan. The easiest way to install socketcan is to install can-utils, which includes a nice toolset for interacting with the CAN bus. We have implemented many of the features available in can-utils like the ability to listen and playback logs. 

The firmware that comes installed onto the CANable board by default is not what we use. It comes with slcan firmware, however this is slower as this creates a virtual CAN device instead of a native CAN device. In order to put the different firmware onto the board follow CANable’s documentation on flashing candlelight firmware found here, under section “Alternative Firmware”: [CANable](https://canable.io/getting-started.html)

Everything is installed now to [operate](/operating/) the CANable board.


# How to install the GreenBoard
The J1939 ECU simulator board or we call it the ‘GreenBoard’ can be found here: [GreenBoard](https://copperhilltech.com/sae-j1939-ecu-simulator-board-with-usb-port/)
This board interacts with a windows application. The windows application can be found here:
Github for windows APPPPPPPPPPPPPPPPPPPPPPPPPPPPPPP

In order to connect with the board you first need to download the driver for it. The drive can be found here:
[GreenBpardDriver](https://copperhilltech.com/blog/connecting-the-jcomj1939usb-board-hardware/)
Once the driver is installed you should be able to run the windows application located at following location: 
polyCan_jCOM/polyCan_jCOM/bin/Release/polyCan_jCOM.exe

Everything is installed now to [operate](/operating/) the GreenBoard.

