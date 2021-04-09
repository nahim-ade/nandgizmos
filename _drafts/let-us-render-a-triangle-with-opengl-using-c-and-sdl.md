---
layout: post
title: Let Us Render a Triangle With OpenGL using C++ and SDL
subtitle: Part 1 - Setting Up Environment
date: 2021-04-09 00:59:46
background: /images/GameProg/pc_game.png
---
In this article, we are going to code a game entirely from scratch using **C++** without using any game engines or frameworks. We'll be using **SDL** to create our window and use **OpenGL** to render(draw) stuff on screen.

We are not going to be using any IDE like Visual Studio and CodeBlocks, instead we will use just a text editor which is Sublime Text 3 :). Note that I am only doing this due to preference and you can go ahead and use any coding tool of choice; use and IDE if you wish or use any Text Editor that your majesty desires. The goal of this writing is to make you understand the process of building games from scratch.

Although, a triangle on a screen may not be regarded as a game in a real sense, but let's just say it is the "Hello World\!" of Games Programming :).

For the purpose of this tutorial, we will be using the **Microsoft C++ (MSVC) compiler** and **Sublime Text 3&nbsp;**only. MSVC can be downloaded [here](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019){: target="_blank" rel="noopener"}(be sure to downoload only **Build Tools for Visual Studio 2019**). Download Sublime Text&nbsp;[here](https://www.sublimetext.com/).

First of all create a directory for your game project and name it as you wish(I called mine "01\_Triangle"). Open the folder in Sublime and create a file structure as thus:

![](/uploads/filestructure.png){: width="190" height="208"}

Go to the&nbsp;[SDL2 download page](https://www.libsdl.org/download-2.0.php)&nbsp;and download the latest Development Library for Windows:&nbsp;[SDL2-devel-2.0.14-VC.zip](https://www.libsdl.org/release/SDL2-devel-2.0.14-VC.zip)&nbsp;(Visual C++ 32/64-bit). Extract the zip file you downloaded

This folder contains the include- and library files needed for compiling, as well as the&nbsp;***SDL2.dll***&nbsp;file that we need to distribute along with the final compiled .exe file. Copy all **".lib"** files from **lib &gt; x86**&nbsp;directory into&nbsp;**deps &gt; lib&nbsp;**in your project directory. Copy the **SDL2.dll** file from **lib &gt; x86**&nbsp;directory into **bin**&nbsp;folder in your project directory. Copy all files from **include**&nbsp;folder into&nbsp;**deps &gt; include &gt; SDL2 folder&nbsp;**in your project directory

Go to GLEW main page and download Windows binaries. Current link is&nbsp;[this](http://glew.sourceforge.net/)&nbsp;for now. Extract the zip file. Copy&nbsp;
