---
layout: post
title: Let Us Render a Triangle With OpenGL Using C++ and SDL
subtitle: Part 2 - Automating the Build Process
date: 2021-04-10 09:10:25
background: /images/createGames/game_dev.jpg
---
In the last tutorial we set up our development environment for creating our "Hello world" game with SDL and OpenGL using C++ programming language.

Normally the linker and compiler are usually enabled by running a particular batch file (usually&nbsp;**"vsvarsall.bat"**) somewhere in the installation directory of MSVC.

&nbsp;

Since we are using Sublime Text and not an IDE we are going to have to write a plugin to have Sublime internally fire up the batch file once at Sublime start up to do what you need to do(permanently enable the MSVC toolset) otherwise each time we want to compile with MSVC we will have to re-enable the compiler and linker.

To start with, add the following settings to your user preferences (Preferences &gt; Settings or Preferences &gt; Settings - User). Here I'm using the setup for my own local machine; update the path to suit for your version of Visual Studio:

```
"vc_vars_arch": "x86",
"vc_vars_cmd": "C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\Community\\VC\\Auxiliary\\Build\\vcvarsall.bat"
```