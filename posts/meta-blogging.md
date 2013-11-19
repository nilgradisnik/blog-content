---
title: "Meta blogging"
author: "Nil Gradisnik"
date: "10-25-2013"
draft: false
tags: ["news"]
---

Let me show you a quick experiment on how to create a simple personal blogging platform. This is an exercise in how geeky you can get with setting up a blog and how many shortcuts you can take to avoid building your own blogging engine, database and [CMS](http://en.wikipedia.org/wiki/Content_management_system). You just want to share a few words with the world, you don't want to work for it too hard, but you still want to build it yourself.

<!--more-->

## Prerequisites
So you know Javascript right? You're familiar with git(Github is your favorite website doh) and you've heard of Markdown for sure. Let's take these three things and setup a simple blog.

There's this odd thing called [Nodejs](nodejs.org). You install it, write a few lines of Javascript code and you have yourself a working web server. You know Javascript and all of a sudden you can do server side programming? Weird. In our case we'll need a few libraries that will come in handy like [Expressjs](expressjs.com) and [Poet](http://jsantell.github.io/poet/) which does most of our blogging engine work.

We'll also need a place to deploy our new blog. I heard that [DigitalOcean](https://www.digitalocean.com/) has some pretty fast servers over there, you might want to check that out.

And that's pretty much all we need. Now it's just a matter of gluing things together.

## Fork me
This [blog-experiment](https://github.com/nilgradisnik/blog-experiment) repo is where you start. You'll need to fork it and clone it to your server machine where Nodejs is waiting to server your blog.

We will also need another repository where the content(blog posts) will be held. Head over to [blog-experiment-content](https://github.com/nilgradisnik/blog-experiment-content) and fork this one as well. This repo will be used as a git submodule of the parent blog-experiment, so you will need to correct the path inside .gitmodules file to point to your forked blog-experiment-content repo otherwise you'll just see my blog content. This probably sounds oddly complicated by now... it probably is but bare with me.

## What's a Webhook?
It's a nifty feaure provided by Github which basically fires a POST request to a defined URL(which will be your server) every time someone commits to git repo. Let's set it up for our content repo, because that's where we want our Webhook to fire so that every time we make some changes(create a new blog post, edit an existing one) the webserver will be notified of that change. If you go to repo Settings you'll find a Service Hooks menu on the left side and the first item on the list is WebHook URLs. Let's add a URL that points to our server with an URI that our server understands. You'll find this can be set inside config.json file of the blog-experiment repo.

Wait, does that mean we're using Github as your blogging CMS? That is correct. Github has a nice online editor that lets you create and edit files inside your repo. Why not take advantage of that.


## Run the server
Once you're done scratching your head installing all the npm dependencies and checking out the git submodule, you are ready to run your web server.

## Writing
Head over to Github and go to your blog-experiment-content repo. In the posts folder you can start creating new Markdown files aka blog posts. Commit the changes and bam! you should be able to see new blog posts.

Yes it's that simple. Not really... It's actually not that simple at all. But it was a fun experiment. And this blog post that you're reading right now is setup this way. Neat.
