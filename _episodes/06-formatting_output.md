---
title: "Formatting Output"
teaching: 30
exercises: 10
questions:
- "How can python output data?"
- "How can the format of the output be controlled?"
objectives:
- "Use the two forms of formatting for strings"
keypoints:
- "Combining strings and variables can help structure output."
- "There's more than one way to do it."
---

There are several ways to format output in python. We'll skip the oldest, used in python 2, though you may still see it in older code.  

One generally formats strings (lines of alphanumeric characters). You might want to do this to emit messages -- especially for debugging -- or for output.

You can just add strings together.

Create a file called "format.py" with the following code and execute it.

~~~
#! /usr/bin/env python3
a = "hello"
b = "world"
line = a + b
print(line)
~~~
{: .language-python}

> ## Question
>
> Is something missing? How can you fix the output?
{: .challenge}

Sometimes the problem is not a lack of whitespace, but too much -- or line endings that make it difficult to make comparisons or format output correctly.

~~~
#! /usr/bin/env python3
a = "hello\n" # \n is a newline character
b = "world"
a = a.strip() # this removes white space from both ends
line = a + b
print(line)
~~~
{: .language-python}

There are also lstrip() and rstrip() functions. And you can provide a list of the characters you want removed if you want to be precise.

If you want to do more than just concatenate or assemble strings, you can use the format function. This uses placeholders in a string as a template and then inserts variables in order.

~~~
#! /usr/bin/env python3
a = "hello\n" # \n is a newline character
b = "world"
a = a.strip() # this removes white space from both ends
line = '{} to the whole {}.'.format(a,b)
print(line)
~~~
{: .language-python}

In fact, you most commonly see it simply embedded in the print function.

~~~
#! /usr/bin/env python3
a = "hello\n" # \n is a newline character
b = "world"
a = a.strip() # this removes white space from both ends
print('{} to the whole {}.'.format(a,b))
~~~
{: .language-python}

The newest style of formatting is called "f-strings". It's like format, but you can just declare the variables inside the curly braces.

~~~
#! /usr/bin/env python3
a = "hello\n" # \n is a newline character
b = "world"
a = a.strip() # this removes white space from both ends
print(f'{a} to the whole {b}.')
~~~
{: .language-python}

There are a vast array of other functions you can combine with format or f-strings.

Finally, we've been printing our output to the screen. But you might want to write the output to a file.

~~~
#! /usr/bin/env python3
a = "hello\n" # \n is a newline character
b = "world"
a = a.strip() # this removes white space from both ends
print(f'{a} to the whole {b}.')
file = open("output.txt","a")
file.write(f'{a} to the whole {b}.')
file.close()
~~~
{: .language-python}

If you inspect the contents of output.txt you'll see the same line was saved there.

> ## Question
>
> What happens if you run format.py again? How does the contents of output.txt change? Can you get the output to end up on separate lines?
{: .challenge}

In the file open function, we specified "a" (for append") as the mode to open the file in, which allows you to add to the existing file. If you use "w" you will overwrite the contents of the file each time you run the program.

{% include links.md %}
