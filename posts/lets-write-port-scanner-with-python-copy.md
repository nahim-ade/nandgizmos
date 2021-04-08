---
layout: post
title: Let's write Port Scanner with Python
subtitle:
date: 2021-04-05 00:08:45
background: /images/portscanner
---
**What is a Port Scanner?**

A port scanner is a utility/tool that is used to check network ports that are open. It does so by sending client requests to a range of server port addresses on a host, with the goal of finding an active port. They are valuable tools in diagnosing computer networks. Hackers often use port scanners to detect possible access points for infiltration and to test the strength of a network security and identify what kinds of devices you are running on the network(**reconnaissance** and **fingerprinting**). Although, port scanning is not a nefarious process in and of itself. The majority of uses of a port scan are not attacks, but rather simple probes to determine services available on a remote machine.

**What is a Port?**

Computer ports are like docking points for the flow of data from one device to another in a network. It is simply a logical construct that identifies a specific process or a type of network service. Port numbers are used for consistency and programming. The port number combined with an IP address form the vital information kept by every ISP in order to fulfill requests. Port numbers range from 0 - 65,536. Ports 0 -1023 are designed for internet use although they can have specialized purposes as well. 1024 - 49151 are considered "registered ports" meaning they are registered by software corporations. 49152 - 65536 are dynamic and private ports and can be used by nearly everyone.

The general protocols used in port scanning are TCP(Transmission Control Protocol) and UDP(User Datagram Protocol). They are both transmission methods used in the internet but have different mechanisms.

In this article, we will write a boilerplate TCP Port Scanner using Python programming language. There are several port scanning tools out there of which **NMAP&nbsp;**is the most popular and it should be noted that the one we will be writing here is just a boilerplate program to illustrate the working process and is nothing more than a programming exercise. As a hacker/administrator it is often recommended to use preexisting tools like nmap so as not to go through the stress of writing and debugging, wasting precious time resulting in a program which may not even be as efficient as required. But if you feel you can write one which will trump well established libraries, then why not :)

If the reader is not familiar with python or programming in general, it is advised to go read up as this is not a programming tutorial nor a python lesson.

**Let's get started\!**

First of all, the libraries we will be using for this excercise are **socket** and **IPy**. Socket class will be used to connect to the port while IPy will be used to parse IP addresses. You may have to ```pip-install``` the IPy library.

Lets get started:

```
import socket
from IPy import IP


try:
    # Initialise socket class
    sock = socket.socket()

    # Set time limit per port scan to 0.5 seconds
    sock.settimeout(0.5)

    # Connect to the specified IP address on the specified port
    for port in range(100):
        sock.connect((12.0.0.1, port))
    
        print('PORT ' + str(port) + ' - OPEN \n' )
except:
    pass

```


We start by creating an instance of a socket class(required for TCP/IP connections). We then try to connect to address 12.0.0.1(Use an IP address that you have permission to mess with!) on ports 1 - 100. If the connection is successful we print out the port number signifying it is open. the ```sock.settimeout(0.5)``` line limits the time to scan each port to 0.5 seconds to make the whole process faster. Without the time out the scan will take a very long time but with very efficient result. Although 0.5 seconds is just enough.

You can get really creative and flexible with your own port scanner. This program can be used as a starter to create your own. You can make it a library by encapsulating the whole thing in a class and modularise each task to make the program even more neat. You should allow user to enter the IP address manually then use the IPy lib to parse it into a readable form. You can add a few things like a banner for instance that will display information about the protocol on each port. You can even allow user to enter multiple IP/website addresses, separated with a comma for instance and use the ```split()``` method, then scan each of them. Also be flexible with the port numbers you scan, for instance you can allow user enter how many ports to scan.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

### Disclaimer

This program is intended for individuals to test their own equipment for weak security, and the author will take no responsibility if it is put to any other use
