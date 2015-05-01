---
layout: post_simple
title:  "Fixing OSX VPN Woes"
date:   2015-04-30

tags:
- osx
- vpn
- home server
---

So you're setting up a VPN server and it's all going very smooth *except* for when you actually try to connect. You check the server logs and notice something like this:

```
Thu Apr 30 19:54:11 2015 : CHAP peer authentication failed for awesomeuser
Thu Apr 30 19:54:11 2015 : sent [LCP TermReq id=0x2 "Authentication failed"]
```

Frustrating? Yes! I spent at least an hour with Google trying to find an answer. A task that's made even more difficult by the fact that Apple likes to change their server app substantially with nearly every new version of OSX.

Now, I can't guarantee that your problem is the same as mine was, but it can't hurt to check. Open your server app and go to the "Users" tab. Open the properties of the user that you're trying to connect as and look for a message like this:

> This user is using an iCloud password for authentication and will not be able to access some services.

If you see that message then that account is not going to be able to authenticate to your VPN. The solution? Just change that user's password. It can even be the very same password they had before. The warning message should go away and hopefully you'll be all set. This applies to OSX Yosemite, but there are similar issues with Mavericks and Mountain Lion. For example, with Mountai Lion you had to be careful to create the user as a network user versus a local user.

The server app is certainly cheap and it's a nice, quick way to get things up and running. Fortunately, Apple made the choice to stick with pretty standard stuff in most cases (Bind9 and whatnot). However, this is certainly an area that could have used a little more attention. At the very least, tell the admin *what* services the user wouldn't be able to access.

I hope this helps you out!
