---
title: "Hello World"
teaching: 0
exercises: 0
questions:
- "How do I create and run a script in python?"
objectives:
- "Setup and run a script in python"
keypoints:
- "Create a text file"
- "Use a shebang to reference the executable"
---

The first program anyone writes in a new language is typically "hello world." This episode should be mostly a review of things you've already learned in the lessons about the bash shell and the Arduino.

Using the bash shell and a text editor, you can create a text file that will contain the python script. The convention for python scripts is that they will have the extension ".py" so let's create a file called "hello.py".

~~~
#! /usr/bin/env python3
print("Hello world!")
~~~
{: .language-python}

The first line of a script includes <kbd>#!</kbd> (called a "shebang") which is treated as a comment by python, but tells the bash shell to execute the referenced program and pass the contents of the file into the program.

In many scripts, you'll see a reference to the program directly. You'll recall we used "which" to see which version(s) of python the shell was going to use. This, instead, asks the "env" program to use the version of python our environment calls for. This should do the right thing and use the virtual environment we created.

You will need to make your file executable before you can run it.

~~~
$ chmod a+x hello.py
~~~
{: .language-bash}

> ## Try This
>
> Use "ls" to inspect the permissions of your file to ensure the execute bit is set correctly.
{: .challenge}

Since you're working on a file that is not on your PATH, the shell can only find your file if you point to it directly. The easiest way is putting a dot-slash in front of the file name.
~~~
$ ./hello.py
Hello world!
~~~
{: .language-bash}

> ## Try This
>
> Can you think of another way to point at your file? Try executing it using a different path.
{: .challenge}

{% include links.md %}
