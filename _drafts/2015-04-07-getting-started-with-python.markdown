---
layout: post_simple
title:  "Getting Started with Python"
date:   2015-04-07

tags:
- python
- programming
---

## Overview

[Python](https://www.python.org/) is easy. As a programmer, however, I found it surprisingly difficult to wrap my head around how to do things the "right" way. There's a lot of yak shaving and while Python is very well documented and there are tons of great tutorials out there, I wanted to put together my own. Hopefully it helps someone explore and learn this great language.

## Installing Python

In order to use Python, you'll need to have it installed. More and more operating systems include Python so before you rush off and download anything, let's check to see if you already have Python.

## 2.x or 3.x?

Let's get this out of the way.

### Windows

If you're on a Windows-based machine, there's a *chance* you might have Python already. Just type "python" from a command prompt to check. If you already have Python you'll see something like this and you can move on:

```
C:\>python
Python 2.7.9 (default, Dec 10 2014, 12:28:03) [MSC v.1500 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

If you don't have Python you'll see something like this:

```
C:\>python
'python' is not recognized as an internal or external command,
operable program or batch file.
```

1. Browse to the [Python 2.7 for Windows](https://www.python.org/downloads/release/python-279/) page and download the Windows MSI installer for your architecture (x86 or x64)
2. Run the installer

#### Bash for Windows

I *highly* recommend installing a Bash-like shell on your Windows machine. It's going to make your life much easier as a lot of the examples and documentation you'll find for Python assume you're running Linux or OSX. You can use [Cygwin](https://www.cygwin.com) or some other alternative, but I use [Git for Windows](https://msysgit.github.io/) which comes with a great Bash shell that has a small footprint, loads fast, and doesn't have Cygwin's strange file system mapping. Oh yeah, and it brings an easy-to-use git client along, too!

***From here on in I'm going to assume that you have installed a Bash-like shell and all of the examples will assume that's what you're using as a command line.***

### OSX

If you're on OSX then you almost certainly have Python. Confirm it this way:

```
$ python
Python 2.7.6 (default, Sep  9 2014, 15:04:36)
[GCC 4.2.1 Compatible Apple LLVM 6.0 (clang-600.0.39)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

If you don't have Python already then you'll see something like this:

```
$ python
-bash: python: command not found
```

Don't panic! We'll get you squared away. The first thing to realize is that the version of Python that comes with OSX isn't *really* the official latest and greatest. At the very least, it's not 100% complete. No big deal. We're going to fix that.

Now, this is a *little* bit more difficult than other systems, but in the end you'll be all ready to go. The two things that you'll need beforehand are XCode and a package manager such as [Homebrew](http://brew.sh) or, if you prefer, [MacPorts](https://www.macports.org/). You need [XCode](http://developer.apple.com/xcode/) in order to get the command line tools necessary to build Python. XCode is free and easy to install so no big deal there.

As for the package manager, a little explanation is in order. See, while OSX comes with a lot of UNIX programs and utilities pre-installed there are gaps. Now, if you're running Linux then installing new stuff is usually handled by a package manager such as [yum](http://yum.baseurl.org/) or [rpm](http://www.rpm.org/). On your Mac you can get similar functionality with a package manager such as [Homebrew](http://brew.sh).

1. First, install [XCode](http://developer.apple.com/xcode/)
2. Next, [Install Homebrew](http://brew.sh/#install)
3. Now modify your PATH environment variable per the Homebrew instructions
4. Finally, install Python using Homebrew by typing:

```
$ brew install python
```

In just a couple of minutes you should have Python all ready to go. Now you should see something like this:

```
$ python
Python 2.7.9 (default, Feb 10 2015, 03:28:08)
[GCC 4.2.1 Compatible Apple LLVM 6.0 (clang-600.0.56)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

This should be different than what you saw before. If it isn't, be sure to check your PATH variable and double-check your steps. Homebrew will install the new Python in this location:

```
/usr/local/bin/python
```

### Linux

On Linux there's a good chance you'll have Python, but you should confirm it. If you do have Python you'll see something like this:

```
$ python
Python 2.7.9 (default, Dec 10 2014, 12:28:03) [MSC v.1500 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

If you don't have Python then you'll see something like this:

```
$ python
-bash: python: command not found
```

Don't panic! How you will install Python will depend on your distribution. Check the [Python Download](https://wiki.python.org/moin/BeginnersGuide/Download) page for details. Be sure to grab the 2.x version of Python!

## Packages

One great thing about Python is that there are a *lot* of packages available to solve all sorts of problems. Basically, these packages are libraries that let you easily do all sorts of cool things. Check out the [PyPI index](https://pypi.python.org/pypi/) to get an idea of what's out there. If you're a .NET programmer, these are kind of like NuGet packages. If you're a Ruby programmer, these are like Gems. Perl? CPAN! PHP? Packagist! Node.js? NPM!

## Setuptools & Pip

Python packages are great, but having an easy way to install them is even better! A part of Setuptools is `easy_install` which is an older method of installing packages. You *will* want to have Setuptools, however, for now we're using it as a means to an end. Specifically, we want to use `easy_install` to install Pip.

See, Pip is a newer tool that lets us install Python packages and it offers [several advantages](https://python-packaging-user-guide.readthedocs.org/en/latest/pip_easy_install.html#pip-vs-easy-install) versus `easy_install`. [Go here to learn how to install pip](https://pip.pypa.io/en/latest/installing.html).

At this point you should have a fully functional Python 2.x environment with Setuptools and Pip. If you're running Linux or OSX (or if you followed my advice and installed a Bash-like shell on your Windows machine) you can verify everything like this at the command line:

1. Type `$ which python` to make sure Python is installed
2. Type `$ python` and make sure you see the version number you expect
3. Type `$ which easy_install` to make sure Setuptools is installed
4. Type `$ which pip` to make sure Pip is installed

If you get no results to the `which` commands or you don't see the paths or versions you expect then double check your PATH variable and, if necessary, re-install as necessary. You'll need everything working before you continue.

## Virtual Environments

Having all these Python packages available to us is great. However, it does introduce a significant problem that emerges as you write more and more code. That problem is one of versions and dependencies. See, if you do nothing then each package you install will be installed *globally*. In other words, you'd have a single copy of the package on your computer. It's similar to the old Windows "DLL Hell" problem in that you can quickly create problems with dependencies and versions.

Fortunately, we have a solution! We'll use [virtualenv](https://virtualenv.pypa.io/en/latest/) to create *virtual environments* that let us work with each of our projects in complete isolation. In other words, it lets us have multiple Python projects with *different* (and in many cases conflicting) package requirements on our computer. Frankly, it's hard to imagine using Python without it so let's get it installed:

```
$ [sudo] pip install virtualenv
```

A virtualenv environment is nothing more than a directory in your project that everything you'll need to run a Python program. It even has a copy of the Python program itself! It also has a copy of the `site-packages` directory which is where packages are installed. Now when you install a package you'll get it in your isolated `site-packages` directory and avoid polluting your global installation.

## Creating a Virtual Environment

Now that we have our tooling in place, let's create a new virtual environment using `virtualenv`. Start by navigating to the directory you want to create your new project in. For example:

```
$ cd /myprojects
```

Now let's create our virtual environment:

```
$ virtualenv helloworld
```

You should see something like this:

```
New python executable in helloworld/bin/python2.7
Also creating executable in helloworld/bin/python
Installing setuptools, pip...done.
```

Now we have a new virtual environment! Let's have a look around:

```
|
+- bin
|
+- include
|
+- lib
```

NOTE: On Windows machines the `bin` directory will be called `scripts` instead.

Neat! Well, kind of. What you have now are all the bits and pieces necessary to run your virtual environment. However, we need to *activate* the new environment. To do that we'll simply change to our new directory:

```
$ cd helloworld
```

Now we'll activate the virtual environment with the `activate` script:

```
$ source /bin/activate
```

NOTE: On Windows machines you have an `activate.bat` file that does the same thing as `source /bin/activate` on *nix machines.

One cool thing that virtualenv does is modify your prompt so that you can tell what virtual environment you have activated (if any). Your prompt should look like this:

```
(helloworld) $
```

You're ready to go!

# Hello World

With your new virtual environment activated, fire up your favorite text editor and create a file in the root of your project named `helloworld.py` and put this in it:

```python
print "Hello world!"
```

Save your file, exit your editor, and type this from the command prompt:

```
(helloworld) $ python helloworld.py
```

Assuming all went well, you should see this:

```
Hello world!
```

Whew! You've done it! Your very first (incredibly boring) Python app!

## Project Structure

When it comes to setting up your project's file and directories, Python enthusiasts like to tell you things like, "Hey, do whatever works for you!" They aren't *technically* lying, but I'll tell you that life is much easier if you start with a fairly common skeleton. This is an area that tripped me up a *lot* initially (and still does to some degree). Here's the bare-bones skeleton that I use (*without* the virtual environment folders):

```
|
+- project
   |
   +- package
   |  |
   |  +- __init__.py
   |     __main__.py
   |
   +- setup.py

```

Bear in mind that this is a *minimal* structure. At first, this structure is going to seem pretty weird. Trust me. It will make more sense in a little bit. Let's start by explaining those strange `__init__.py` and `__main__.py` files.

### `__init__.py`

The `__init__.py` file, when placed in a directory, causes Python to treat that directory as one that contains packages. Often this file is empty, but it may contain code under certain circumstances. That's for another day.

### `__main__.py`

The `__main__.py` file is the one that Python executes when placed in a directory. If your project is a pure package that isn't meant to be executed directly then you won't need this file. You can just put the file(s) containing your code in this folder.

Let's take our `helloworld.py` file and make it fit this structure:

```
(helloworld) $ mkdir helloworld
(helloworld) $ mv helloworld.py /helloworld/__main__.py
(helloworld) $ touch /helloworld/__init__.py
```

Now, if we run our program again:

```
(helloworld) $ python helloworld
```

We should see:

```
Hello world!
```

The magic happens because Python treated our `helloworld` directory with the `__init__.py` as a package and ran `__main__.py` based on the naming convention. Neat!

## Entry Points

Given the nature of Python, you could simply dump code in your file and move on. However, you're more likely to want a *little* structure to keep things sane. Let's modify our `__main__.py` file from before to look like this:

```python
def main(args=None):
    print_hello_world()

def print_hello_world():
    print "Hello world!"

main()
```

Now if we run our program as before everything should output the same. All we've done is put everything into functions and then called the entry function at the end to kick things off. This is great, but it does have a drawback. What if we wanted another program to use code in this one as an imported module? In other words, what if we wanted to import a function from this program for use in another program? We can, but as it is this code will execute rather than simply import. To fix it we'll make a small change:

```python
def main(args=None):
    print_hello_world()

def print_hello_world():
    print "Hello world!"

if __name__ == "__main__":
    main()
```

Here we've taken advantage of a Python interpreter feature. See, when Python reads our code it will assign the `__name__` variable to have a value `__main__` if it's running as the main program. If this file is being imported from another module, '__name__' will be set to the module's name. As such, we can perform a little test and only run the `main` function if we're not being imported. Great!

## Installing Packages

## Includes

### `setup.py`

```python
from setuptools import setup
import py2exe

setup (
    name = "MyApp",
    version = "0.1",
    description="MyApp is not a dead parrot.",
    author="Arthur McCoddleswat",
    author_email="arthur@myapp.com",
    url="http://www.myapp.com/",
    packages=['myapp'],
    entry_points = {
        'console_scripts': ['MyApp = myapp.__main__:main']
                    },
    download_url = "http://www.myapp.com/download/",
    zip_safe = True
)
```

## Unit Testing

## Creating Executables

### Windows

We've covered a lot of ground and I've treated

### OSX

### Linux
