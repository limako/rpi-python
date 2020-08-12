---
title: "Flow Control"
teaching: 0
exercises: 0
questions:
- "How can you affect the flow of execution in python?"
objectives:
- "while, try, for, if/then/else can direct the flow of execution"
keypoints:
- "Loops can be unconditional or conditional "
---

In arduino programming all of the operation was contained in two functions: one called "setup" that was called once, and one called "loop" that was called over and over again.

In python, commands don't need to be enclosed in functions: they simply get executed in order and the program will exit when it reaches the end.  You can replicate the functionality of the arduino "loop" function by using "while".

The while command takes a test as an argument and as long as that test evaluates as "true", the progam will execute the steps inside the while loop as rapidly as possible. The simplest test that will evaluate as "true" is to just say "True."

Before executing the next program, be ready to type a <kbd>Ctrl-C</kbd> to stop execution.

~~~
#! /usr/bin/env python3
while True:
  print("Hello world!")
~~~
{: .language-python}

In this example, the program will output forever until interrupted. A <kbd>Ctrl-C</kbd> will do it. But notice that this stops execution ungracefully, wherever the program was, it just stops with no cleanup.

If you use "try", you can catch errors or interrupts and clean up before exiting. This becomes more important if you're opening files, writing to disk, or using serial connections all of which you probably should shut down gracefully rather than leaving to chance.

~~~
#! /usr/bin/env python3
try:
  while True:
    print("Hello world!")
except:
  print("Done!")
~~~
{: .language-python}

In this example, you should be able to type <kbd>Ctrl-C</kbd> and see the statement "Done!" to show

This particular structure works like "loop" in Arduino -- that is, it just loops forever. But you can also look only while certain conditions are true. But if you only want to look for a certain number of times, you can use "for."

~~~
#! /usr/bin/env python3
try:
  for x in range(0,4):
    print("Hello world!")
except:
  print("Done!")
~~~
{: .language-python}

> ## Question
>
> What is the value of "x" during each iteration?
{: .challenge}

You can use "if" statements to test for conditions which can include "else" clauses for what to do in exceptions.

~~~
#! /usr/bin/env python3
try:
  for x in range(0,4):
    if (x <3):
      print("Hello world!")
    else:
      print("Goodbye world!")
except:
  print("Done!")
~~~
{: .language-python}

> ## Try this
>
> You can test the modulo as a condition determine whether a value divides evenly by a divisor, e.g. "x % 2 == 0" will only be true for even numbers.
{: .challenge}

This only scratches the surface for how you might direct flow control.

{% include links.md %}
