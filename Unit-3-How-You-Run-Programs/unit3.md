## Starting an Interactive Session

Perhaps the simplest way to run Python programs is to type them at Python’s interactive command line, sometimes called the interactive prompt. The most platformneutral way to start an interactive interpreter session is usually just to type python at your operating system’s prompt, without any arguments

```
% python
Python 3.3.0 (v3.3.0:bd8afb90ebf2, Sep 29 2012, 10:57:17) [MSC v.1600 64 bit ...
Type "help", "copyright", "credits" or "license" for more information.
>>> ^Z
```
Typing the word “python” at your system shell prompt like this begins an interactive
Python session; the “%” character at the start of this listing stands for a generic system
prompt in this book—it’s not input that you type yourself. On Windows, a Ctrl-Z gets
you out of this session; on Unix, try Ctrl-D instead.

The notion of a system shell prompt is generic, but exactly how you access it varies by
platform:

• On Windows, you can type python in a DOS console window—a program named cmd.exe and usually known as Command Prompt. 

• On Mac OS X, you can start a Python interactive interpreter by double-clicking on Applications→Utilities→Terminal, and then typing python in the window that opens up.

• On Linux (and other Unixes), you might type this command in a shell or terminal window (for instance, in an xterm or console running a shell such as ksh or csh).

• Other systems may use similar or platform-specific devices. On handheld devices, for example, you might click the Python icon in the home or application window
to launch an interactive session.

## The System Path
 
When we typed `python` in the last section to start an interactive session, we relied on the fact that the system located the Python program for us on its program search path. Depending on your Python version and platform, if you have not set your system’s
`PATH` environment variable to include Python’s install directory, you may need to replace the word “python” with the full path to the Python executable on your machine. On
Unix, Linux, and similar, something like `/usr/local/bin/`python or `/usr/bin/python3` will often suffice. On Windows, try typing `C:\Python33\python` (for version 3.3)

```
c:\code> c:\python33\python
Python 3.3.0 (v3.3.0:bd8afb90ebf2, Sep 29 2012, 10:57:17) [MSC v.1600 64 bit ...
Type "help", "copyright", "credits" or "license" for more information.
>>> ^Z
```
Alternatively, you can run a “cd” change-directory command to go to Python’s install
directory before typing python—try the `cd c:\python33` command on Windows, for example:
```
c:\code> cd c:\python33
c:\Python33> python
Python 3.3.0 (v3.3.0:bd8afb90ebf2, Sep 29 2012, 10:57:17) [MSC v.1600 64 bit ...
Type "help", "copyright", "credits" or "license" for more information.
>>> ^Z
```

## New Windows Options in 3.x: PATH, Launcher

More dramatically, Python 3.3 for Windows ships with and automatically installs the new Windows launcher—a system that comes with new executable programs, py with
a console and pyw without, that are placed in directories on your system path, and so may be run out of the box without any PATH configurations, change-directory commands, or directory path prefixes:

```
c:\code> py
Python 3.3.0 (v3.3.0:bd8afb90ebf2, Sep 29 2012, 10:57:17) [MSC v.1600 64 bit ...
Type "help", "copyright", "credits" or "license" for more information.
>>> ^Z
c:\code> py −2
Python 2.7.3 (default, Apr 10 2012, 23:24:47) [MSC v.1500 64 bit (AMD64)] ...
Type "help", "copyright", "credits" or "license" for more information.
>>> ^Z
c:\code> py −3.1
Python 3.1.4 (default, Jun 12 2011, 14:16:16) [MSC v.1500 64 bit (AMD64)] ...
Type "help", "copyright", "credits" or "license" for more information.
>>> ^Z
```

## Running Code Interactively

With those preliminaries out of the way, let’s move on to typing some actual code. However it’s started, the Python interactive session begins by printing two lines of informational text giving the Python version number and a few hints shown earlier (which I’ll omit from most of this book’s examples to save space), then prompts for input with >>> when it’s waiting for you to type a new Python statement or expression. When working interactively, the results of your code are displayed below the >>> input lines after you press the Enter key.

```
% python
>>> print('Hello world!')
Hello world!
>>> print(2 ** 8)
256
```

When coding interactively like this, you can type as many Python commands as you
like; each is run immediately after it’s entered. Moreover, because the interactive session automatically prints the results of expressions you type, you don’t usually need to
say “print” explicitly at this prompt:

```
>>> lumberjack = 'okay'
>>> lumberjack
'okay'
>>> 2 ** 8
256
```

## Why the Interactive Prompt?
1. Experimenting
2. Testing


## Entering multiline statements
First, be sure to terminate multiline compound statements like for loops and if tests
at the interactive prompt with a blank line. In other words, you must press the Enter
key twice, to terminate the whole multiline statement and then make it run. For example
(pun not intended):
```
>>> for x in 'spam':
       print(x)  #press enter twice here
```

