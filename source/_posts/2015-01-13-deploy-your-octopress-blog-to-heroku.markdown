---
layout: post
title: "Deploy your Octopress blog to Heroku"
date: 2015-01-13 18:08:38 -0500
comments: true
categories: octopress, heroku
---

This post will walk you through setting up a new blog with the Octopress blogging framework
and deploy to Heroku.

So first off, what exactly italics IS Octopress.  Octopress is billed as a blogging framework for hackers.  It's a little different that some of the other blogging frameworks you may have had some experience with.

The first is it's built with Ruby.  The second, is there is no database.  You create your posts using the markdown language and Ruby (and Octopress) generates static HTML pages.  This make it pretty easy to set up and very fast since everything is a static page.

To get started, fire up your command line and clone a copy of the Octopress repository.

```
$ git clone git://github.com/imathis/octopress.git my_blog
```
Next, navigate into the folder that was created when you cloned the Octopress code.

```
$ cd my_blog
```

Since Octopress is built off Ruby, lets check the current version of Ruby installed.

```
$ ruby -v
```

If it's not at least `ruby 1.9.3` check out the documentation to upgrading your ruby version with RVM [here](http://octopress.org/docs/setup/rvm/)

So now, lets install the gems 

```
$ gem install bundler
$ bundle install
$ rake install
```
At this point, you should be able to see the basic template for your site.  Running 
```
$ rake preview
```
will generate the required files for you site and start a simple web server.  Check out localhost:4000 to see if your site is up and running.  It should look something like this

{% img left /images/Octopress_Screenshot.png 800 350 'image' 'images' %}

Now we need to remove `public` and `Gemfile.lock` from our `.gitignore` file.  We'll need this to add generated content to Heroku.

Once that's take care of, let's head to `_config.yml` and start customizing the settings

Main settings:
```
url: http://www.codebycodes.com
title: Code by Codes
subtitle: "Codes, rants and musings"
author: Cody Norman
```
If you'd like to connect some of your external accounts, scroll down and check out some of the 3rd party services you can connect.