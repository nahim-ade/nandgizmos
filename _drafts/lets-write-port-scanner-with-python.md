---
layout: post
title: Let's write Port Scanner with Python
subtitle:
date: 2021-04-04 23:38:22
background: /images/portscanner
---
**What is a Port Scanner?**

A port scanner is a utility/tool that is used to check network ports that are open. They are valuable tools in diagnosing computer networks. Hackers often use port scanners to detect possible access points for infiltration and to test the strength of a network security and identify what kinds of devices you are running on the network(**reconnaissance** and **fingerprinting**).

**What is a Port?**

Computer ports are like docking points for the flow of data from one device to another in a network. It is simply a logical construct that identifies a specific process or a type of network service. Port numbers are used for consistency and programming. The port number combined with an IP address form the vital information kept by every ISP in order to fulfill requests. Port numbers range from 0 - 65,536. Ports 0 -1023 are designed for internet use although they can have specialized purposes as well. 1024 - 49151 are considered "registered ports" meaning they are registered by software corporations. 49152 - 65536 are dynamic and private ports and can be used by nearly everyone.

The general protocols used in port scanning are TCP(Transmission Control Protocol) and UDP(User Datagram Protocol). They are both transmission methods used in the internet but have different mechanisms.

In this article, we will write a boilerplate TCP Port Scanner using Python programming language. There are several port scanning tools out there of which **NMAP&nbsp;**is the most popular and it should be noted that the one we will be writing here is just a boilerplate program to illustrate the working process and and is nothing more than a programming exercise. As a hacker/administrator it is often recommended to use preexisting tools like nmap so as not to go through the stress of writing and debugging some code, thereby wasting precious time resulting in a

&nbsp;

A&nbsp;**port scan**&nbsp;or&nbsp;**portscan**&nbsp;is a process that sends client requests to a range of server port addresses on a host, with the goal of finding an active port; this is not a nefarious process in and of itself. The majority of uses of a port scan are not attacks, but rather simple probes to determine services available on a remote machine.