Also bear in mind that the interactive prompt runs just one statement at a time: you
must press Enter twice to run a loop or other multiline statement before you can type
the next statement:

```
>>> for x in 'spam':
...   print(x) # Press Enter twice before a new statement
... print('done')
 File "<stdin>", line 3
 print('done')
 ^
SyntaxError: invalid syntax
```
This means you can’t cut and paste multiple lines of code into the interactive prompt,
unless the code includes blank lines after each compound statement. Such code is better
run in a file—which brings us to the next section’s topic

## A First Script
Let’s get started. Open your favorite text editor (e.g., vi, Notepad, or the IDLE editor),
type the following statements into a new text file named script1.py, and save it in your
working code directory that you set up earlier:

```
# A first Python script
import sys # Load a library module
print(sys.platform)
print(2 ** 100) # Raise 2 to a power
x = 'Spam!'
print(x * 8)
```
This file is our first official Python script. You
shouldn’t worry too much about this file’s code, but as a brief description, this file:

• Imports a Python module (libraries of additional tools), to fetch the name of the
platform

• Runs three print function calls, to display the script’s results

• Uses a variable named x, created when it’s assigned, to hold onto a string object

• Applies various object operations that we’ll begin studying in the next chapter

The sys.platform here is just a string that identifies the kind of computer you’re working on; it lives in a standard Python module called sys, which you must import to load
(again, more on imports later).

## Running Files with Command Lines
Once you’ve saved this text file, you can ask Python to run it by listing its full filename
as the first argument to a python command like the following typed at the system shell
prompt (don’t type this at Python’s interactive prompt, and read on to the next paragraph if this doesn’t work right away for you):
```
% python script1.py
win32
1267650600228229401496703205376
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!
```
## Command-Line Usage Variations
Because this scheme uses shell command lines to start Python programs, all the usual
shell syntax applies. For instance, you can route the printed output of a Python script
to a file to save it for later use or inspection by using special shell syntax:

```
% python script1.py > saveit.txt
```

If you are working on a Windows platform, this example works the same, but the system
prompt is normally different as described earlier:
```
C:\code> python script1.py
win32
1267650600228229401496703205376
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!

```
As usual, if you haven’t set your PATH environment variable to include the full directory
path to python, be sure to include this in your command, or run a change-directory
command to go to the path first

```
C:\code> C:\python33\python script1.py
win32
1267650600228229401496703205376
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!
```

Alternatively, if you’re using the Windows launcher new in Python 3.3 (described earlier), a py command will have the same effect, but does not require a directory path or
PATH settings, and allows you to specify Python version numbers on the command line too:

```
c:\code> py −3 script1.py
win32
1267650600228229401496703205376
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!
```

On all recent versions of Windows, you can also type just the name of your script, and
omit the name of Python itself. Because newer Windows systems use the Windows Registry (a.k.a. filename associations) to find a program with which to run a file, you don’t need to name `python` or `py` on the command line explicitly to run a .py file.

```
C:\code> script1.py
```

## Unix-Style Executable Scripts: #!

Our next launching technique is really a specialized form of the prior, which, despite
this section’s title, can apply to program files run on both Unix and Windows today.
Since it has its roots on Unix, let’s begin this story there.

### Unix Script Basics

If you are going to use Python on a Unix, Linux, or Unix-like system, you can also turn files of Python code into executable programs, much as you would for programs coded in a shell language such as csh or ksh. Such files are usually called executable scripts. In
simple terms, Unix-style executable scripts are just normal text files containing Python
statements, but with two special properties:

• `Their first line is special.` Scripts usually start with a line that begins with the characters #! (often called “hash bang” or “shebang”), followed by the path to the
Python interpreter on your machine.

• `They usually have executable privileges.` Script files are usually marked as executable to tell the operating system that they may be run as top-level programs.
On Unix systems, a command such as chmod `+x` file.py usually does the trick.
Let’s look at an example for Unix-like systems. Use your text editor again to create a
file of Python code called `brian`:

```
#!/usr/local/bin/python
print('The Bright Side ' + 'of Life...') 
```

If you give the file executable privileges with a chmod +x brian shell command, you can run it from the operating
system shell as though it were a binary program (for the following, either make sure ., the current directory, is in your system PATH setting, or run this with ./brian):

```
% brian
The Bright Side of Life...
```
### The Unix env Lookup Trick

On some Unix systems, you can avoid hardcoding the path to the Python interpreter in your script file by writing the special first-line comment like this

```
#!/usr/bin/env python
...script goes here...
```

### The Python 3.3 Windows Launcher: #! Comes to Windows

A note for Windows users running Python 3.2 and earlier: the method described here is a Unix trick, and it may not work on your platform. Not to worry; just use the basic
command-line technique explored earlier. List the file’s name on an explicit python command line:

```
C:\code> python brian
The Bright Side of Life...
```


## Module Imports and Reloads

