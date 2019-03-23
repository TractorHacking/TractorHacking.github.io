---
layout: page
title: About
permalink: /about/
---
<div style="float:right;"><a href="https://cpe.calpoly.edu/"><img src="/images/capstone.png" alt="CalPolyComputerEngineering" width="200"/></a></div>

# Our Mission
We are studying the CAN bus of John Deere tractors. If we can understand the communication protocol of the John Deere CAN bus messages, we could begin to learn important diagnostic codes through experimentation. We will be collecting large amounts data from tractors to uncover and interpret the proprietary communication commands. To aid in this pursuit, we have  designed a diagnostic tool, PolyCAN, that will assist us and future projects in gathering data. We have also begun early development on an ECU test bench with a simulated CAN network called GreenBoard.


# Technical Documentation
The first goal of this project was to get an idea of how the John Deere CAN bus works. We offer some technical documentation which details what we know about John Deere’s communication protocols. This documentation includes information about the CAN bus, the J1939 standard, connecting to a tractor, ECU internals, and common CAN bus commands. This was performed by the 2017-2018 iteration and is held under the 'Technical Documentation' tab. 

# PolyCAN
PolyCAN is a diagnostic tool that enables communication on the John Deere CAN bus. It allows anyone with a linux machine to record all messages on the CAN bus and analyze the payload of these messages. With PolyCAN, one can also send messages on the bus to communicate with the tractor computer systems. PolyCAN features a clear command line interface and features a variety of diagnostic tools. PolyCAN was developed by the 2018-2019 interation and is held under the 'PolyCAN' tab. 

[Getting started with PolyCAN](/polycan/) 

[PolyCAN Developer Guide](/polycan/developer/)


# GreenBoard
GreenBoard is the beginning of a tractor simulator program that lets us simulate a CAN network. When connected to a tractor ECU, this test bench could allow us to someday analyze the protocol more systematically and incorporate other methods of analysis and penetration testing that are so invasive that they cannot be performed on a working tractor. To use GreenBoard, click the 'GreenBoard' tab.

[Getting started with GreenBoard](/greenboard/)

[Greenboard Developer Guide](/greenboard/developer/)

# Posters
A poster explaining each iteration of the project for the Cal Poly Capstone Expo can be downloaded below:
   
   [2017-2018](/files/poster.pdf)

   [2018-2019](/files/poster1819.pdf) 


# Sponsors
<div style="float:right;"><a href="https://www.ifixit.com/"><img src="/images/ifixit.png" alt="iFixit" width="200"/></a></div>
iFixit provides a worldwide database of repair guides as well as high quality repair parts and tools. They have a history challenging over-restrictive policies that limit the customer's ability to repair their own products. Our project falls within this mission by doing research that will lead to documentation of diagnostic codes and the possibility of replacement parts for John Deere tractors.


# License

<a rel="license" href="https://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="/images/by.svg" /></a>

<a xmlns:cc="http://creativecommons.org/ns#" href="https://tractorhacking.github.io" property="cc:attributionName" rel="cc:attributionURL">https://tractorhacking.github.io</a> is licensed under a <a rel="license" href="https://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

Software developed for this project is released under the MIT License, see the software GitHub repositories for more license information. 
