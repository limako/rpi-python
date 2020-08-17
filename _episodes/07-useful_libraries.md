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

## sys

The (sys library)[https://docs.python.org/3/library/sys.html] provides functions that support creating a unix utility. Many of its utilities are about the script being able to determine what kind of platform its being run on or the configuration of the system. These are mostly beyond the scope of what we're likely to do. But there are a few functions that can help you take advantage of the unix shell.

The first is to accept arguments when you start the program. Create a script called "systest.py"

~~~
#! /usr/bin/env python3
import sys
if(len(sys.argv) == 2):
    print(f'The argument was {sys.argv[1]}.')
    print(f'The name of the script was {sys.argv[0]}.')
else:
    print("Usage: systest.py [argument]")
~~~
{: .language-python}

The sys library populates the sys.argv variable with all of arguments that were on the command line that invoked the script. Note that the reference to the script includes any path elements that were referenced to execute the script. Sometimes people write a single program with multiple functions that can behave differently depending on how the program was invoked.

Note also that this example contains some basic error checking. If you're expecting an argument, you might not want to continue if the argument is absent. Typically, programs will emit a "Usage" statement that explains what the program is expecting.

There is another library, [argparse](https://docs.python.org/3/library/argparse.html), that provides more robust functions for command line arguments, including flags and switches, and hooks for easily adding help messages for each flag and argument. But for simple input, the sys library is often enough.

The sys library offers many more functions, including the ability to write not just to STDOUT, but also to STDERR.

> ## A Brief Digression:
>
>There are three important file descriptors in unix programming. A unix program run on the command line will typically print output to STDOUT that will show up in the terminal window. All of the print statements we've looked at print to STDOUT. Error messages should be directed to STDERR, which will typically also show up in the terminal window, although it can be directed elsewhere.  And if you direct information into a unix program, the program can receive it on STDIN.
{: .callout}

~~~
#! /usr/bin/env python3
import sys
if(len(sys.argv) == 2):
    print(f'The argument was {sys.argv[1]}.')
    print(f'The name of the script was {sys.argv[0]}.')
else:
    sys.stderr.write(f"Usage: systest.py [argument]\n")
~~~
{: .language-python}

If you run this program without an argument, you won't notice any difference. But if you redirect STDOUT somewhere else -- say, to a file

~~~
$ ./systest.py > output
~~~
{: .language-bash}

In this case, the Usage statement will not be redirected into the file, but will show up in the terminal window. Otherwise, the user would get no notification that the script wasn't working as expected.  

## pyserial

The [pyserial](https://github.com/pyserial/pyserial) library allows python to send and receive data via serial devices. This library is not one of the Python Standard Libraries and you may recall that we installed it in the first episode of this unit.

We're going to pull together everything we've learned in this lesson to build a script that can receive data from an arduino program. In the [rpi-arduino serial episode](https://limako.github.io/rpi-arduino/06-serial/index.html) we created a sketch that transmitted pairs of numbers recorded from a potentiometer via the serial connection. If you run this program while an arduino is connected and emitting values, you should see those values printed, prefaced by the timestamp we learned to create above.

Note that this script will keep running until killed with <kbd>Ctrl-C</kbd>, but note that we catch the interrupt and graceful close the serial connection before stopping.

~~~
#! /usr/bin/env python3

import serial,time
ser = serial.Serial('/dev/ttyACM0', baudrate = 9600) # open the connection
try:
  while 1:
    if(ser.in_waiting >0): # check for a line to be read
      line = ser.readline() # read the line from the serial connection
      line = line.decode('utf-8') # convert to UTF-8 encoding
      line = line.rstrip()
      timestamp = time.strftime("%Y-%m-%d %H:%M:%S", time.localtime())
      #print(line)
      print(f'"{timestamp}",{line}') #enclose timestamp (a string) in quotes
except:
  ser.close() # close the serial connection
  print("done.")
~~~
{: .language-python}

> ## Try this
>
> In the Arduino unit, we wrote sketches that also received data via the serial interface. Can you extend this python script to have it send data to the Arduino to modify the behavior of the sketch?
{: .challenge}

{% include links.md %}
