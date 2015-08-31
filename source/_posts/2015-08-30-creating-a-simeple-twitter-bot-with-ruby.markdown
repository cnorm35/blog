---
layout: post
title: "Creating a Simeple Twitter Bot with Ruby"
date: 2015-08-30 14:47:48 -0400
comments: true
categories:
---


Let me preface this by saying I'm not always the biggest fan of Twitter bots.  With that said, they can be useful and fun to build.  Here is a quick rundown of creating a simple Twitter bot in Ruby.



First off, you will need to have an existing Twitter account. So, if you'd like to create a new account just for the bot you'll also need a phone number.  The easiest way to take care of this is to create a new google voice number if you've already used your phone number for your primary twitter account.  Head over to https://apps.twitter.com/ to create a new app that can communicate with Twitter's API.

IMAGE/SCREEN SHOT?

It requires the app's Name, Description, and URL.  Fill out the info.  You can use something like "http://www.example.com" to get started with and update it later. Also, the Name must be unique so something like 'Test' is probably going to be taken.

Fill out the requied info and create your new app.  Once that's done you'll be taken to the Application details page.  Head over to the `Key and Access Tokens` section next.  This is where you'll find your Consumer Key and Consumer Secret Keys.  There's one more step that we need to do before we're going to be ready to go.  Scroll down to the bottom to `Token Actions` and create a new access token.  This will create the new Access Token and Access Token Secret needed to connect out bot to Twitter's API.

Now that we have all of keys and tokens situated, we're ready to write some code.

This post is meant to be a quick intro into automating actions using the Twitter gem.  It will be a single file and ran from the command line so feel free to create a Gemfile, and set up a directory structure if you like.

Let's create a directory to keep our bot files in

```$ mkdir TwitterBot```

`$ cd TwitterBot`

`$ touch bot.rb`

Now that we have a directory set up and a `bot.rb` file created, let's install the Twitter gem:

`$ gem install twitter`

Time to write some code, open the `bot.rb` we created and let's get to work.

```ruby
#!/usr/bin/env ruby

client = Twitter::REST::Client.new do |config|
  config.consumer_key        = ""
  config.consumer_secret     = ""
  config.access_token        = ""
  config.access_token_secret = ""
end

```




