---
layout: page
title: "One Month Rails for PSL page"
date: 2015-01-11 17:02
comments: true
sharing: true
footer: true
published: true
---

I created a github repository with each branch being a different lesson in the course.

There are 2 ways to view the code for the lessons.

The first way, is the view the finished code for each lesson on Github.
You can find all the code for the course [here](https://github.com/cnorm35/one_month_rails_psl).

{% img left /images/github_branch_screen.png 800 350 'image' 'images' %}

Click on the branch button to the left of the repository's name, and select the lesson you're looking for.  Once you're on the lesson branch, you can click through all the files to see the final code for the lesson.

The second way is a little more involved, but will give you a local copy that you can view offline
and run the application on your local development environment.

To clone the application locally, open up your Terminal and navigate to the directory you want to clone to application to (this should probably be the same directory your Pinteresting app is in)

```
$ git clone https://github.com/cnorm35/one_month_rails_psl.git
$ cd one_month_rails_psl
```

Now you have a local copy of the master branch from Github.  To see a list of the branches,
just type:
```
$ git branch -a
```

Here is the current list of all the branches.  I'll update this with the full list of branches once 
I have a chance to work through all the lessons (hopefully by the end of the week)

```
add_bootstrap_elements_to_pages
  adding_icons
  adding_names_to_users
  adding_validations
  authorization
  changing_the_root_route
  creating_a_page_for_one_pin
  creating_more_pages
  creating_navigation_links
  creating_your_homepage
  customizing_bootstrap
  design_improvements
  fixing_a_bug
  generate_pins_scaffold
  generating_users
  going_online_with_heroku
  image_upload_with_paperclip
  installing_devise
  installing_the_bootstrap_gem
* master
  new_user_signup
  ordering_pins
  pagination
  paperclip_to_amazon_s3
  pins_controller
  pins_users_and_associations
  pins_views
  replacing_emails_with_names
  setting_the_root_path_with_routes
  setting_up_devise
  styling_with_jquery_masonry
  twerking_devise_views
  what_is_embedded_ruby
```

When you have a branch(one of the lessons) you would like to checkout just type

```
$ git checkout origin/name_of_the_lesson
```

For example, if you wanted to check out the Customizing Bootstrap lesson, it would be:

```
$ git checkout origin/customizing_bootstrap
```

If you'd like to view the Pinteresting application in your browser, navigate to the directory 
and run
```
$ rails server
```

If you check the results of starting the rails server, you'll see that it's running on a different port instead of the standard localhost:3000.  You should be able to view the example app on localhost:8080.

This way, you can have this example application running and open in your browser at the same time
as your own version of the Pintersting application.

If you're having problems getting the example application to run, check out the [documentation](https://github.com/cnorm35/one_month_rails_psl) on the github page for some extra info.

Hopefully, this will make it a little easier to see the end results from the lessons and allow you to keep moving forward in the course.

Once your finished with the One Month Rails course, I highly recommend checking out the [Rails Tutorial](http://railstutorial.org/book) from Michael Hartl.  He takes you through the process of building a twitter clone step-by-step.  There is also a nice introduction to getting started with testing.
