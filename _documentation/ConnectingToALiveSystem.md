---
layout: page
title: Connecting to a Live System
---

# Model Information
The tractor we connected to was a John Deere model 5055E. We found a CAN-BUS port to the bottom right from the driver's point of view - a picture of it is below.

![IMAGE](/images/can_port_5055e.jpg)

# Scanning Session 1
For the first session, we used a Sigilent 1202XE to connect to the two CAN pins that corresponded to the Tractor's bus. After fiddling around with the scope's settings for a bit, we got a readable signal off of a 250 kilobit scan rate - failing to match this got us garbage data. However, while our scope was able to read the signals moment-to-moment, we were not able to save this in its entirety for later processing - we took a few photos of the screen's readout, but this was only a droplet of the data that passed through the scope. Attempting to save the capture resulted in merely 1.4 seconds of data being stored in a massive .25 GB csv file, all of which were momentary voltage readings, and it took several minutes to complete.
