---
layout: post_image
title: "Basic Security"
date: 2015-09-02 11:28:00
image_file: "blog/basic-security.jpg"

tags:
- security
- privacy
- infosec
---

# Overview

Let's face it, most of us don't put enough emphasis on day-to-day online privacy and security. We're just happy when we have a decent wireless connection and our favorite browser with all the bells and whistles. The unfortunate truth, however, is that we're living in a world where personal privacy and online security are serious concerns. The trouble is that most people don't know where to begin. Since you seem like a nice person so I'm going to suggest a few things you can do to make your online world just a bit safer.

NOTE: These aren't in any particular order. I employ some combination of all of these every day. I've tried to keep each one brief so that you can read them all and decide what you feel like is important.

## Disable Discovery and Sharing

Hey, when you're at home do whatever you're going to do, but when you're out and about in the big, wide world you want to get serious about protecting yourself. One of the first things to do is disable all the "network discovery" and "file and printer sharing" stuff on your computer. Do a quick search online and you're sure to find clear instructions. Leaving this stuff enabled is just asking for trouble.

## Turn Your Firewall On

Yes, it can be a pain and no, it isn't a 100% sure-fire solution, but you need to suck it up, buttercup. That firewall is one of your first lines of defense. How? Because it will inspect data flowing in and out of your network connection and, based on the rules that have been configured (and you can change), it will allow or deny that data. In other words, it can help keep the bad guys out.

