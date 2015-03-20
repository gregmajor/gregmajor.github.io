---
layout: post_simple
title:  "Getting GitHub Pages Code Highlighting To Work"
date:   2015-03-20

tags:
- blogging
- GitHub Pages
---

If you're a programmer (or at least comfortable with markdown and Git) and you've not checked out [GitHub Pages](https://pages.github.com/) you should. It's a free blogging platform that leverages [Jeykll](http://jekyllrb.com/) to serve static sites written in HTML and Markdown that you push to GitHub. In other words, it's a great option for programmers because it uses ubiquitous technologies and a comfortable workflow.

The only significant challenge that I've had with GitHub Pages and Jeykll was getting code highlighting to work. I tried dozens of combinations, but nothing seemed to click. Finally, I got it to work and I wanted to share the magic combination with you now.

## The Configuration

First, here's what my **_config.yml** file looks like:

```yaml
name: "My Blog"
description: ""
url: "http://myblog.com"

paginate: 4
paginate_path: "page:num"

markdown: redcarpet
permalink: pretty
highlighter: pygments

syntax-highlighting:
  enabled : true
  css: syntax.css
```

Of course, your config will be different, but the important bits are using **redcarpet** for the markdown engine and **pygments** as the highlighter. Honestly, I'm not sure if the syntax-highlighting section is necessary and I've been too lazy to test it.

## The Post Markdown

When you construct your posts, use [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/) syntax and pay particular attention to the code fencing section. Also, refer to [Pygments](http://pygments.org/) to find lexers that can make your code all pretty and stuff.

## Working Locally

In order to get all this working locally, you'll need to make sure you have Python installed and use pip to install Pygments. For a nice walk-through you can [go here](http://jekyll-windows.juthilo.com/3-syntax-highlighting/). Myself, I use [Chocolatey](https://chocolatey.org/) to install Python.

## Summary

Reading this now it may seem obvious, but the confusion between Pygments and Rouge, the various markdown engines, and the markdown syntax itself makes it less than intuitive. I certainly hope that this nudges someone else in the right direction if they're having problems getting code highlighting to work with GitHub Pages!