So far, I’ve been talking about “importing modules” without really explaining what this
term means. This section will introduce
enough module basics to get you started.

```
C:\code> C:\python33\python
>>> import script1
win32
1267650600228229401496703205376
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!
```

This works, but only once per session (really, process—a program run) by default. After
the first import, later imports do nothing, even if you change and save the module’s
source file again in another window:
```
...Change script1.py in a text edit window to print 2 ** 16...
>>> import script1
>>> import script
```

This is by design; imports are too expensive an operation to repeat more than once per file, per program run. Imports must find files, compile
them to byte code, and run the code.

If you really want to force Python to run the file again in the same session without
stopping and restarting the session, you need to instead call the reload function available in the imp standard library module (this function is also a simple built-in in Python
2.X, but not in 3.X):

```
>>> from imp import reload # Must load from module in 3.X (only)
>>> reload(script1)
win32
65536
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!
<module 'script1' from '.\\script1.py'>
>>>
```

## The Grander Module Story: Attributes

The basic idea is straight forward, though: a module is mostly just a package of variable names, known as a
namespace, and the names within that package are called attributes. An attribute is
simply a variable name that is attached to a specific object (like a module).

In more concrete terms, importers gain access to all the names assigned at the top level
of a module’s file. These names are usually assigned to tools exported by the module
—functions, classes, variables, and so on—that are intended to be used in other files
and other programs. Externally, a module file’s names can be fetched with two Python statements, `import` and `from`, as well as the `reload` call.


To illustrate, use a text editor to create a one-line Python module file called myfile.py
in your working directory, with the following contents:
```
title = "The Meaning of Life"
```

You can access this module’s title attribute in other components in two different ways.
First, you can load the module as a whole with an import statement, and then qualify the module name with the attribute name to fetch it (note that we’re letting the interpreter print automatically here):

```
% python # Start Python
>>> import myfile # Run file; load module as a whole
>>> myfile.title # Use its attribute names: '.' to qualify
'The Meaning of Life'
```

In general, the `dot` expression syntax `object.attribute` lets you fetch any attribute
attached to any object, and is one of the most common operations in Python code.

Alternatively, you can fetch (really, copy) names out of a module with `from` statements:

```
% python # Start Python
>>> from myfile import title # Run file; copy its names
>>> title # Use name directly: no need to qualify
'The Meaning of Life'
```

In practice, module files usually define more than one name to be used in and outside
the files. Here’s an example that defines three:
```
a = 'dead' # Define three attributes
b = 'parrot' # Exported to other files
c = 'sketch'
print(a, b, c) # Also used in this file (in 2.X: print a, b, c)
```

This file, `threenames.py`, assigns three variables, and so generates three attributes for
the outside world

```
% python threenames.py
dead parrot sketch
```

All of this file’s code runs as usual the first time it is imported elsewhere, by either an
`import` or `from`. Clients of this file that use `import` get a module with attributes, while
clients that use `from` get copies of the file’s names:

```
% python
>>> import threenames # Grab the whole module: it runs here
dead parrot sketch
>>>
>>> threenames.b, threenames.c # Access its attributes
('parrot', 'sketch')
>>>
>>> from threenames import a, b, c # Copy multiple names out
>>> b, c
('parrot', 'sketch')
```

The results here are printed in parentheses because they are really tuples—a kind of
object created by the comma in the inputs (and covered in the next part of this book)
—that you can safely ignore for now.

Once you start coding modules with multiple names like this, the built-in dir function
starts to come in handy—you can use it to fetch a list of all the names available inside
a module. The following returns a Python list of strings in square brackets (we’ll start
studying lists in the next chapter):

```
>>> dir(threenames)
['__builtins__', '__doc__', '__file__', '__name__', '__package__', 'a', 'b', 'c']
```

The contents of this list have been edited here because they vary per Python version.


### Modules and namespaces

Module imports are a way to run files of code, but, as we’ll expand on later in the book,
modules are also the largest program structure in Python programs, and one of the first
key concepts in the language.

As we’ve seen, Python programs are composed of multiple module files linked together
by import statements, and each module file is a package of variables—that is, a `namespace`

### import versus from

 I should point out that the `from` statement in a sense
defeats the namespace partitioning purpose of modules—because the
`from` copies variables from one file to another, it can cause same-named variables in the importing file to be overwritten, and won’t warn you if it does. This essentially collapses namespaces together, at least in terms of the copied variables.
Because of this, some recommend always using `import` instead of `from`.


### Using exec to Run Module Files

Strictly speaking, there are more ways to run code stored in module files than have yet
been presented here. For instance, the `exec(open('module.py').read())` built-in function call is another way to launch files from the interactive prompt without having to
import and later reload.

```
% python
>>> exec(open('script1.py').read())
win32
65536
Spam!Spam!Spam!Spam!Spam!Spam!Spam!Spam!
...Change script1.py in a text edit window to print 2 ** 32...
>>> exec(open('script1.py').read()
```