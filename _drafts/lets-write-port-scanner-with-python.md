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

In this article, we will write a boilerplate TCP Port Scanner using Python programming language. There are several port scanning tools out there of which **NMAP&nbsp;**is the most popular and it should be noted that the one we will be writing here is just a boilerplate program to illustrate the working process and is nothing more than a programming exercise. As a hacker/administrator it is often recommended to use preexisting tools like nmap so as not to go through the stress of writing and debugging, wasting precious time resulting in a program which may not even be as efficient as required.

If the reader is not familiar with python or programming in general, it is advised to go read up as this is not a programming tutorial nor a python lesson.

**Let's get started\!**

First of all, the libraries we will be using for this excercise are **socket** and **IPy**. Socket class will be used to connect to the port while IPy will be used to resolve parse IP addresses.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

### Disclaimer

This program is intended for individuals to test their own equipment for weak security, and the author will take no responsibility if it is put to any other use
