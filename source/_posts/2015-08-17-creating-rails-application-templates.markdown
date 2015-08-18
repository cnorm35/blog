---
layout: post
title: "Creating Rails Application Templates"
date: 2015-08-17 09:11:43 -0400
comments: true
categories:
---

Programmers are lazy, this is probably one of the greatest things about us.  Anything that takes slightly longer than we think it should and you start thinking “Hmmmmm……I wonder if I could fix that” or “I bet I could make that better".

I don’t know about you, but I’m the type that can get easily distracted by shiny new things to try out, whether it’s a new framework, gem, pattern, or fancy bourbon (I mean, we can’t program all the time).

I started looking into Rails application templates to try to alleviate these problems for me.  If I want to try out a new feature, follow along with a tutorial, or just start tinkering with a new project, it takes me a little while to get everything set up with my preferences.  Things like setting up devise, bootstrap, getting flash messages to play nicely with bootstrap and any other configs I think will help with whatever project I’m kicking off.

Why choose a template over just having a full application you can clone from github as a fresh starting point?  I think Rails templates are a much more powerful and versatile option.  Rails templates are built on Thor which is probably the best feature in Rails you’ve never heard about.  You’re probably pretty familiar with ActiveRecord, ActionController and so on.  Thor is described as

_Thor is a toolkit for building powerful command-line interfaces. It is used in Bundler, Vagrant, Rails and others._

_underscores_

(link Thor docs and jumpstart tutorial)  Every notice how you don’t have to run bundle install after you create a new rails app?  You have Thor to thank for that.

Adding in the ability to run commands and edit the files is a huge advantage.  It’s also an easy way to stick to best practices with less effort.  How?  You can do things like set up guard, r-spec, and even create a git repo and make an initial commit, all without having to write any code well, except for the template derp.

I’ll admit, I can be pretty sloppy with having tests in my personal apps.  If I’m pressed for time, I’ll normally choose cramming as many features as possible (the F-it Ship it mantra) than tests.  I think this helps combat that having my test suite all set up and ready to go

If you want the TL;DR version, you can create a new rails app from the template by running:

COMMANDS

Or you can see the entire template here: (link Github)

http://ryanswapp.com/posts/How-to-Make-a-Rails-Application-Template

Talk about using <<-TEXT, <<-CODE from Thor dsl
When inserting the last line using before (talk about before and after), talk about what the regex is doing and link rubular.

As I was working on this post, I proved my exact point.  Front-end has never been my specialty so I found myself looking up bootstrap elements and past projects to refresh myself. Also, devise flash messages don’t always work well at first with bootstrap.  Luckilty, they know have a page on the devise wiki that helps you add the helper method and get everythi running smoothly.
