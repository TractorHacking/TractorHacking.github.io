---
layout: page
title: User Manual
---

# Usage

This document serves as a quick start guide for those to pick up this work after we have finished ours. 

## Contents
{: .no_toc}
1. TOC
{:toc}

## Tractor Electronics Layout

#### Navigating the John Deere Manuals

## Connecting to a Tractor

Most automobiles have an OBD-II port, which is a standard rectangular connector and communication protocol that
allows users to tap into their car's communication. The simpler John Deere tractors do not have this port, but they
have something similar. It is a circular port that exposes the CAN high and low wires, as well as ground and a few
other signals that aren't needed for this project. Below are images of the connector on the John Deere 5055E tractor, 
and its associated pin diagram.

![CAN Connector on the John Deere 5055E](/images/can_port_5055e.jpg)
![Pinout of the CAN cable used to connect to the tractor](/images/can_connector_pinout.png)



## ECU Internals

## Finding SAE Documents

The Society of Automotive Engineers (SAE) sets standards for much of the electronic communication that goes on 
inside any automobile, and tractors are no exception. In this project, we have used SAE documentation to 
learn about automobile communications networks and to understand what the individual CAN messages mean. Unfortunately,
SAE documents are not free, and we were only able to gather them through Cal Poly's subscription to the SAE database. 
Because of this, we cannot freely post these to this website, because they are not public use. If you are a current
Cal Poly student, or have access to this database through other means, then you will be able to use the same 
resources we did. The documents that were of the most help to us are:
* Serial Control and Communications Heavy Duty Vehicle Network - Top Level Document
	* Briefly describes commonly used terms with CAN J1939 message format
	* Details how an ECU usually processes and validates incoming messages
* Vehicle Application Layer - J1939-71
	* Applying the J1939 standards directly to the vehicle on a low level
	* This won't be very useful when starting out, but if more progress is made this document would be useful 
	if one is trying to control specific tractor functions
* Digital Annex of Serial Control and Communication
	* The most used document, this is what is used to map specific PGN numbers to the attributes they carry
	* The document cannot be posted in its entirety, but an abridged version saved as a .csv is posted in the
	scripts repository [here](https://github.com/TractorHacking/Scripts/blob/master/markdown_gen/dict/PGN.csv)

If you are a current Cal Poly student, sign in to your Cal Poly Portal and follow this link to the 
SAE database: 

[SAE Database](https://saemobilus-sae-org.ezproxy.lib.calpoly.edu/search/)

## Using the Filtering Scripts

Initially, we decided to make a quick script to look through the files gathered from the tractor and look for
certain CAN IDs, especially ones that appear frequently. This script kept growing in functionality as more 
features were needed. This is going to be a useful piece of software: although there are existing programs that
already parse live CAN data (such as [python-OBD](http://python-obd.readthedocs.io/en/latest/), we needed one that 
would give us information about the data we saved. The final script and information about how to use it can be 
found on our pubic repository linked below.

[Tractor Hacking Scripts](https://github.com/TractorHacking/Scripts/tree/master/tractordata_parse)
