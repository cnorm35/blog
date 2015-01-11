---
layout: page
title: "One Month Rails for PSL page"
date: 2015-01-11 17:02
comments: true
sharing: true
footer: true
published: true
---

I created a github repo with each branch being a different lesson in the course.

There are 2 ways to view the code for the lessons.

The first way, is the view the finished code for each lesson on Github.

{% img left /images/github_branch_screen.png 800 350 'image' 'images' %}

Click on the branch button to the left of the reposotory's name, and select the lesson you're looking for.  Once you're on the lesson branch, you can click through all the files to see the final code for the lesson.

The second way is a little more invloved, but will give you a local copy that you can view offline
and run the application on your local development enviroment.

To clone the application locally, open up your Terminal and navigate to the directory you want to clone to applicaion to (this should probably be the same directory your Pinteresting app is in)

```
$ git clone https://github.com/cnorm35/one_month_rails_psl.git
$ cd one_month_rails_psl
```

Now you have a local copy of the master branch from Github.  To see a list of the branches,
just type:
```
$ git branch -a
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
as your own version of the Pintersting application

Hopefully, this will make it a little easier to see the end results from the lessons and allow you to keep moving forward in the course.
