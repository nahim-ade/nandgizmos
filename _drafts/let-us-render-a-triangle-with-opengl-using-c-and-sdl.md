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

The vc_vars_cmd setting is required by the following plugin, but the vc_vars_arch setting is optional; if it is not given, it defaults to x86.

Next, select Tools > Developer > New Plugin from the menu and replace the stub plugin code with the following and save it in the default location that Sublime defaults to as something like set_vc_vars.py:


```
import sublime
import sublime_plugin

from threading import Thread
from subprocess import Popen, PIPE
from os import environ

SENTINEL="SUBL_VC_VARS"

def _get_vc_env():
    """
    Run the batch file specified in the vc_vars_cmd setting (with an
    optional architecture type) and return back a dictionary of the
    environment that the batch file sets up.

    Returns None if the preference is missing or the batch file fails.
    """
    settings = sublime.load_settings("Preferences.sublime-settings")
    vars_cmd = settings.get("vc_vars_cmd")
    vars_arch = settings.get("vc_vars_arch", "x86")

    if vars_cmd is None:
        print("set_vc_vars: Cannot set Visual Studio Environment")
        print("set_vc_vars: Add 'vc_vars_cmd' setting to settings and restart")
        return None

    try:
        # Run the batch, outputting a sentinel value so we can separate out
        # any error messages the batch might generate.
        shell_cmd = "\"{0}\" {1} && echo {2} && set".format(vars_cmd, vars_arch, SENTINEL)

        output = Popen(shell_cmd, stdout=PIPE, shell=True).stdout.read()

        lines = [line.strip() for line in output.decode("utf-8").splitlines()]
        env_lines = lines[lines.index(SENTINEL) + 1:]
    except:
        return None

    # Convert from var=value to dictionary key/value pairs. We upper case the
    # keys, since Python does that to the mapping it stores in environ.
    env = {}
    for env_var in env_lines:
        parts = env_var.split("=", maxsplit=1)
        env[parts[0].upper()] = parts[1]

    return env

def install_vc_env():
    """
    Try to collect the appropriate Visual Studio environment variables and
    set them into the current environment.
    """
    vc_env = _get_vc_env()
    if vc_env is None:
        print("set_vc_vars: Unable to fetch the Visual Studio Environment")
        return sublime.status_message("Error fetching VS Environment")

    # Add newly set environment variables
    for key in vc_env.keys():
        if key not in environ:
            environ[key] = vc_env[key]

    # Update existing variables whose values changed.
    for key in environ:
        if key in vc_env and environ[key] != vc_env[key]:
            environ[key] = vc_env[key]

    # Set a sentinel variable so we know not to try setting up the path again.
    environ[SENTINEL] = "BOOTSTRAPPED"
    sublime.status_message("VS Environment enabled")

def plugin_loaded():
    if sublime.platform() != "windows":
        return sublime.status_message("VS is not supported on this platform")

    # To reload the environment if it changes, restart Sublime.
    if SENTINEL in environ:
        return sublime.status_message("VS Environment already enabled")

    # Update in the background so we don't block the UI
    Thread(target=install_vc_env).start()
```

Once you save the plugin, Sublime will load it and execute the plugin_loaded function, which will do all of the work.You should see the status bar say VS Environment Enabled if it worked.

If you see Error Fetching VS Environment double check that the path to the batch file is correct (note that you need to double all path separators to make them JSON compliant).

The general idea is that the batch file is executed in a sub-process, and then before returning we also execute the set command to get the command interpreter to dump its entire environment to the console, which the plugin captures.

Once we have that data, we can easily compare it with the current environment to add in any environment variables that the batch file set up but which didn't already exist, and update the values of any environment variables that were changed (e.g. the PATH).

As a part of this process we also set a new environment variable that tells the plugin that the environment has already been set up, so that if the plugin gets reloaded it doesn't try to run the operation again.

As such, if you need to change the path to the batch file or the architecture that you want to be set up for, you need to change the preference and restart Sublime.

This could be made more robust by having it do something like store the current environment before modifying it and then watching the preferences to see if that setting is changed and act accordingly, but presumably it's not often that you would need to modify these settings.

I also created the following sublime-build file

```
{
    "shell_cmd": "cl \"${file}\" /Fe\"${file_base_name}\"",
    "working_dir": "${file_path}",
    "selector": "source.c, source.c++",

    "variants":
    [
        {
            "name": "Run",
            "shell_cmd": "cd bin && app.exe"
        },

        {
            "name": "Build",
            "shell_cmd": "nmake"
        }
    ]
}
```

Next, create a new file, name it "Makefile" and save it in the root of your project. Now we should have the following file structure for our project.




Copy the following contents into you newly created Makefile:

```
INCLUDES=deps/include
LIBS_DIR=deps/lib

LIBS=opengl32.lib glu32.lib SDL2main.lib SDL2.lib glew32.lib

# Specify compiler
CC=cl.exe

# Specify linker
LINK=link.exe

# Build all target
all : app

# Compile and Link the object files and dependent libraries into a binary
app : objs/*obj
	$(LINK)  -out:bin/app.exe -LIBPATH:$(LIBS_DIR) objs/*obj $(LIBS)

# Compile the source files into object files
objs/*obj : src/*.cpp
	$(CC) -D "WIN32" /Fo"objs/" -c -EHsc src/*.cpp -I $(INCLUDES)
```

The Makefile above will compile our source files and link the object files and dependent libraries into an exe to the bin folder. Since we are using MSVC we will be using nmake to build. If you would like to know about Makefiles you can read up on the internet. I will write about it in the future.

In the next part, we will be writing the main C++ source codes to render our Triangle.