While your at it, consider adding a network traffic monitoring tool such as [Little Snitch](https://www.obdev.at/products/littlesnitch/index.html) (Mac) or [GlassWire](https://www.glasswire.com/) (Windows).

## Use a Decent Browser

It should be obvious by now, but if not then I'll say it again: ditch Internet Explorer and install [Chromium](https://www.chromium.org/Home) (or [Chrome](https://www.google.com/intl/en/chrome/browser/desktop/index.html)), [Firefox](https://www.mozilla.org/en-US/firefox/new/), and/or [Tor Browser](https://www.torproject.org/projects/torbrowser.html.en). This will provide a good platform for browsing the web. Oh, and don't think I'm a Safari hater. It's just that many of the good extensions and tools haven't been made available for it yet.

## Install an Ad Blocker

There's just no good reason not to install [Adblock Plus](https://adblockplus.org/). Yes, there are alternatives such as [Disconnect](https://disconnect.me/) and [Ghostery](https://www.ghostery.com/en/our-solutions/ghostery-add-on/), but this is what I'd recommend as a baseline. It'll help block tracking, pop-ups, ads, and all sorts of crud. One thing to note, however, is that these guys can be resource hogs and _may_ slow down your browsing. On any modern computer, however, it's unlikely you'll notice much of a difference and it's worth it.

## Use a Password Manager

Using one password (even a "secure" one) for every website you visit is just really terrible idea. If it's compromised then it's not a terribly difficult task for bad guys to use it in other places, too. Most password managers are sold with the idea that you don't have to remember passwords and they'll auto-fill login forms. The true value, however, is that you can generate a unique and VERY strong password for each and every site and you'll only need to remember your master passphrase.

You've got a few great options that are very popular including [LastPass](https://lastpass.com/), [Dashlane](https://www.dashlane.com/), and [1Password](https://agilebits.com/onepassword). I've been using LastPass for years, but you can't really go wrong with any of these.

## Use Anonymous Searching

We all love Google. Well, most of us anyway. It's simply the biggest and best search engine out there. However, no matter which search engine you use you're leaving a inference trail that's just unnecessary and potentially dangerous. The solution? Use a search service that will anonymize your searches. My personal favorite? [StartPage.com](https://startpage.com/). Just head over, add it to your list of search engines, and make it your default startup page.

## Use HTTPS

One of our goals is to prevent people from sniffing our network traffic in order to see what we're sending and receiving. Fortunately, that's much easier by simply using HTTPS. When you use the HTTPS version of a site you're getting end-to-end encryption between your computer and the host. Our friends at the Elecronic Frontier Foundation have made life a little easier in this regard with their [HTTPS Everywhere](https://www.eff.org/https-everywhere) browser add-on. Don't leave localhost without it!

## Scrub Your HTTP Header Referer Data

There's a little trick that most people aren't aware of and LOTS of sites take advantage of it for fun and profit. When one site offers a link to another site there's a little extra bit of data that gets sent in what's known as the ["referer" (yes, it's mis-spelled) header](https://en.wikipedia.org/wiki/HTTP_referer). Basically, the first site tells the second site that it's the one that sent you. With a little effort someone could use your referer headers to draw a [Family Circus style map](http://www.npr.org/sections/monkeysee/2011/11/11/142218444/bil-keanes-dotted-line-an-appreciation) of your browsing.

Fortunately we can put a stop to that with browser add-ons like [Referer Control for Chrome](https://chrome.google.com/webstore/detail/referer-control/hnkcfpcejkafcihlgbojoidoihckciin) and [Referrer Control for Firefox](https://addons.mozilla.org/en-us/firefox/addon/referrer-control/).

## Go Incognito

First, head over to [Panopticlick](https://panopticlick.eff.org/) and click the "test me" button. What you'll see is what amounts to a fingerprint of your browser. That is to say it's a fingerprint of YOUR browser which is installed on YOUR computer. Web sites can use this fingerprint to track you and we don't want any of that. By simply using Chrome's "incognito" mode or Firefox's "safe mode" you can dramatically reduce the data points that can be used to track your browser. A quick search will show you how to make these modes the default on your favorite browser.

## Block Third-Party Cookies

Ugh. Cookies. They're a necessary evil on today's web. Basically, a cookie is a small bit of data put on your computer by a web server. Generally speaking, first-party cookies are reasonably okay(ish). However, third-party cookies are our concern here. Before we go further, however, let me explain this a bit more.

See. a "first-party" cookie is one that is associated with a resource that is requested from the same domain. Any cookie that is associated with a resource that is not from the same domain is a "third-party" cookie. What's important to note here is that there's no difference other than this context. A cookie is just a cookie, but depending on what domain you're accessing the context can change. This is how a "first-party" cookie can become a "third-party" cookie depending on the domain you're visiting.

The reason we want to block third-party cookies is that they rarely serve any purpose other than to track you. Fortunately, it's dead-simple to make that nasty business stop. Just do a quick search for "disable third party cookies" and the name of your preferred browser and follow the instructions. Done and done!

## Encrypt DNS Queries

The Domain Name System (DNS) has an important job. It turns domain names such as google.com into IP addresses such as 216.58.218.206. It's great and it's a big part of how the Internet works. However, there's nothing stopping that DNS server from keeping that information which means that there's a record of every site you attempt to visit. No big deal? What if I told you that most people don't realize that the default DNS server is often the one operated by their provider (hint: Comcast, AT&T, and so forth). They don't need to know where you're going, right?

I've used [OpenDNS](https://opendns.com/) for many years. They offer a nice little tool called [DNSCrypt](https://www.opendns.com/technology/dnscrypt/) that will encrypt DNS traffic more or less the same as HTTPS encrypts web traffic. It's open source, free, and another great step toward privacy and security.

## Use a VPN

A virtual private network (VPN) is essentially a private network available via a public network. It lets you use a public network like the free WiFi at your local coffee shop to connect to a private network. I won't bore you with the details of tunneling and encryption. Suffice it to say that you _really_ should be using one if you're connecting to a network that you don't have 100% control of.

Personally, I run my own VPN server, but you don't have to. There are a LOT of online services that you can sign up for such as [Private Internet Access](https://www.privateinternetaccess.com/pages/buy-vpn/), [TorGuard](https://torguard.net/), [IPVanish](https://www.ipvanish.com/?a_aid=start), and [IVPN](https://www.ivpn.net/).

## Use an SSH SOCKS Proxy

Okay, this is probably getting slightly outside the realm that most people are comfortable with, but using an SSH-enabled server you _can_ encrpyt your web traffic and keep your data from prying eyes. Basically, the idea is that your local machine will send its requests to a proxy server via SSH. This means that the traffic between you and the proxy is encrypted and therefore nobody knows what you're doing. It's a matter of connecting via SSH to a proxy server and you configure your web browser to send traffic to that proxy. From that point on you're handing off web requests to the proxy which, in turn, communicates with the Internet and the sends you the result back.

## Use Encrypted Instant Messaging Apps

Is it as convienent as Google Talk or Facebook Messenger? No. If you care about privacy, however, you should consider using an encrypted instant messaging application such as [Adium](https://adium.im/) (Mac), [Pidgin](https://www.pidgin.im/), or (my personal favorite) one of the [Open Whisper Systems clients](https://whispersystems.org/).

## Use Encrypted Email

Nobody likes the hassle of yet another email account, but when it comes to privacy we have to make tradeoffs. I keep my "trash" email which is what I use for anything I wouldn't care about being in the public domain. For my truly private email, however, I like [ProtonMail](https://protonmail.ch/). Alternatives include [SCRYPTmail](https://scryptmail.com/login) and [Tutanota](https://tutanota.com/). Be patient, however, as this is still an emergent area and most services have some pretty rough edges when compared to less secure options such as GMail and the like.

# Summary

Twenty years ago getting online was a bit of a chore. It because much easier of course, but now we're coming full circle in that it takes extra effort on our part to be secure. Most people either don't know how to keep their data private and secure their computers. Worse yet, may people simply trust that the big names on the web will do the right thing and keep them safe. This is in spite of the almost daily headlines about security breaches and data leaks as well as stories from friends and neighbors about the horrors of identity theft.

Complacency is our greatest vulnerability as an online community. The bad guys rely on the fact that most users are complacent about security and most companies tend to favor sexy new features rather than acting as responsible custodians of information. I hope these tips will get you thinking about how you use the Internet and take action to protect yourself.

Questions? Suggestions? Corrections? Hit me up!
