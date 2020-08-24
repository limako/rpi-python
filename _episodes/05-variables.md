---
title: "Variable in Python"
teaching: 30
exercises: 10
questions:
- "How to store and manipulate data symbolically?"
objectives:
- "Assign values to variable"
- "Convert data from one type to another"
keypoints:
- "Python is strongly, dynamically typed"
---
In our last Flow Control examples, we snuck a variable (x) into the code. Any word, that isn't a reserved word (i.e. the name of some python command) can be defined as a variable.

By convention, python recommends using lower case words for variable names with underscores if necessary to aid reability.

Let's add another variable "place". You can assign a value to a variable using an equals sign.
~~~
#! /usr/bin/env python3

times = 4
try:
  for x in range(0,times):
    if (x < (times -1)):
      print("Hello world!")
    else:
      print("Goodbye world!")
except:
  print("Done!")
~~~
{: .language-python}

Now let's add another variable "place", this time we need to put the value in quotes.

~~~
#! /usr/bin/env python3

times = 4
place = "world"
try:
  for x in range(0,times):
    if (x < (times - 1)):
      print("Hello " + place + "!")
    else:
      print("Goodbye " + place + "!")
except:
  print("Done!")
~~~
{: .language-python}

Python will determine when a value is placed in a variable what type the variable is. We can inspect the type of a variable using the "type" command.

~~~
#! /usr/bin/env python3

times = 4
place = "world"
try:
  for x in range(0,times):
    if (x < (times - 1)):
      print("Hello " + place + "!")
    else:
      print("Goodbye " + place + "!")
except:
  print("Done!")

print(type(times))
print(type(place))
~~~
{: .language-python}

In our examples, "times" is an integer (non-decimal numbers) and "place" is a string (a sequence of alphanumeric characters).

The other most common data type you're likely to encounter is "float" which can be used for most simple decimals.

~~~
#! /usr/bin/env python3

times = 4
place = "world"
try:
  for x in range(0,times):
    progress = x / (times - 1)
    if (x < (times - 1)):
      print("Hello " + place + "!")
    else:
      print("Goodbye " + place + "!")
except:
  print("Done!")

print(type(times))
print(type(place))
print(type(progress))
~~~
{: .language-python}

> ## Question
>
> What is the value of "progress" at the end? What is the type? Can you explain why?
{: .challenge}


A primary consideration is trying to compare variables of different types. Consider the following script:

~~~
#! /usr/bin/env python3

i = int(1)
f = float(1)
s = str("1")

if (i == f):
    print("int equals float")

if (i == s):
    print("int equals string")

if (f == s):
    print("float equals string")

if (f == float(s)):
    print("float equals float(string)")

~~~
{: .language-python}

> ## Question
>
> Which tests return TRUE? What happens if you use different values for i, f, and s?
{: .challenge}


Variables themselves can evaluate to TRUE under certain circumstances.

~~~
#! /usr/bin/env python3

i = int(1)
f = float(1)
s = str("1")

if (i):
  print("int is TRUE")

if (f):
  print("float is TRUE")

if (s):
  print("string is TRUE")

if (u):
  print("undefined is TRUE")

~~~
{: .language-python}

> ## Question
>
> Which variables evaluate to TRUE? Under what circumstances?
{: .challenge}

There many other data types with more esoteric uses -- there is, for example, a BOOL data type that can only be TRUE or FALSE. And types for complex numbers. For most simple projects, however, these types are not needed.

{% include links.md %}
