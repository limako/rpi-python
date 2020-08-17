---
title: "Installation and Setup"
teaching: 0
exercises: 0
questions:
- "Is python installed?"
- "Where is python installed?"
- "Which python should I use?"
- "How should I manage python versions and libraries?"
objectives:
- ""
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

Create a directory in your home directory for our work.

~~~
$ mkdir rpi-python
$ cd rpi-python
~~~
{: .language-bash}

You can check to see to whether python is installed using which:

~~~
$ which python
/usr/bin/python
$ which python2
/usr/bin/python2
$ which python3
/usr/bin/python3
~~~
{: .language-bash}

Raspbian Buster Lite comes with both python 2 and python 3 pre-installed. Currently, "python" is a symlink to python 2, but this is likely to change.

As was indicated in the introduction, python 3 is the current, stable version of python and new projects should almost certainly be written to use it, if possible. However, there is a large base of existing code and libraries written for python 2 and, if these resources are valuable, it might be worth using python 2 instead.

If python is not installed, you can install it using apt, e.g.

~~~
sudo apt install python3
~~~
{: .language-bash}

But this should not be necessary. Note that these commands need to be run as root to modify the installed system.

As you work with python, you may discover that for one project, you need to use incompatible versions of python or python libraries. Python addresses this problem by allowing you to create a virtual environment (venv) that maintains a version of python and its libraries separate from the overall system, to provide more stability and to prevent changes made to support one project from stepping on resources required for another.

You may need to install venv.

~~~
sudo apt install python3-venv
~~~
{: .language-bash}

This will allow you to create a virtual python environment in this directory and then activate it.

~~~
$ python3 -m venv .venv
$ source .venv/bin/activate
~~~
{: .language-bash}

Once you've done this, your command line prompt will be prefaced with a reference to your virtual environment.  

> ## Try This
>
> Use "which" to see which python3 will be used for execution now.
{: .challenge}

If you want to get out your virtual environment, you can run "deactivate." Or log out.

Note that these commands are *not* prefaced with sudo, since this is creating a virtual environment that is owned by user. This also allows the user to manage this environment without affecting the rest of the system.

Similarly, to install libraries, the python package installer pip3 (or just pip for python2), should be run as the ordinary user and not via sudo. And it installs the library in our virtual environment, so it won't affect or interact with other projects we're trying to use.

A library we're likely to need is the serial library, so let's install it now.

~~~
$ pip3 install pyserial
~~~
{: .language-bash}

We'll talk more about using libraries in the last episode of this lesson.

Consult python documentation for [more information about virtual environments and pip](https://docs.python.org/3/tutorial/venv.html).

{% include links.md %}
