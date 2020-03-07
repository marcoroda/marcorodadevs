---
layout: post
title: marcoroda.com Setup
date: 2020-03-05
published: true
---
<!-- # Add an extra blanc line 
<p>&nbsp;</p> -->

<small><i>Table of contents</i></small>
* Table of contents
{:toc}

# /brief
This page resumes the procedure I went through to set-up my theme-console website.
It includes the setting up of the jekyll static generator environment, jekyll template, host it on Github, get a domain and finally configure the DNS.

# Motivation
* Have a static website to post whatever I am working or worked on;
* To produce documentation and share it with the hackers out there;

# Jekyll
The first step is to create a static website from scratch (sort of). To do that I used [Jekyll](https://jekyllrb.com/). Jekyll is a static site generator, much like [Hugo](https://gohugo.io/) or any other available out there. You give it text written in your favorite markup language and it uses layouts (default or custom) to create a static website. It is Github pages compatible, making it a perfect candidate to start with.

## >> Environment Set-up
To start, I installed on my machine the full [Ruby](https://jekyllrb.com/docs/installation/) development environment (Jekyll is written in Rub -> Ruby Gem). I set it all up on my Ubuntu 16.04 machine, W10 worked as fine using [WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10).
Having done that, create a template jekyll site with the following instructions.
<p>&nbsp;</p>

```shell
# Install Jekyll and bundler gems
$ gem install jekyll bundler
# Create a new Jekyll site at ./myblog
$ jekyll new myWebsite
# Change into your new directory.
$ cd myWebsite
```
<p>&nbsp;</p>

The content of this folder should look like this:
<p>&nbsp;</p>
```shell
$ ls -l
total 12
-rwxrwxrwx   404.html
-rwxrwxrwx   about.md
-rwxrwxrwx   _config.yml
-rwxrwxrwx   Gemfile
-rwxrwxrwx   Gemfile.lock
-rwxrwxrwx   index.md
drwxrwxrwx   _posts
```

## >> Build and Serve it

Now, build and serve the website:
<p>&nbsp;</p>
```shell
$ jekyll serve --watch --port 8000
```
<p>&nbsp;</p>
Open your [WebBrowser](http://127.0.0.1:8000//) and you should see this:
<p align="left">
  <img width="500"  src="../../../../../assets/tuto_MarcoRoda/jekyll_1.png">
</p>
<p>&nbsp;</p>
Great, we have created a static website using Jekyll.

## Theme-Console
When a new Jekyll template site is created, by default it comes with the minima theme installed. The user might freely decide to pick some other theme (and there are a lot, really). [Here](http://jekyllthemes.org/) you can check out some of them.

I have decided to use a Jekyll template available on [Github](https://github.com/b2a3e8/jekyll-theme-console).
To install it and be able to build and serve it locally, I went through the README.me file as such:
<p>&nbsp;</p>
  1. Add the following line to your Gemfile:
  ```shell
  gem "jekyll-theme-console"
  ```
  2. Fetch and update bundled gems by running the following Bundler command:
  ```shell
  $ bundle
  ```
  3. Set theme in your project's Jekyll _config.yml file:
  ```shell
  theme: jekyll-theme-console
  ```
  4. Finally, update the theme and serve the website:
  ```shell
  $ bundle update
  $ jekyll serve --watch --port 8000
  ```
<p>&nbsp;</p>
Open the [browser](http://127.0.0.1:8000//) and verify you have the following window:
<p align="left">
  <img width="500"  src="../../../../../assets/tuto_MarcoRoda/jekyll_2.png">
</p>





