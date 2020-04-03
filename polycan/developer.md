---
layout: page
title: PolyCAN Developer's Guide
permalink: /polycan/developer/
---
# Overview
The PolyCan program integrates interaction with a CAN network via the CANable board. This board takes two wires CAN high and CAN low data lines and appears as a native linux CAN device. In order to setup the board to connect one needs to set the bitrate for the can device and to enable the device, both of these features is implemented in the bringUp bash script located in polyCan/CANable directory. If the operation is successful no warnings should be printed to the screen, and the CANable light should turn off. To disconnect the board there is a corresponding script putDown that will disconnect the device. Note both of these bash scripts need superuser privileges to operate correctly. 
The part of the software that deals with the CANable board transfers data through .csv files with the format of our log files. Then once the software finishes listening to the CAN network it passes the .csv file to other parts of the code to perform all of the log analysis.

<div style="margin:0auto;"><img src="/images/polycandeveloper.png" alt="polycanimplementation" width="700"/></div>
<div style="margin:0auto;"><img src="/images/uml-diagram.png" alt="polycanimplementation" width="700"/></div>

# Contents
{: .no_toc}
1. TOC
{:toc}

# How we find new unknown commands
One of our goals was to develop a method to be able to decode unknown commands we receive from the CANBus. This was achieved by the direct comparison of logs with only slightly different conditions. For testing polycan we worked with a John Deere 5055E tractor. John Deere provides on their website a list with diagnostic trouble codes which looks like the figure shows below:

![Trouble Code Example](/images/troublecodeexample.png)

As you can see in this example, there are a few ways to force the tractor to output a trouble code. To find the equivalent CANBus command for the trouble code shown in the figure, we put the tractor in gear while startup which causes the tractor to not start up and generation an error code. This log was compared with a log recorded while a normal engine start of the tractor. The idea to is to find a unique entry in those two logs. After the comparison on the two logs, there are a few unique entries which are in the log from the tractor in gear but not in the normal engine start log. A lot of there unique entries are parameters which change due to the running conditions, like engine temperature, oil pressure and engine rpm. By checking the unknown PGNs in the log, we found out that PGN 65226 stores the “Active Diagnostic Messages” and the Data code “01 FF F4 FE FF 00 FF FF” stores the diagnostic trouble code “PTI 523238.31”.

<div style="margin:0auto;"><img src="/images/twocomparedlogs.png" alt="comparelogs" width="700"/></div>


We were able to produce an other error code by sending a manipulated log back to the tractor. 
First we captured the CAN messages from the tractor running for 10 seconds and used after that the manipulate function on that log to increase the engine RPM to 3000 rpm. We sent this back to the not running tractor to simulate a too high engine RPM which threw out an alert and an error code. 


# Module Descriptions

### sql_interface.py
The sql interface module is responsible for accessing the sql database. It contains a class called  db and some functions that act upon the class. The class db contains username, password and connection fields. When the init_db(username, password) function is called, the database class is created using the given username and password and a connection is set up. 

In order to download logs from the database, get_log(name) is called which returns a Pandas dataframe containing the log with the name specified. If unsure which log name to send to this function, call get_lognames() which returns a list of the logs stored in the database. 

In order to upload logs to the database, upload_logs() is called, which uploads all the logs that are in the logs folder to the database. In order to get the database of known commands, get_known() is called which returns a python dictionary containing all of the known packet information including bitfields.

### file_interface.py
The file_inteface is responsible for PolyCAN’s interaction with the Linux filesystem. The function get_file_path(path) opens the directory specified by the path and opens a menu allowing the user to select a file within that directory. Once a file has been selected, the function returns the full path to the file.

To open a log stored in csv format, open_log() is called, which in turn calls get_file_path(path) to first select the path. It then opens the file and returns a Pandas dataframe containing the log. To store a captured log to a file, capture_log() is called, which gets a file name from the user and stores a captured log to the given path. 

To send a log while capturing response from the tractor, sendAndCapture_log() is called, which first gets a file name from the user to store the new log and then allows the user to select a log to send using get_file_path(path).

### packet.py
This module does all the interactions with the CANable board. It defines a Packet Class that stores all relevant fields of a j1939 command. The class Packet can be initialized 1 of 3 ways. First way is that it can take a single line from a .csv log file with the function Packet.initFromCSV(self,line). The next way a user can initialize a packet is with the byte string returned by Socket.recv(), this is done with the function Packet.initFromPkt(self,packet). Lastly, if there was capturing of CAN traffic with the can-utils utility candump the function Packet.initFromCanUtils(self,line) will extract from the can-utils log format all the important fields. Once the Packet object has been initialized the object can be used to turn the command into a .csv log file format or to a bytestring used to send the command via Socket.send(). There are two functions that are not apart of the class Packet that handle sending and receiving commands given a Socket. These functions are getNewPacket(socket) and sendPacket(packet,socket). The purpose of these functions is such that the user does not have to deal with the case of segmented packets. Segmented packets occur whenever there is more than 8 bytes of data sent, if so then the data is sent over several sequential packets. These functions handle any segmented packets and combies all the packets into one large packet abstracting this issue from the caller.

### canable.py
Interacts with the class Packet and creates the .csv log files. There are 3 functions in this file, get_csv(path), sendCSVWhileRead(pathR,pathW), and send_csv(path). The first function get_csv(path) takes the path to a .csv log file either overwrites or creates a new file at the given path with all of the commands the user record.The function  sendCSVWhileRead(pathR,pathW) does the same thing with the file given by pathW, as well as sending out the file specified by pathR. The function send_csv(path) only sends out of .csv log file and does not listen to any CAN traffic.

### log.py
Describes container class Pgn for a known PGN data packet. Pgn contains a list of PgnParameter objects that separate data fields of a packet.
Dictionary of known commands ‘known’ is populated with Pgn objects accessible by PGN in decimal (i.e. dictionary key 61444 yields PgnObject(pgn=61444, length=8, …, parameters = [PgnParameter, PgnParamteter, ...])

### log_viewer.py
LogViewer is responsible for storage and navigation between uploaded data logs. LogViewer provides an interface for all analysis tools - sorting, filtering, pattern matching.  LogDisplay is responsible for navigation within a data log. LogViewer contains one or more LogDisplays.  After a tool is applied, log is updated in LogDisplay and printed in terminal. To maintain menu hierarchy and allow switching between several active logs LogViewer contains several boolean state variables that represent which logs are being displayed, which log is active, which line is being analyzed.

### log_handler.py
“Muscles” of PolyCAN. Contains all log and data analysis tools that operate on logs entry by entry. Pandas and NumPy packages greatly simplify the analysis and provide a programming framework for log tools. Input and output of each “tool” is a Pandas dataframe with the standardized structure:

![Example Data Frame](/images/examplelogdataframe.png)

### menu.py
The menu.py module is responsible for displaying menus so that the user can select from a number of options. Menu.py uses the keyreader.py module to read escape codes from the terminal. The most basic menu function is launch_menu(options) which creates selection from one long list. This becomes cumbersome with larger lists. In order to separate the list into pages of 20, display_pages(log) can be used. 

### keyreader.py
This module was not written by us. It interacts with the operating system to read all codes from the terminal in an unbuffered manner, including escape codes. This is necessary for our interface to be responsive and to use specific keys like arrow keys.

