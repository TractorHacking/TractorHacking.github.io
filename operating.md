---
layout: page
title: Operating
permalink: /operating/
---
# How to operate the CANable board
Once you have all the needed libraries installed and running the candlelight firmware, connect the CANable board to your computer and run the bash script “bringUp” it is found in the following location: polycan/CANable/bringup. You will need to run this command from a terminal and give the script superuser privileges.  This can be done by typing the following command (this is assuming you are in the CANable directory): “sudo ./bringUp”

If everything is working correctly you should see the red and green lights on the CANable board go from on to off and remain off. If you don't see the lights change on the board or see a warning printed in the terminal, you will need to try and unplug the board and try the command again (the script should display a line reporting if it correctly created and can device, if there is a warning it will be clear). Once you see the lights correctly turn off, and no warning displayed in the terminal you should be good to go!