---
layout: post_image
title: "Getting Started With Git"
date: 2016-03-31 02:08:00
image_file: "blog/getting-started-with-git.jpg"

tags:
- git
- programming
---

Okay, let's assume you've used version control systems before and perhaps you've even used Git. Great! However, you're still a bit confused about how it all works and what you should be doing. Groovy! That makes you just like every other Git user at some point in their lives. This is a primer (or refresher) on Git.

On the other hand, if you have a complete mastery of when rebasing makes sense and under what circumstances a forced push is useful then TL;DR and move on. Have a nice day. Better yet, send me a pull request on how this could be made better.

## Installation

It won't come as much of a surprise to learn that in order to use Git you'll need to have it installed on your computer. Let's get that out of the way first.

### Windows

There are several approaches to installing Git on Windows. My personal preference is to use [Git for Windows](https://git-for-windows.github.io/) as it provides a pretty decent [BASH](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) implementation, a decent Git GUI (if you're in to that kind of thing), and shell integration. If you prefer to spend your time in PowerShell you'll probably prefer [posh-git](https://github.com/dahlbyk/posh-git). Of course, you can also just install from [the Git download page](https://git-scm.com/downloads).

### OS X

Congratulations! You already have Git. However, the version you have is likely pretty outdated. You can download the latest from [the Git download page](https://git-scm.com/downloads) or, if you prefer, use a tool like [Homebrew](http://www.brew.sh) to install it and stay up to date.

### Linux

Congratulations! [The architect of your operating system is also the guy that created Git](https://en.wikipedia.org/wiki/Linus_Torvalds) so you're off to a great start. You probably already have Git, but if not then it's certainly easy to find thanks to your distribution's package manager (`apt-get`, `rpm`, or whatever). Using a distribution that doesn't have a package manager or you're not familiar with how to install software on your Linux computer? Well, you're probably used to reading HOWTO documents already so... do that.

### BeOS/MS-DOS/Minux/OS2/NetWare

Seriously? I mean, cool. Good for you, buddy.

### Git GUI's

I found [this quote regarding Git](http://readwrite.com/2013/09/30/understanding-github-a-journey-for-beginners-part-1) recently:

> "The problem with Git is that it’s so ancient that we have to use the command line or Terminal if you’re a Mac user in order to access it, typing in snippets of code like ‘90s hackers. This can be a difficult proposition for modern computer users. That’s where GitHub comes in."

Typing simple commands on a (**gasp**) command line is _difficult_? If that's the case for you then perhaps you should visit your guidance counselor and [talk about an exciting career in TV and VCR repair](https://www.youtube.com/watch?v=fBuV_7X8mI4). Seriously, learning Git means learning **Git** which is _not_ a pretty graphical interface. Are those available? Sure! They're out there. They can be nice to use, too. Do yourself a huge favor, however, and learn the tool _then_ learn the other goodies. Oh, and the notion that [GitHub](http://www.github.com) is just a graphical interface for Git? Just ignore that.

## Setup

Git uses dotfiles (literally, files with names that begin with a full stop a.k.a., "period" or "dot") to store configuration values. The ones you'll generally be concerned with are `.gitconfig` and `.gitignore_global` which are usually in your home folder (or in `%USERPROFILE%` on Windows) and `.gitignore` which is generally found in each repository. Open these up and poke around. They're in the [INI file format](https://en.wikipedia.org/wiki/INI_file) and are quite easy to change.

## Repositories

A [Git repository](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository) is nothing more than a folder that has been initialized using `git init` and therefore contains a `.git` folder in it that contains the goodies Git needs to keep track of things. It isn't magical. It's merely a folder that has been initialized for Git. Go ahead and poke around in there. It's pretty interesting stuff!

Think of your `.git` folder as Git's database. In that database is everything Git knows about the files, branches, and history of everything. The folder that _holds_ the `.git` sub-folder? That's a single checkout from your Git database that's been put in your working folder. If you come from a centralized (or client-server) version control system like CVS or Perforce you can think of the `.git` folder as the VCS server and the folder that _contains_ the `.git` folder as your workspace. 

## Modifying, Staging, and Committing

Okay, so a version control system is all about keeping track of changes, right? Well, with Git there are [three states that a file can be in](http://code.snipcademy.com/tutorials/git/fundamentals/three-states-areas) when it comes to Git; **modified**, **staged**, and **committed**. Committed just means that the file hasn't changed. Modified means that the file has changed, but those changes have not been committed. Staged means that the file has been changed (which includes moves, deletes, and new files) and has been marked in the index to go as a part of your next commit.

### HEAD

You're going to run across the term `HEAD` fairly often when using Git. `HEAD` is simply a pointer to the last commit you made. You can [learn more here](http://www.gitguys.com/topics/head-where-are-we-where-were-we/).

### Staging

To stage changes that you've made to your working copy you use commands like `git add <filename>`, `git add *`, and `git rm <filename>`. This adds the change(s) to Git's index which means that they are staged, but not committed.

#### Add

To add staged change use `git add <filename>`, `git add *`, `git add .` `git add -A`, or [whatever variant gets the job done for you](https://git-scm.com/docs/git-add).

#### Remove

To remove a staged change use `git rm <filename>`, git rm *`, or [whatever variant gets the job done for you](https://git-scm.com/docs/git-rm).

### Viewing Status and History

To see the current state of your working copy according to Git, just type `git status`. You'll get output something like this:

```
# On branch master
# Changes to be committed:
# (use "git reset HEAD <file>..." to unstage)
#
#modified: hello.py
#
# Changes not staged for commit:
# (use "git add <file>..." to update what will be committed)
# (use "git checkout -- <file>..." to discard changes in working directory)
#
#modified: main.py
#
# Untracked files:
# (use "git add <file>..." to include in what will be committed)
#
#hello.pyc
```

It's usually a very good idea to take a look at the status before issuing a commit. That way you can make sure something doesn't sneak in. For example, without a good `.gitignore` file set up, things like debug binaries, unencrypted passwords, temp folders, and all sorts of other junk will creep in to your repository.

One thing you won't see with `git status`, however, is project history. To see that, you'll want to use `git log`. That command will let you view and filter the history of commits.

### Committing

To commit your staged changes simply use the `git commit` command. At this point, `HEAD` now points to that commit as well. If you see a message like `nothing to commit, working directory clean` then that means all your staged changes have been committed. Oh, and do yourself and everyone else a favor and add a message to each of your commit messages. All you need to do is use the `git commit -m "<your message>"` syntax.

## Branching

A branch essentially assigns a name to a particular commit and every ancestor of that commit. It's a very tiny bit of data that acts as a sort of waypoint in history. It is _not_ a completely new copy of every file. That would be silly and terribly inefficient (and exactly what a lot of version control systems do). Branches are cheap.

There are a lot of reasons to create a branch, but generally speaking you create a new branch in order to isolate changes. What you get is sort of a _virtual_ copy of everything that you can change independently. Later on you can decide to keep those changes separate, merge everything back into a single version, or scrap it altogether. You can also do what most people do on large projects and just abandon your branch leaving it to wither away and die cold and alone. On second thought, don't be that person.

## Checkout

When you want to switch branches you simply issue the `git checkout <branch-name>` command. Git will do what's necessary to update your working folder with all the right stuff. If you have uncommitted changes, Git will complain and tell you to do something with them. At that point you can commit, revert, or stash your changes.

### Branch and Immediately Checkout

Now that you know about both the `branch` and the `checkout` commands, you can use a handy shortcut for creating and immediately switching to a new branch: `git checkout -b <branch-name>`. Bingo! You're ready to go straight to work.

## Stashing

It happened again. You've been cranking away on some code when something else comes up and you need to switch to a different branch. You don't want to commit what you have because it's half-baked. You just want to set it aside so you can switch gears and then come back to it later. The answer is the `git stash` command.

Stashing puts your modified, tracked files and staged changes and saves them so you can resurrect them at any time. Stashes are stored in a list and when you want to bring your latest stash back you simply issue the `git stash apply` command. If you have multiple stashes, you can pick which ones you want to apply. You can also unapply a stash, delete a stash, and so forth, but we'll skip those features here. You can learn more about stashing [right here](https://git-scm.com/book/no-nb/v1/Git-Tools-Stashing).

## Merging

First, let's assume the following branch history:

```
      C---D---E experiment
     /
A---B---F---G master
```

Where:

- *master* is the default branch that Git created for us when we initialized the repository
- *experiment* is a branch that we created in order to try out an idea we had

When you perform the `git merge <some-other-branch-name>` command you're telling Git that you want to join two branch histories together. Git does this by "replaying" the changes that occurred on one branch after it diverged on top of another branch. Once complete Git will record the result in a new commit. The ancestry of each commit is preserved and the result would look like this:

```
      C---D---E experiment
     /         \
A---B---F---G---H master
```

Now, if the same file changed in the same place in both branches, we might end up with a merge conflict. Unless Git can auto-resolve the conflict (and often it can), it will refuse to stitch the branch histories until _you_, the human, tell Git what to do. Generally speaking, a three-way merge tool such as [P4Merge](https://www.perforce.com/product/components/perforce-visual-merge-and-diff-tools) is going to be your best friend. It will show you the file as it exists in both branches as well as the _base_ which is simply how the file was originally before each branches changes. From there you can figure out what to keep, what to throw away, and what to change. Spend some time getting to know your merge tool _before_ you really need it!

### Previewing Changes

It's usually a good idea to have a peek at what's different between two branches before you merge. To do that simply execute the `git diff <source-branch-name> <target-branch-name>` command. I won't go in to how to _read_ the diff command output (see [here](https://git-scm.com/docs/git-diff) for that), but I will tell you that setting up a [diff tool](https://git-scm.com/docs/git-difftool) is a really good idea. I recommend [P4Merge](https://www.perforce.com/product/components/perforce-visual-merge-and-diff-tools) for that task. Here's what I have in my `.gitconfig` file for that:

```
[merge]
	tool = p4merge
[mergetool "p4merge"]
	path = "C:/Program Files/Perforce/p4merge.exe"
    keepBackup = false
    trustExitCode = false
[diff]
	tool = p4merge
[push]
	default = simple
```

### Fast Forward Merges

When it comes to merges with Git, one thing we should talk about is how Git records the history. For the purposes of this discussion, we'll simplify things and assume that there are two methods; "fast forward" and "not fast forward". Here's the difference:

First, let's assume the following branch history:

```
      C---D---E experiment
     /
A---B-------- master
```

Where:

- *master* is the default branch that Git created for us when we initialized the repository
- *experiment* is a branch that we created in order to try out an idea we had

When you perform the `git merge <some-other-branch-name>` command you're telling Git that you want to join two branch histories together. If the source branch has not changed since the branch was started, by default Git will attempt to record the merge using the "fast forward" which results in linear branch history that looks like this:

```
A--B--C--D--E--F
```

However, if you perform the `git merge -no-ff <some-other-branch-name>` command (note the `-no-ff` argument), then Git will _not_ attempt to record the merge with the "fast forward" which results in an extra commit and a branch history that looks like this:

```
      C---D---E experiment
     /         \
A---B-----------F master
```

The commit at point "F" in the diagram above is the _merge_ commit. So, in short, "not fast forward" merging keeps the notion of explicit branches by adding the extra commit to the history. Alternatively, "fast forward" records the changesets in a linear fashion and in a sense ignores the fact that a branch ever existed. Whether to use fast foward merges or not can be quite a hot topic amoung Git nerds. Some people say, _"Hey, if the source never changed while the branch was being worked on then why should I clutter my history with that information?"_ Others will argue that having full history is worth the price of a little extra noise.

## Local and Remote

Up to this point, we've only been talking about things happening on _your_ computer. However, Git is a _distributed_ version control system and that allows multiple people to work on the code at the same time. Unlike a centralized VCS that usually involves a server that everyone connects to and is the only place that has all of the information about branches and so-forth, a distributed system is peer-to-peer and everyone has their own complete copy of the repository.

So what does that really mean? Well, it means that while there's always a **local** repository, there can be **remote** repositories as well. In other words:

- *local* is a version of the code that you have on your computer
- *remote* is a version of the code hosted out on the network (or Internet) somewhere

### GitHub, BitBucket, Etc.

It's easy to get confused about the role a service such as [GitHub](http://www.github.com) provides. This is particularly true if your experiences with version control have been with centralized systems like Team Foundation Server, Subversion, or CVS. At their core, all these services provide is a hosted copy of the repository, identical to the one you have on your computer, that people can sync with. You could accomplish the same basic thing with your own computer as long as everyone can connect to it from their computers. Sure, most of these services have lots of other goodies, but at their very core they're merely a commonly-accessible clone of your repository.

## Local Branches and Remote Branches

Here's a little something that trips a lot of folks up, but it's really pretty simple. Your Git repository has, for all intents and purposes, two kinds of branches: local branches and remote tracking branches. Local branches are what we've talked about so far. Nothing new there. Remote tracking branches, however, are a bit different.

### Origin

Remote tracking branches are named with a simple convention:

```
[remotename]/[branch-name]
```

By default, Git will set the remote name to `origin` when you clone a repository. Assuming you stick with Git's defaults (and you probably should for now), you'll often see `origin/master` as the "root" of a remote. Oh, you can also have more than one remote repository defined in your local repository, but we won't get in to that here.

The most important thing to remember about a remote tracking branch is that you can't modify it directly. It seems obvious when you think about it, right? So what good is it? Well, what you _usually_ do with a remote tracking branch is:

- Fetch and optionally merge the changes other people have pushed to the same remote tracking branch
- Push your local changes to the remote tracking branch
- Create new branches based on the remote tracking branch

### Checkout

Folks often get a little confused when it comes to remotes and checkout. That's generally because Git does some fancy footwork that sort of hides what's really happening. For example, if you perform a `git checkout <branch-name>` and you don't have a _local_ branch by the name you specify, but there is a _remote_ branch with the same name then Git will assume you want a new local branch tracking that remote tracking branch. Handy! Just remember you can't modify a remote tracking branch directly and what really happened is that you created a new local branch that tracks the remote.

Oh, and don't forget to `git fetch` before you issue your checkout command. Speaking of which...

### Fetching

Fetching updates your local Git database with the latest remote information. That includes new remote branches, changes to existing remote branches, and all the data necessary to bring your local working copy up to date with remote changes if you choose to do so. Fetching is safe to do when you darn well please and won't screw up anything you've got going on in your working folder.

## Pushing

When you've committed changes and you want to send those changes to the remote repository, you're going to use `git push <remote-name> <branch-name>`. Remember, if you've created a new branch it won't be available to anyone else unless you've pushed it.

### Force Pushing

Do not force push. Unless you mean ["force push" in a Star Wars context](http://starwars.wikia.com/wiki/Force_push). In that case, knock yourself out. Nerd.

### Merging

Before we go on, let's use this as our example branch diagram representing local and remote:

```
      C---D---E local
     /
A---B---F---G remote
```

Just like when you merge a branch locally, you're telling Git that you want to join two branch histories together. Just as before, the ancestry of each commit is preserved and the result would look like this:

```
      C---D---E local
     /         \
A---B---F---G---H remote
```

### Pulling

Pulling is a shortcut that's the equivalent of running `git fetch` and `git merge` back-to-back. Many folks will tell you to avoid it, however. Why? Because you're skipping the opportunity to see exactly what's about to happen beforehand.

### Rebasing

`git rebase` or `git pull --rebase`

When you rebase, Git will take the commits that exist in your local branch and re-apply them on top of the remote branch. This re-writes the ancestors of your local commits. The effect is this:

```
              C---D---E local
             /
A---B---F---G remote
```

In general, you can (optionally) rebase local changes before you push them for the first time in order to keep the history clean, but you probably _never_ want to rebase anything you've already pushed somewhere. In other words, there's nothing wrong with this:

```
$ git checkout -b newfeature --track origin/newfeature
$ touch README.md
$ git add README.md
$ git commit -am "Added a blank README file."
$ vim README.md
$ git commit -am "Added some basic layout to the README file."
$ vim README.md
$ git commit -am "Fixed a typo."
$ git rebase
$ git push
```

Just remember after that `git push` that you've made history public and changing that history is a no-no.

### Re-Writing History

When you rebase you are re-writing Git's history. Useful to be sure, but once that history is pushed to remotes that other people are using then your days of re-writing history are over. Why? Because you're not re-writing _your_ history, you're re-writing _everyone's_ history and that can lead to some pretty serious problems for people trying to do their own merging and pushing.

- You are 100% sure you know what you are doing.
- You get explicit consent to do so from everyone working on that remote.

Being loose and careless about this will get you a very bad reputation, and if you do it the consequences could range from getting kicked off the team to getting fired to getting hellbanned from touching a computer for the rest of your life.

## Pull Requests

A pull request is how you ask an upstream project to pull changes into their repository. Most often this means you're asking a project that you don't have permission to push to to incorporate changes that you've made to a _clone_ of their repository into their repository. This means that you need to first push your changes to your public repository and then request the upstream project to pull those changes into theirs. Simple!

## Forking

Let's get one thing out of the way here... [forking is a [GitHub](http://www.github.com) thing](https://help.github.com/articles/fork-a-repo/) and **not** a Git thing. Got it? Groovy. Now, that you understand that, let's talk about why forks are nice.

A fork is really nothing more than a shortcut. It's the same thing as cloning someone else's repository to your computer, making changes, then creating a [GitHub](http://www.github.com) public repository, making it a remote for your local repository, and establishing tracking between your local branch and your remote tracking branch. Forking just saves you a lot of extra work when all you probably want to do is help somebody out by fixing a bug, adding a feature, or writing some documentation.

## Summary

So there you have it! While this certainly isn't the comprehensive guide to Git, it covers the essentials. If you have further questions, here are some great resources:

- [Getting Started With Git](https://git-scm.com/book/en/v1/Getting-Started)
- [Dr. Dobb's Getting Started With Git](http://www.drdobbs.com/tools/getting-started-with-git-the-fundamental/240160261)
- [GitHub Bootcamp](https://help.github.com/categories/bootcamp/)
- [Git FAQ](http://gitfaq.org/)
