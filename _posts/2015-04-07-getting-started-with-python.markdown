---
layout: post_simple
title:  "Getting Started with Python"
date:   2015-04-08

tags:
- python
- programming
---

# Overview

The [Python](https://www.python.org/) language is easy. As a long-time programmer, however, I found it surprisingly difficult to wrap my head around how to do things with Python the "right" way. There are tons of great tutorials out there, but none of them put it all together in a way that really made me feel like I had a complete setup that wouldn't have experienced Python programmers chuckling to themselves.

Hopefully this guide will give you a kick start to learning this great language. If not (or even if it does), I still recommend checking out the official Python documentation and [The Hitchiker's Guide to Python](http://docs.python-guide.org/en/latest/). Both are outstanding references that go into greater detail than I do here.

Additionally, I'm going to begin each section with at least one link to either the official documentation or another great example of the topic. Generally, these are links to places where I found answers. More often than not, these will contain *much* more information than I'm giving here. This is particularly true when it comes to troubleshooting and fringe cases. If you find an error or have a question then [drop me a line](http://gregmajor.com/#section-contact)!

Let's get the [yak shaving](http://www.hanselman.com/blog/YakShavingDefinedIllGetThatDoneAsSoonAsIShaveThisYak.aspx) over with first.

# Installing Python

The official documentation for installing Python can be [found here](https://wiki.python.org/moin/BeginnersGuide/Download).

In order to use Python, you'll need to have it installed. Let's get that out of the way now.

## 2.x or 3.x?

The official documentation regarding the differences between v2 and v3 of Python can be [found here](https://wiki.python.org/moin/Python2orPython3). Another great explanation of Python interpreters can be [found here](http://docs.python-guide.org/en/latest/starting/which-python/).

Let's get this out of the way. My opinion is that beginners should stick with v2. It's been around a really long time and you're less likely to run into problems finding packages and code examples. That being said, there's no technical reason you *shouldn't* go with v3, but just know that you may run into some compatibility issues here and there.

## Installing on Windows

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

Don't panic! I'll give you a couple of options to get Python installed.

### Method 1 (MSI Installer)

1. Browse to the [Python 2.7 for Windows](https://www.python.org/downloads/release/python-279/) page and download the Windows MSI installer for your architecture (x86 or x64)
2. Run the installer

The Python installer will, by default, create a directory that is `Python` plus the version number, e.g. Python version 2.7 will install at `C:\Python27`. Note that it is up to you to edit your PATH environment variable since the installer doesn't do that for you.

### Method 2 (Chocolatey)

[Chocolatey](https://chocolatey.org/) is a package manager for Windows based on NuGet. What does that mean? Well, if you're familiar with most Linux distributions you've likely already used one. For example, [yum](http://yum.baseurl.org/) or [rpm](http://www.rpm.org/). Essentially, it's a way to install software and all of its dependencies *and* keep it updated quickly and easily. This method starts by installing Chocolatey and then proceeds to use it to install Python.

1. Browse to [Chocolatey](https://chocolatey.org/) and follow the instructions to run the Powershell script that will install Chocolatey
2. Next, open a command prompt and type `choco install python2`

In just a few minutes you should have a nice, fresh install of Python in the `C:\tools\python2` directory. Take a few minutes to browse the other Chocolatey packages. There's a *lot* of great stuff there and it's an excellent tool to get a Windows machine up and running quickly.

### Bash for Windows

I *highly* recommend installing a Bash-like shell on your Windows machine. It's going to make your life much easier as a lot of the examples and documentation you'll find for Python assume you're running Linux or OSX. You can use [Cygwin](https://www.cygwin.com) or some other alternative, but I use [Git for Windows](https://msysgit.github.io/) which comes with a great Bash shell that has a small footprint, loads fast, and doesn't have Cygwin's strange file system mapping. Oh yeah, and it brings git along with it, too!

***From here on in I'm going to assume that you have installed a Bash-like shell and almost all of the examples that aren't Windows-specific will assume that's what you're using as a command line.***

## Installing on OSX

If you're on OSX then you almost certainly have Python. Confirm it this way:

```bash
$ python
Python 2.7.6 (default, Sep  9 2014, 15:04:36)
[GCC 4.2.1 Compatible Apple LLVM 6.0 (clang-600.0.39)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

If you don't have Python already then you'll see something like this:

```bash
$ python
-bash: python: command not found
```

The first thing to realize is that the version of Python that comes with OSX isn't *really* the official latest and greatest. At the very least, it's not 100% complete. No big deal. Don't panic! We're going to fix that.

Now, this is a *little* bit more difficult than other systems, but in the end you'll be all ready to go. The two things that you'll need beforehand are XCode and a package manager such as [Homebrew](http://brew.sh) or, if you prefer, [MacPorts](https://www.macports.org/). You need [XCode](http://developer.apple.com/xcode/) in order to get the command line tools necessary to build Python. XCode is free and easy to install so no big deal there.

As for the package manager, a little explanation is in order. See, while OSX comes with a lot of UNIX programs and utilities pre-installed there are gaps. Now, if you're running Linux then installing new stuff is usually handled by a package manager such as [yum](http://yum.baseurl.org/) or [rpm](http://www.rpm.org/). On your Mac you can get similar functionality with a package manager such as [Homebrew](http://brew.sh).

1. First, install [XCode](http://developer.apple.com/xcode/)
2. Next, [Install Homebrew](http://brew.sh/#install)
3. Now modify your PATH environment variable per the Homebrew instructions
4. Finally, install Python using Homebrew by typing:

```bash
$ brew install python
```

In just a couple of minutes you should have Python all ready to go. Now you should see something like this when you type `python` from a terminal:

```bash
$ python
Python 2.7.9 (default, Feb 10 2015, 03:28:08)
[GCC 4.2.1 Compatible Apple LLVM 6.0 (clang-600.0.56)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

This should be different than what you saw before. If it isn't, be sure to check your PATH variable and double-check your steps. Homebrew will install the new Python in this location:

```bash
/usr/local/bin/python
```

## Installing on Linux

On Linux there's a good chance you'll have Python, but you should confirm it. If you do have Python you'll see something like this:

```bash
$ python
Python 2.7.9 (default, Dec 10 2014, 12:28:03) [MSC v.1500 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

If you don't have Python then you'll see something like this:

```bash
$ python
-bash: python: command not found
```

Don't panic! How you will install Python will depend on your distribution. Check the [Python Download](https://wiki.python.org/moin/BeginnersGuide/Download) page for details. Be sure to grab the 2.x version of Python!

# Modules and Packages

The official documentation for modules and packages can be [found here](http://docs.python.org/tutorial/modules.html).

One great thing about Python is that there are a *lot* of packages available to solve all sorts of problems. Basically, these packages are collections (one or more) modules that you can import into your code and use. Modules are nothing more than files that contain Python code. There are packages containing modules that do all sorts of neat things. Check out the [PyPI index](https://pypi.python.org/pypi/) to get an idea of what's out there. If you're a .NET programmer, these are kind of like NuGet packages. If you're a Ruby programmer, these are like Gems. Perl? CPAN! PHP? Packagist! Node.js? NPM!

Before we talk any more about modules and packages, however, we really need to do some more yak shaving. Sorry.

<iframe width="560" height="315" src="//www.youtube.com/embed/trXjZ70ab1Q" frameborder="0" allowfullscreen></iframe>

# Setuptools & Pip

The official documentation for installing Pip can be [found here](https://pip.pypa.io/en/latest/installing.html).

Python packages are great, but having a super easy way to install them is even better! Setuptools is a library used to package Python projects. A part of Setuptools is `easy_install` which is an older method of actually installing packages. You *will* want to have Setuptools, however, for now you're using it as a means to an end. Specifically, you want to use `easy_install` to install Pip. Pip is a newer tool that also lets us install Python packages and it offers [several advantages](https://python-packaging-user-guide.readthedocs.org/en/latest/pip_easy_install.html#pip-vs-easy-install) versus `easy_install`.

Once Pip is installed, you have a fully functional Python environment. If you're running Linux or OSX (or if you followed my advice and installed a Bash-like shell on your Windows machine) you can verify everything like this at the command line:

1. Type `$ which python` to make sure Python is installed
2. Type `$ python` and make sure you see the version number you expect
3. Type `$ which easy_install` to make sure Setuptools is installed
4. Type `$ which pip` to make sure Pip is installed

If you get no results to the `which` commands or you don't see the paths or versions you expect then double check your PATH variable and, if necessary, re-install as necessary. You'll need everything working before you continue.

# Virtual Environments

The official documentation for virtualenv can be [found here](https://virtualenv.pypa.io/en/latest/userguide.html).

Having all these Python packages available to us is great. However, it does introduce a significant problem that emerges as you write more and more code. That problem is one of versions and dependencies. See, if you do nothing then each package you install will be installed *globally*. In other words, you'd have a single copy of the package on your computer. It's similar to the old Windows "DLL Hell" problem in that you can quickly create problems with dependencies and versions.

Fortunately, there's a solution! You'll use [virtualenv](https://virtualenv.pypa.io/en/latest/) to create *virtual environments* that let us work with each of your projects in complete isolation. In other words, it lets us have multiple Python projects with *different* (and in many cases conflicting) package requirements on your computer. Frankly, it's hard to imagine using Python without it so let's get it installed:

```bash
$ [sudo] pip install virtualenv
```

A virtualenv environment is nothing more than a directory in your project that everything you'll need to run a Python program. It even has a copy of the Python program itself! It also has a copy of the `site-packages` directory which is where packages are installed. Now when you install a package you'll get it in your isolated `site-packages` directory and avoid polluting your global installation.

# Creating a New Virtual Environment

The official documentation for creating a new environment with virtualenv can be [found here](https://virtualenv.pypa.io/en/latest/userguide.html#usage).

Now that you have your tooling in place, let's create a new virtual environment using `virtualenv`. Start by navigating to the directory you want to create your new project in. For example:

```bash
$ cd /myprojects
```

Now let's create the virtual environment:

```bash
$ virtualenv helloworld
```

You should see something like this:

```bash
New python executable in helloworld/bin/python2.7
Also creating executable in helloworld/bin/python
Installing setuptools, pip...done.
```

Now you have a new virtual environment! Let's have a look around:

```
|
+- helloworld
   |
   +- bin
   |
   +- include
   |
   +- lib
```

NOTE: On Windows machines the `bin` directory will be called `Scripts` instead.

Neat! Well, kind of. What you have now are all the bits and pieces necessary to run your virtual environment. However, you need to *activate* the new environment. To do that you'll simply change to your new directory:

```bash
$ cd helloworld
```

Now you'll activate the virtual environment with the `activate` script:

```bash
$ source /bin/activate
```

NOTE: On Windows machines you have an `activate.bat` file that does the same thing as `source /bin/activate` on *nix machines.

One cool thing that virtualenv does is modify your prompt so that you can tell what virtual environment you have activated (if any). Your prompt should look like this:

```bash
(helloworld) $
```

You're ready to go! When you want to *deactivate* a virtual environment, you'll need to run `deactivate` from your command prompt or, if you're on Windows, execute the `Scripts\deactivate.bat` file.

At this point I should mention a popular tool amoung Pythonists called [virtualenvwrapper](http://virtualenvwrapper.readthedocs.org/en/latest/index.html). Virtualenvwrapper is a set of extensions to virtualenv that many people find very useful. Personally, I've not used it because I haven't had the need, but it's something you may want to investigate on your own.

# Hello World

A great example of a "Hello World" script in Python can be [found here](http://learnpythonthehardway.org/book/ex1.html).

With your new virtual environment activated, fire up your favorite text editor and create a file in the root of your project named `helloworld.py` and put this in it:

```python
print "Hello world!"
```

Save your file, exit your editor, and type this from the command prompt:

```bash
(helloworld) $ python helloworld.py
```

Assuming all went well, you should see this:

```bash
Hello world!
```

Whew! You've done it! Your very first (incredibly boring) Python app!

# Project Structure

When it comes to setting up your project's file and directories, Python enthusiasts like to tell you things like, "Hey, do whatever works for you!" They aren't *technically* lying, but I'll tell you that life is much easier if you start with a fairly common skeleton. This is an area that tripped me up a *lot* initially (and still does every now and again). Here's the bare-bones skeleton that I use (*without* the directories that virtualenv creates):

```
|
+- project
   |
   +- package
   |  |
   |  +- __init__.py
   |  |
   |  +- __main__.py
   |  |
   |  +- module.py
   |
   +- setup.py

```

Bear in mind that this is a *minimal* structure. At first, this structure is going to seem a bit weird. Trust me. It will make more sense in a little white. Let's start by explaining those strange `__init__.py` and `__main__.py` files. We'll discuss `setup.py` a bit later.

## `__init__.py`

The `__init__.py` file, when placed in a directory, causes Python to treat that directory as one that contains packages. Often this file is empty, but it may contain code under certain circumstances. That's for another day.

## `__main__.py`

The `__main__.py` file is the one that Python executes when placed in a directory. If your project is a pure package that isn't meant to be executed directly then you won't need this file. You can just put the file(s) containing your code in this folder (represented by the strictly optional `module.py` file in the example above).

Let's transform your current `helloworld.py` program to look like this:

```
|
+- helloworld
   |
   +- helloworld
      |
      +- __init__.py
      |
      +- __main__.py
```

Here's a quick guide to make it happen:

```bash
(helloworld) $ mkdir helloworld
(helloworld) $ mv helloworld.py /helloworld/__main__.py
(helloworld) $ touch /helloworld/__init__.py
```

Now, if you run your program again:

```bash
(helloworld) $ python helloworld
```

You should see:

```bash
Hello world!
```

The magic happens because Python treated the `helloworld` directory with the `__init__.py` as a package and ran the code in `__main__.py` based on the naming convention. Neat! For really simple programs this is plenty good enough. For more complicated programs, however, you'll probably want to go a little further.

# Entry Points

Given the nature of Python, you could simply dump code in your `__main__.py` file and move on. However, you're more likely to want a *little* structure to keep things sane. Let's modify the `__main__.py` file from before to look like this:

```python
def main(args=None):
    print_hello_world()

def print_hello_world():
    print "Hello world!"

main()
```

Now if you run your program as before everything should output the same. All you've done is put everything into functions and then called the entry function at the end to kick things off. This is great, but it does have a drawback. What if you wanted another program to use code in this one as an imported module? In other words, what if you wanted to import a function from this program for use in another program? You can, but as it is this code will execute rather than simply import. To fix it you'll make a small change:

```python
def main(args=None):
    print_hello_world()

def print_hello_world():
    print "Hello world!"

if __name__ == "__main__":
    main()
```

Here you've taken advantage of a Python interpreter feature. See, when Python reads your code it will assign the `__name__` variable to have a value `__main__` if it's running as the main program. If this file is being imported from another module, `_name__` will be set to the module's name. As such, you can perform a little test and only run the `main` function if your module not being imported. Great!

# Creating and Importing Modules

As your programs grow and you write code that you want to reuse you'll want a better way to organize it. In Python we have the module and package system that we discussed a bit earlier. Let's re-organize your program to see how modules work.

Creating a new module is very easy. Just create a new `.py` file and the name of the file will be your new module name. To use your new module you'll need to import it. Create a new file named `helloworld.py` in your `/helloworld/helloworld/` directory. You should end up with a structure like this:

```
|
+- helloworld
   |
   +- helloworld
      |
      +- __init__.py
      |
      +-- __main__.py
      |
      +-- helloworld.py
```

Now take the `print_hello_world` function and move it into your new `helloworld.py` file. It should look like this:

```python
def print_hello_world():
    print "Hello world!"
```

Now edit your `__main__.py` to look like this:

```python
from helloworld import print_hello_world

def main(args=None):
    print_hello_world()

if __name__ == "__main__":
    main()
```

If you run your program then you should see the same `Hello world!` output as before. If you don't, double-check your code carefully.

The module and package system in Python is powerful and flexible. There are a few conventions you'll want to pay attention to. Hopefully this tiny example will give you an essential understanding. From here, my recommendation is to read the official documentation for modules and packages [found here](http://docs.python.org/tutorial/modules.html). Among other things, it will teach you about having multiple modules and namespaces.

# Installing Packages

The official documentation for installing packages with Pip can be [found here](https://python-packaging-user-guide.readthedocs.org/en/latest/installing.html#use-pip-for-installing).

Let's say that you want to write a web app with Python. Great! There are quite a few great web frameworks available for Python ranging from the full-featured ones such as [Django](http://www.djangoproject.com/) and [TurboGears](http://www.turbogears.org/) to smaller micro frameworks such as [Flask](http://flask.pocoo.org/), [web2py](http://www.web2py.com/), and [Pyramid](http://www.pylonsproject.org/). Let's assume you want to try Flask. So how can you get it and start using it? We'll use Pip!

```bash
(helloworld) $ pip install flask
```

You should see something like this:

```
Collecting flask
  Downloading Flask-0.10.1.tar.gz (544kB)
    100% |################################| 544kB 984kB/s
Collecting Werkzeug>=0.7 (from flask)
  Downloading Werkzeug-0.10.4-py2.py3-none-any.whl (293kB)
    100% |################################| 294kB 68kB/s
Collecting Jinja2>=2.4 (from flask)
  Downloading Jinja2-2.7.3.tar.gz (378kB)
    100% |################################| 380kB 540kB/s
Collecting itsdangerous>=0.21 (from flask)
  Downloading itsdangerous-0.24.tar.gz (46kB)
    100% |################################| 49kB 1.2MB/s
Collecting markupsafe (from Jinja2>=2.4->flask)
  Downloading MarkupSafe-0.23.tar.gz
Installing collected packages: markupsafe, itsdangerous, Jinja2, Werkzeug, flask
  Running setup.py install for markupsafe
    building 'markupsafe._speedups' extension
    clang -fno-strict-aliasing -fno-common -dynamic -I/usr/local/include -I/usr/local/opt/sqlite/include -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes -I/usr/local/Cellar/python/2.7.9/Frameworks/Python.framework/Versions/2.7/include/python2.7 -c markupsafe/_speedups.c -o build/temp.macosx-10.10-x86_64-2.7/markupsafe/_speedups.o
    clang -bundle -undefined dynamic_lookup -L/usr/local/lib -L/usr/local/opt/sqlite/lib build/temp.macosx-10.10-x86_64-2.7/markupsafe/_speedups.o -o build/lib.macosx-10.10-x86_64-2.7/markupsafe/_speedups.so
  Running setup.py install for itsdangerous
  Running setup.py install for Jinja2

  Running setup.py install for flask
Successfully installed Jinja2-2.7.3 Werkzeug-0.10.4 flask-0.10.1 itsdangerous-0.24 markupsafe-0.23
```

Tada! Just like that you have installed Flask and it's dependencies (Jinja2 - a templating enging, Werkzeug - a WSGI library, itsdangerous - a signing library, and markupsafe - a safe string library for XML and HTML) and it only took a few seconds. Now you can write something like this:

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")

def hello():
    return "Hello world!"

if __name__ == "__main__":
    app.run()
```

```bash
(helloworld) $ python hello.py
```

Open your browser to the URL displayed after you ran the command and you should see our familiar "Hello world!" text. To learn more about Flask, check out the official documentation which can be [found here](http://flask.pocoo.org/docs/0.10/). I digress. What you have now is the power to install packages from the [PyPI index](https://pypi.python.org/pypi/) using Pip. Have fun!

## Distributing Your Code

The official documentation for Distutils can be [found here](https://docs.python.org/2/distutils/index.html).

Sooner or later you're going to want to share your code with other people. That's great! This is where we need a packaging tool. Now, there are quite a few options and each has advantages and disadvantages (see [this Stack Overflow post](http://stackoverflow.com/questions/6344076/differences-between-distribute-distutils-setuptools-and-distutils2) for a great run-down). For this example, however, we're going to start with the built-in Distutils packaging tool. These are the four things you'll be concerned with:

1. Writing a setup script (`setup.py` by convention)
2. *(optional)* Writing a setup configuration file
3. Creating a source distribution
4. *(optional)* Creating one or more built distributions

### 1. Writing a Setup Script

The official documentation for `setup.py` can be [found here](https://docs.python.org/2/distutils/setupscript.html).

The official documentation describes `setup.py` this way:

> The setup script is the centre of all activity in building, distributing, and installing modules using the Distutils. The main purpose of the setup script is to describe your module distribution to the Distutils, so that the various commands that operate on your modules do the right thing.

Here's an example:

```python
from distutils.core import setup

setup (
    name = "HelloWorld",
    version = "1.0",
    description="HelloWorld prints a friendly greeting to the screen.",
    author="Arthur McCoddleswat",
    author_email="arthur@helloworld.com",
    url="http://www.helloworld.com/",
    packages=['helloworld'],
    entry_points = {
        'console_scripts': ['HelloWorld = helloworld.__main__:main']
                    },
    download_url = "http://www.helloworld.com/download/",
    zip_safe = True
)
```

Note that there are other variables that you can supply, but these are a fairly common minimum set.

### 2. (optional) Writing a Setup Configuration File

The official documentation for writing setup configuration files can be [found here](https://docs.python.org/2/distutils/configfile.html).

Sometimes you can't capture everything you need to build your distribution in the `setup.py` file. You may need the user to give you some input in order to get the job done. A great way to tackle this is to create a `setup.cfg` file that the user can edit or that can provide default values the installer can override based on command arguments. I won't go into detail here, however. Have a peek at the official documentation when you need to learn how these work.

### 3. Creating a Source Distribution

The official documentation for creating source distributions can be [found here](https://docs.python.org/2/distutils/sourcedist.html).

To create a source distribution for your module, you need to create a setup script, `setup.py`, similar to the one shown above. Next, run this command from your terminal:

```bash
python setup.py sdist
```

For Windows, open a command prompt and run this:

```
setup.py sdist
```

`sdist` will create an archive file (e.g., tarball on Unix, ZIP file on Windows) containing `setup.py`, and your module. The archive file will be named `helloworld-1.0.tar.gz` (or `.zip`), and will unpack into a `helloworld-1.0` directory. If someone else wants to install your module, all they have to do is download your archive file, unzip it, and then run this from the command line:

```bash
python setup.py install
```

This will copy all the necessary stuff into a directory reserved for third-party modules in their Python installation. Congratulations! You've just published software!

### 4. (optional) Creating One or More Built Distributions

The official documentation for creating built distributions can be [found here](https://docs.python.org/2/distutils/builtdist.html).

Per the official documentation:

> A built distribution is how you make life as easy as possible for installers of your module distribution: for users of RPM-based Linux systems, it’s a binary RPM; for Windows users, it’s an executable installer; for Debian-based Linux users, it’s a Debian package; and so forth. Obviously, no one person will be able to create built distributions for every platform under the sun, so the Distutils are designed to enable module developers to concentrate on their specialty—writing code and creating source distributions—while an intermediary species called packagers springs up to turn source distributions into built distributions for as many platforms as there are packagers.

I won't go into detail here, but you should really check out the official documentation get the a handle on how built distributions work.

# Creating Executables

Now, creating modules that you can distribute for other Python programmers can use is great, but if you're like me then you'll probably want to create executables and apps from your code, too. This generally isn't *too* bad, but it does depend on your target operating system. If you've been following along with the helloworld example then you're almost ready to create an executable for your platform. Let's have a quick look at each method.

## Windows

The official documentation for py2exe can be [found here](http://www.py2exe.org/index.cgi/Tutorial).

For Windows, we're going to use [py2exe](http://www.py2exe.org) to turn our package into a Windows executable *without* needing to install Python on that computer. In fact, all they really do is compile your code to bytecode and bundle a Python interpreter. There are other options besides py2exe, of course, such as [cx_freeze](http://cx-freeze.sourceforge.net/) and [PyInstaller](https://github.com/pyinstaller/pyinstaller/wiki), but py2exe is straight-forward and works well in most cases.

1. [Download py2exe](http://sourceforge.net/projects/py2exe/files/py2exe/) and install it
2. Open a command prompt, make sure your vitual environment is activated, and type `python setup.py py2exe`

You should see a screen full of output and, assuming everything was working when you ran your program before and your `setup.py` file is correct then you will have a `dist` directory that contains your new executable (and the files it needs to execute). Give it a try!

## OSX

The official documentation for py2app can be [found here](https://pythonhosted.org/py2app/tutorial.html#create-a-setup-py-file).

For OSX, we're going to use [py2app](https://pythonhosted.org/py2app/) to turn our package into an app. The process is almost identical to py2exe.

1. [Install py2app](https://pythonhosted.org/py2app/install.html) (the easiest way is with Pip)
2. Open a terminal, activate your virtual environment, and type `python setup.py py2app`

In short order you should now have a `.app` file in your `dist` directory. There are other really nice options that you can try while developing your app so be sure to check out the official documentation.

## Linux

The official documentation for PyInstaller can be [found here](https://github.com/pyinstaller/pyinstaller/wiki). Using PyInstaller isn't all that difficult, but you're probably best reading the official documentation since summarizing here would take quite a while. Sorry Tux fans!

# Summary

I hope that by now you have a fully functional Python environment that lets you write Python code, safely isolate dependencies, create packages, and build executables. There's a *lot* of ground that I didn't cover such as [writing unit tests](https://nose.readthedocs.org/en/latest/index.html), the [Python language](https://docs.python.org/2/reference/) itself, [documenting your code](https://www.python.org/dev/peps/pep-0257/), [Python Enhancement Proposals (PEP)](https://www.python.org/dev/peps/), and so on. In time I hope to add addendums that will fill some or all of those gaps.

Meanwhile, I hope this guide has helped and you enjoy learning Python!
