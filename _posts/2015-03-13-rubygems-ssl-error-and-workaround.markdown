---
layout: post_simple
title: "RubyGems SSL Error and Workaround"
date: 2015-03-13

tags:
- Ruby
- SSL
---

Yesterday I ran into a little problem after installing Ruby and RubyDev via Chocolatey on my Windows virtual machine. Here's the command that was giving me trouble:

```
C:\Users\Greg>gem install bundler
```

Which returned this error:

```
ERROR:  Could not find a valid gem 'bundler' (>= 0), here is why:
          Unable to download data from https://rubygems.org/ - SSL_connect returned=1 er
=0 state=SSLv3 read server certificate B: certificate verify failed (https://api.rubygem
rg/latest_specs.4.8.gz)
```

So after a little research (Google), I found [this tidbit](https://gist.github.com/luislavena/f064211759ee0f806c88) which fixed me right up. Hope it helps you, too!
