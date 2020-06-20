---
title: "Introduction"
teaching: 0
exercises: 0
questions:
- "What is python?"
- "Why might I want to use python?"
objectives:
- "Understand what python is."
- "Understand why scientists use python."
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---
This is a brief introduction to python programming, focused on the Raspberry Pi and assuming you've done an arduino tutorial. It does not otherwise assume you know much, if anything, about programming. This guide will walk you through installing python and using it to write small programs that allow to you interface between the Raspberry Pi and other devices. A subsequent guide will focus on using Python to work with the General Purpose Input/Output (GPIO) -- the little pins that stick up along the edge of the Raspberry Pi board.

Scientists use Python for many programming tasks, chief among them these days are bioinformatics (working with sequence data), data analysis (analyzing large data sets), and figure construction. Our focus is different: mainly receiving information from one source and doing something with it: transforming it, saving it, etc.

Python is an interpreted programming language that has has become
very popular in scientific contexts. There is a huge library of python resources
that make it useful for many purposes. Just like with model organisms, what makes it useful is less any particular essential characteristic than the body of pre-existing work one can draw from to base your own work on going forward.

Python was created by Guido von Rossum beginning in the late 1980s. Since then, it's gone through three generations. The current version (3) is probably the one that new projects should be based on going forward, although many old projects and code still use version 2. And for a particular project, if a library of existing code would be useful, it might still be appropriate to use version 2.

In C and C-based languages (like bash and the arduino programming language), white space is generally meaningless. Loops, if-statements, and functions are delimited using curly braces <kbd>{}</kbd>.  In Python, however, the indentation (either tabs or spaces) determines the structure.

Python does not require you to declare variables. In arduino programming language, you need to specify what kind of data a variable contains. Python, on the other hand, will decide for you based on what the initial data looks like. Knowing this can help you debug problems if you find that operations in python yield surprising results.

Note that python is [extremely well documented](https://docs.python.org/3/) and there are [many tutorial](https://docs.python.org/3/tutorial). These lessons are designed to present a subset of python that will be most useful for the kinds of projects that interface with hardware.

{% include links.md %}
