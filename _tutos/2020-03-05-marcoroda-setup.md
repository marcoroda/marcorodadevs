---
layout: post
title: marcoroda.com Setup
date: 2020-03-05
published: true
github_comments_issueid: "4"
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
To start, I installed on my machine the full [Ruby](https://jekyllrb.com/docs/installation/) development environment (Jekyll is written in Rub -> Ruby Gem). I set it all up on my Ubuntu 16.04 machine, W10 worked as fine using [WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10) and this [link](https://gorails.com/setup/windows/10#subsystem) to install ruby version > 2.4 (required).
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

## >> Theme-Console
When a new Jekyll template site is created, by default it comes with the minima theme installed. The user might freely decide to pick some other theme (and there are a lot, really). [Here](http://jekyllthemes.org/) you can check out some of them.

I picked a Jekyll template available on [Github](https://github.com/b2a3e8/jekyll-theme-console).
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

<p>&nbsp;</p>

Having the theme-console template up and running I started to customize it. For adding header content, I added the following to *_config.yml*:

<p>&nbsp;</p>
```shell
header_pages:
  - index.md
  - projects.md
  - tutos.md
  - about.md
  - contact.md
```
Note that the *index.md*, *projects.md*, etc. are markdown files on the /root directory. 
<p>&nbsp;</p>

For the footer I added the following line on *_config.yml*:

<p>&nbsp;</p>
```shell
footer: '<a href="/CV">CV</a> <a href="https://github.com/marcoroda" target="_blank">Github</a>'
```

## >> Collections
By default, when the jekyll template website is created, there is only one type of collection (_posts). Collections are a great way to group related content like projects, tutos or talks at a conference. 

### >> >> _posts Collection
If you inspect the markdown file under _posts/, you will see that at the top of the file there is the following:

<p>&nbsp;</p>
```shell
---
layout: post
title:  "Welcome to Jekyll!"
date:   2020-03-06 16:23:13 +0100
---
```
<p>&nbsp;</p>

This tells the jekyll Ruby engine the layout ('post' which is the default one), title and date. If we want the markdown files under the _post dir/ to be rendered automatically by [Liquid](https://shopify.github.io/liquid/) under a specific static page (or markdown file) we create a *projects.md* file with the following content:

<p>&nbsp;</p>
```shell
---
title: /projects        # the title of the static page
layout: home            # layout to be used
permalink: /projects    # link to the *project.md* file 
---
```
<p>&nbsp;</p>
Here we tell jekyll that for this page, go to the _layouts dir and render the code on it.

### >> >> _tutos Collection
I wanted to create another type of collection to display different content. I started byt creating a *_tutos* collection. 
To do that I added the following lines to my *_config.yml*:
<p>&nbsp;</p>
```shell
collections:
  tutos:
    output: true
```
<p>&nbsp;</p>
Then create a dir/ non the root of the website "_tutos". Add a markdown file very much like the one we have already under the _posts dir/. The following lines need to be placed on the beginning of the .md file.
<p>&nbsp;</p>
```shell
---
layout: post
title: marcoroda.com Setup
date: 2020-03-05
published: true
---
```
<p>&nbsp;</p>
Now we create a *tutos.md* under the the root dir/ and tell jekyll to render whatever is on * _layouts/tuto.html*. On that html file we have a liquid template fetching and displaying all the tutos available.

# Host on github
Github makes it very easy to host static website through [Github pages](https://pages.github.com/). Create a github repository and under settings enable Github pages, choose the branch from where the website is going to be built and press save. Set-up the git repo locally and set the remote. Finally push it to github and you are done.
<p>&nbsp;</p>
*In order to be able to run the website locally, the following line needs to be added to the Gemfile*. Comment it out when pushing to github.
<p>&nbsp;</p>
```shell
gem "jekyll-theme-console"
```
<p>&nbsp;</p>
If all goes as expecte you should have your website deployed under *https://<<your-github-username>>.github.io/<<your-website-repo-name>>/*

# Get a domain
One can buy a domain and have the website still hosted on github. I bought my domain (marcoroda.com) at [godaddy](https://uk.godaddy.com/). To let github know about my domain I have created under my website repo's root a CNAME file with the URL domain in it. Also, under the website github repo settings, you have a field where you enter the domain name.

<p align="left">
  <img width="500"  src="../../../../../assets/tuto_MarcoRoda/github_pages.png">
</p>

# Configure the DNS
To configure the DNS I used [CloudFlare](https://www.cloudflare.com/). Why do we need a DNS in the first place?

Domain Name Servers (DNS) are the Internet's equivalent of a phone book. They maintain a directory of domain names and translate them to Internet Protocol (IP) addresses. This is necessary because, although domain names are easy for people to remember, computers or machines, access websites based on IP addresses. 

## >> Account on CloudFlare
My set-up uses CloudFlare to manage the DNS. There are plenty of DNS services out there. No need to stick to this one, you can pick the one you want. CloudFlare is completely free and thhey claim to be one of the fastest to resolve the DNS name in the market. Also you can configure and buy addictional DNS servers so that if your website traffic has a peak it can handle it easily. 

## >> CloudFlare DNS managment
Being a proud owner of a domain, you can head to cloudflare and first add a website and second configure the DNS. To do so you will have to add the CNAME type. Follow this [github help](https://help.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site) article on how to do it. This usually takes some time to be effective. Be patient. 

<p align="left">
  <img width="600"  src="../../../../../assets/tuto_MarcoRoda/cloud_flare.png">
</p>

# Wrapping up
With all the above steps done, hopefully you managed to set up your own website with your own domain. Static websites are again gaining a lot of popularity. No need for server side applications, such as backend and databases. You have totally control over with no cost whatsoever, almost, you still have to pay for the domain (if you like).

# Comments
Leave a comment and/or suggestion on this post.