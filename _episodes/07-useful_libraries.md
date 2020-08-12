---
title: "Useful Libraries"
teaching: 0
exercises: 0
questions:
- "What else can python do?"
objectives:
- "Use libraries to extend python's functionality."
- "Use libraries to extend python's functionality."
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

Python is designed so that the core functionality is limited. This makes the language smaller and able to launch and run more quickly with a lower memory footprint. Much of the higher level functionality is available through a giant set of "libraries" that offer additional functions that can be imported at runtime.

The (Python Standard Libraries)[https://docs.python.org/3/library/index.html] are part of python itself. These libraries will be available for use (i.e. "import") without additional installation. There are also public repositories, like the (Python Package Index)[https://pypi.org/] that include a universe of additional libaries to draw from. These libraries probably need to installed and managed (via pip) to be available.

To use the functions in a library, it needs to be included by means of an "import" statement.

## time

The (time library)[https://docs.python.org/3/library/time.html] has an array of functions for accessing and using system information related to measuring time. Unlike an Arduino, a Raspbery Pi has a real-time clock that will use the network (if available) to maintain an extremely accurate current time value. But there are also functions that allow access to other kinds of time values or to measure the elapsed time between two points. The most basic use might be to access the local time and then emit a string formatted as a time stamp every five seconds.

~~~
#! /usr/bin/env python3
import time
while True:
  timestamp = time.strftime("%Y-%m-%d %H:%M:%S", time.localtime())
  print(timestamp)
  time.sleep(5)
~~~
{: .language-python}

sys

The (sys library)[https://docs.python.org/3/library/sys.html] has

> ## A Brief Digression:
>
> A unix program run on the command line will print output to STDOUT that will show up in the terminal window. Error messages are directed to STDERR, which will typically also show up in the terminal window.  
{: .callout}

import sys
sys.stderr.write()

if(len(sys.argv) <> 2):
    print "Usage: marmoset_receive.py [filename]"

    file = open(sys.argv[1],"a",buffering=0)


logging

{% include links.md %}
