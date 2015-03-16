---
layout: post_simple
title:  "Developer and Power Users Tool List for Mac"
date:   2015-03-13

tags:
- programming
- mac
- OSX
- Windows
---

Years ago [Scott Hanselman](http://www.hanselman.com) put together his [Ultimate Developer and Power Users Tool List for Windows](http://www.hanselman.com/blog/ScottHanselmans2014UltimateDeveloperAndPowerUsersToolListForWindows.aspx) and, to his credit, he's kept it up-to-date. Riffing off his list (and the lists of those that came well before), here is my own. Of course, I use a MacBook as my primary OS and run Windows in a virtual machine and SSH into an Amazon EC2 instance of CentOS Linux every day. As such, my list is a little different. Don't worry Windows fans! There's some good stuff in here for you, too.

### Life Changers

- [Parallels](https://www.parallels.com/products/desktop/) - This is by far the best virtualization software I've used. Sure, you can get VirtualBox for free and, well, VMWare probably has something, but I don't think either one can touch Parallels.
- [Alfred](http://www.alfredapp.com/) - Learning to use a launcher is essential for getting things done efficiently and Alfred is one of the most powerful and polished.
- [Homebrew](http://brew.sh/) - It bills itself as the missing package manager for OS X and it's true. It's the fastest way to get all the stuff Apple didn't provide and a LOT of other goodies, too.
- [SpiderOak](https://spideroak.com/) - Everyone has files and what you're not storing in a Git repository should probably be backup up. Think of SpiderOak as Dropbox for power users. Power users that care about security.
- [LastPass](https://lastpass.com/) - Stop using weak passwords! With LastPass, you can generate unique, high-security passwords then simply store them for later use. The browser plug-in makes filling out forms a thing of the past.

### Mac Stuff

- [Caffeine](http://lightheadsw.com/caffeine/) - This great little utility has one job: keep your Mac from going to sleep. It's awesome.
- [PopClip](http://pilotmoon.com/popclip/) - This is one of those apps that you don't realize you need, but once you do you'll be pissed that you didn't think of it and there's no Windows equivalent (that I'm aware of).
- [iTerm2](http://iterm2.com/) - Forget the built-in Terminal app and install this well-loved bad boy.
- [Pixelmator](http://www.pixelmator.com/) - Adobe should be ashamed of itself for charging so much for Photoshop. Trust me, as a long time (PAID) user of Photoshop, I think Pixelmator is all most anyone will ever need. It's a LOT cheaper, too!
- [Transmit](http://panic.com/transmit/) - Okay, paying for an FTP client seems silly when FileZilla does an amazing job for free. If you need to use an FTP client more than once a day, however, Transmit does have some really nice features and it looks great to boot.
- [Inkscape](https://inkscape.org/en/) - One beautiful thing about OS X is that you can run apps like Inkscape with no trouble at all. Forget Adobe Illustrator and fire this one up when you need to work with vector files.  Don't forget that Pixelmator has a vector mode, too!
- [Patterns](http://krillapps.com/patterns/) - Got a problem? Use regular expressions! Now you've got two problems! Okay, so when you do need to assemble or debug complex regex, Patterns is a great option.
- [Changes](http://martiancraft.com/products/changes.html) - Finding a great diff tool for OS X is surprisingly challenging (and potentially expensive). I haven't used it much, but Changes holds promise.
- [WebStorm](https://www.jetbrains.com/webstorm/) - JetBrains puts out some really nice, language-specific IDE's and WebStorm is no exception. For straight-up JavaScript work, WebStorm is a winner.

### Dotfiles!

What is a dotfile? Well, *nix systems (Linux, OS X, and so on) have a convention for files where if a file name begins with a full stop (dot or period if you prefer) then it is a hidden file. That means that you won't see it when listing files unless you specifically ask to see it. Another common convention is that program settings and customizations are stored in your home directory using one of these hidden files. For example, the ~/.vimrc file contains your personal vim preferences.

One of the many benefits of this setup is that it's easy to maintain your settings across multiple computers. In fact, it's now pretty common to create yourself a GitHub repository to keep them safe. If you're like me, you might go a step further by cloning your repository and creating symlinks to the files. Trust me, it make life much easier.

Interested? [My dotfiles can be found here](https://github.com/gregmajor/dotfiles).

### Programming Stuff

- [CodeRunner](https://coderunnerapp.com/) - Here's a fantastic application that doesn't get the exposure it deserves. It's essentially a REPL for over 20 different programming languages and it's awesome.
- [Navicat Premium Essentials](http://www.navicat.com/store/navicat-essentials) - Working with databases is much easier if you've got a great tool and Navicat fits the bill. MySql, PostgreSQL, Oracle, SQLite, SQL Server, and others are all handled with ease. Cheap? No, but good stuff.
- [Brackets](http://brackets.io/) - What?! Say it isn't so! Has Greg shunned [Sublime Text](http://www.sublimetext.com) as his go-to text editor and replaced it with an Adobe product? In short, the answer is "yes". Brackets isn't as fast as Sublime and I've only been using it for about a month at this point, but so far I dig it.
- [SourceTree](https://www.atlassian.com/software/sourcetree/overview) - I don't use it often as I usually just use Git from the command line, but it is a nice tool for when visualization is the key to understanding what's going on.
- [Firebug](http://getfirebug.com/) - If you do any real web work at all then you probably already know about Firebug. Sure, Chrome has built-in developer tools and they're pretty decent now, but Firebug is still chock full of awesome.
- [Postman](http://www.getpostman.com/) - It's a RESTful world and Postman is a great option for sending REST requests and debugging API's.

### Windows-Only Stuff

- [Chocolatey](https://chocolatey.org/) - Much like Homebrew is to OS X and apt-get, yum, and so forth are to Linux, Chocolatey is to Windows. I usually look for a Chocolatey package before I download and install something myself.
- [Beyond Compare](http://www.scootersoftware.com/) - There are seemingly hundreds of file comparison tools out there. Pick the one you like, but Beyond Compare has been my go-to for a while now.
- [ConEmu](https://code.google.com/p/conemu-maximus5/) - Every serious user looks to the command line to get things done. Of course, the built-in console and terminal emulators stink out loud. For Windows, give ConEmu a shot. Want to take it to true geek paradise? [Check this out](https://code.google.com/p/conemu-maximus5/).
- [LINQPad](http://www.linqpad.net/) - It's hard to beat LINQPad as a lightweight, LINQ-infused database browser and code notepad.
- [Git for Windows](https://msysgit.github.io/) - Git is practically synonymous with distributed version control. It's one of the first three things that I install.
- [Fiddler](http://www.telerik.com/fiddler) - Nothing beats Fiddler for debugging HTTP traffic. Like many debugging tools, it can take some effort to learn, but it's well worth your time if your serious about web development.
- [Visual Studio](https://www.visualstudio.com/) - Ah, the IDE we love and hate. Sure, it's a beast and damned expensive, but it is THE standard for .NET development. Looking for an alternative, though? Give [SharpDevelop](http://www.icsharpcode.net/OpenSource/SD/Default.aspx) a whirl. It's been around a long time and has some neat features.
- [Kaxaml](http://www.kaxaml.com/) - If you're doing any WPF work then Kaxaml is a great tool to have in your bag. Think of it as a notepad for XAML.
- [Snoop](http://snoopwpf.codeplex.com/) - If you need to dig into running XAML there's no better way to do it than with Snoop. It's a lifesaver when things just aren't working like you expect.
- [Luke](https://code.google.com/p/luke/) - Lucene.NET is an incredibly performant, open source search engine ported from the Java world. Luke is an essential tool for browsing the underlying indexes and documents as well and for troubleshooting queries.

### Visual Studio Add-Ins

- [Productivity Power Tools](https://visualstudiogallery.msdn.microsoft.com/dbcb8670-889e-4a54-a226-a48a15e4cace) - Think of this as the developer preview of new Visual Studio features. A must-have in my opinion.
- [NuGet Package Manager](https://www.nuget.org/) - You're not getting far with modern .NET development without NuGet.
- [ReSharper](https://www.jetbrains.com/resharper/) - JetBrains makes great stuff and while there are alternatives, ReSharper's tools make life a LOT easier.

### Web Stuff

- [GitHub](https://www.github.com/) - When it comes to online Git hosts, it's hard to argue that there's any more popular than GitHub.
- [GitHub Pages](https://pages.github.com/) - What do you get when you combine GitHub and [Jekyll](http://jekyllrb.com/)? You get a whole crate full of awesome! If you've got a custom domain and the GitHub Pages docs aren't quite enough to get you up and running, check out [this great guide](http://www.hongkiat.com/blog/github-with-custom-domain/).
- [Envato Market](http://market.envato.com/) - Need digital content? WordPress themes? HTML5 skeletons? How about some stock images or audio? Whatever you need, you're likely to find something on one of Envato's sub-sites such as ThemeForest or GraphicRiver. You'll feel better about paying the artist, too.

So there you have it! Hit me up on Facebook or Twitter and let me know what I'm missing!