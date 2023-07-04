---
title: "How this all started..."
date: 2022-10-09T21:58:50-07:00
author: ["D.Moreno"]
description: "'How to build a blog' as this blog's first blog post"
tags: [
  "Project",
  "Blog Build",
]
# Page parameters
draft: false # until false then posted to production
ShowToc: true
ShowBreadCrumbs: true

## including a cover image
# cover:
#   image: "<image path/url>"   # as static content
#   image: https://i.ibb.co/K0HVPBd/paper-mod-profilemode.png  # as a url
#   alt: "<alt text>"
#   caption: "<text>"
---


In this inaugural post I walk through the decision making that informed the design of this site (which tools and technologies I used), and the steps to set it all up.

<!--more-->


# 📌 TL;DR

This site is
* hosted on [Firebase](https://firebase.google.com/)
* created using [Hugo](https://gohugo.io/)
* has a custom domain purchased on [Google Domains](https://domains.google/)
* Built following <a href="{{< relref "blog/how_this_all_started.md#build_walkthrough" >}}">these steps</a>


## Lessons / Key takeaways

<table>
  <tr>
   <td>
<strong><h3>Start projects with a goal, list of requirements and constraints. Then consider the options before starting on any work.</h3></strong>
   </td>
   <td>
<ul>

<li>I knew I wanted to set up my own site, because I’ve been wanting to learn the basics of front end dev and have a space to play around in

<li>At first, I started using Octopress for content generation then double backed to research alternatives before landing on Hugo. <strong><em>If I had researched first, I would have saved some time</em></strong>.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong><h3>This site is hosted on <a href="https://firebase.google.com/">Firebase</a></h3></strong>
   </td>
   <td>
<ul>

<li>It has a free tier with plenty of headroom before I hit any price point

<li>Offers a nice runway to grow the site beyond static content, with serverless backends and plenty of plugins to try in the future

<li>For custom domains purchased on Google Domains, the ‘ownership check’ is skipped which saves time and implementation complexity
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong><h3>The content is generated using <a href="https://gohugo.io/">Hugo</a></h3></strong>
   </td>
   <td>
<ul>

<li>Hugo has an active community (reddit, discord, and thorough <a href="https://gohugo.io/">documentation</a>) which is reassuring for a FE beginner

<li>It’s written in Go, which is also something on my #ToLearn list
</li>
</ul>
   </td>
  </tr>
</table>


# Planning the build

I followed these steps to get this site up:

1. Start with a goal, and list of requirements and constraints
2. Generate the site content
3. Find a host and custom domain


## First: Goals, requirements, and constraints

**TL;DR** If you want to focus on writing, there is no need to set up your own site. Go with Medium, which is the best free-to-post site IMO.

I had intended to learn some FE basics + start writing this year. Setting up this blog allowed me to peel two potatoes at the same time (cruelty free figures of speech only on this site :bird: :bird:)


### Goals



1. Find a place to host my writing
2. Learn HTML, Javascript, and CSS basics
3. Host in a place that allows me to link to github projects
    1. Stretch: Run code from the site itself


### Non-goals



* Build a dynamic site (...yet) / build anything that would necessitate a database


### Requirements



* I’m new to front end development, so I need something that comes with a framework I can tinker with as opposed to building something from scratch
    * The framework should come with an active community so that I can find support as needed
* I am not interested in opening my home network to the internet, so I’d like to host on a third party platform
    * Preferably a free-to-host platform


### Constraints



* **Time:** My primary goal is to have a place to write, but my secondary goal is having a sandbox to explore and configure a site. A tension arises here as the tinkering pulls time out of writing, and vice versa.


## Second, generate the content

**TL;DR** I chose [Hugo](https://gohugo.io/) because it had the most active community for support and it’s written in Go which is a language I wanted to pick up anyway.

I went on the hunt for static content generators, which are tools to create the html, css, and javascript that would become my site. In doing so, I found a new requirement that the site be tolerable aesthetically so a generator with an active community and support for themes was added to my list from the _requirements_ step.

I found this great list of [site generators](https://myles.github.io/awesome-static-generators/), from there I narrowed down to a few options based on the technologies used as well as the communities supporting the tooling:


<table>
  <tr>
  <td><strong>Site Content Options</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Comments</strong>
   </td>
  </tr>
  <tr>
   <td><a href="https://www.11ty.dev/">Eleventy</a>
   </td>
   <td>Open sourced Javascript static site generator
   </td>
   <td>
<ul>

<li>Handles incremental builds

<li>Has an active Git, good documentation, and active Discord

<li>Many actively maintained plugins

<li>Requires a bit more setup for hosting on GitHub Pages & Firebase (Anecdotally)
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><a href="https://nextjs.org/">Next.js</a>
   </td>
   <td>Minimalist Jamstack framework using Javascript, typescript, and rust.
<p>
Objective is to build scalable React web apps (static, dynamic)
   </td>
   <td>
<ul>

<li>Good community, popular modern framework

<li>Lack of native themes

<li>Lacks plugins (e.g. 'read time' was a feature I was after on my site)

<li>Steep learning curve compared to plug and play generators
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><a href="https://gohugo.io/about/what-is-hugo/">Hugo</a>
   </td>
   <td>Written in Go
<p>
General purpose static site framework
   </td>
   <td>
<ul>

<li>Handles incremental builds

<li>Fastest builder (thanks Go!)

<li>Limited plugins

<li>Many community supported themes

<li>Steep learning curve to create new themes (thanks Go :frown:) but many themes already to choose from.
</li>
</ul>
   </td>
  </tr>
</table>


I went with Hugo, because it offered a quick setup with plenty of room for tinkering after the initialization. It’s also written in Go which makes site building fast for quick prototyping down the road.


## Third, finding a host

**TL;DR** I went with Firebase which offers trivial custom domain setup along with a free tier that offers plenty of headroom for the traffic and site content I plan to create.

I considered the following for hosting - I initially published to GitHub Pages; which seemingly offered the fastest time-to-deployment since my source was in a public repo anyway, but switched to Firebase after configuring my custom domain. Firebase, I found, offered the most runway for continued development beyond static content only (no concrete plans here, but the optionality is valuable).


<table>
  <tr>
   <td><strong>Host Options</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Comments</strong>
   </td>
  </tr>
  <tr>
   <td><a href="https://www.netlify.com/">Netlify</a>
   </td>
   <td>Serverless Jamstack platform. Free tier up to 300 build minutes per month.
   </td>
   <td>
<ul>

<li>Support for web dev CI/CD

<li>Many 3P service APIs

<li>1-click roll backs
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td>Github Pages
   </td>
   <td>Git repo hosting service that may run the files through a jekyll build process.
<p>
Soft build limit (10/hour), and site size (1gb served, 100gb bandwidth)
   </td>
   <td>
<ul>

<li>Git provided cert :lock:

<li>Zero-config build
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><a href="https://firebase.google.com/">Firebase</a>
   </td>
   <td>App and rich site development platform, offers automated backend services and a suite of features for release and app measurement. Has a free tier also
   </td>
   <td>
<ul>

<li>Zero-config SSL certs :lock:

<li>Trivial setup for real-time backend

<li>1-click roll backs

<li>GCP backed for serving at scale (GCP comes with $300 new acct credits)

<li>Impressive open-sourced bundled features
</li>
</ul>
   </td>
  </tr>
</table>


> NOTE: Not an exhaustive list, see more [complete list here](https://geekflare.com/best-static-site-hosting-platform/).


## Finally, getting a neat custom domain

Pricing was a wash and there is no differentiator in the product offering itself (no matter the seller, you’re getting the same domain!) I went with [Google Domains](https://domains.google/) because when adding the custom domain in Firebase, if purchased from Google Domains then the ownership proof is done automatically which will save some time and implementation compleixty.

> NOTE: GitHub Pages threw an error when I tried to reconfigure the build to my custom domain, so I chose to relocate my site to Firebase at this point.


# Building it {#build_walkthrough}

I will skip steps for hosting on GitHub Pages, which can otherwise [be found here](https://docs.github.com/en/pages/quickstart), and provide the steps I followed to host on Firebase (including setting up my custom domain name on Google Domains)

Prerequisites: Git, Hugo, and Node.js


```
brew install git
brew install hugo
brew install node
```


Setup a Github repo for the site



1. Create a repo with the naming convention [username].github.io
    * I left “main” as the source for Hugo build and created a separate branch for the site called <code>[gh-pages](https://github.com/morendav/morendav.github.io/tree/gh-pages)</code>

    > NOTE: this was initially for the github pages deployment, but I kept the naming convention.


2. Clone the github repo locally.
    * you’ll want to be working locally from the <code>main</code> branch

3. Initialize Hugo in your cloned repo.

```
hugo new site [username].github.io/
cd [username].github.io/
```


4. Picking a theme requires downloading & updating the config file. I am using [PaperMod](https://themes.gohugo.io/themes/hugo-papermod/)

    > NOTE: PaperMod instructions use a YAML based Hugo build but I kept TOML. You can find YAML → TOML translators online. A sample YAML config for PaperMod [is here](https://github.com/adityatelange/hugo-PaperMod/blob/exampleSite/config.yml)


```
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
```


5. configure only the contents of ./public/* (the built site) to push to the  <code>[gh-pages](https://github.com/morendav/morendav.github.io/tree/gh-pages)</code> branch

```
mkdir .github/ .github/workflows
touch .github/workflows/
```



Add the following content to that file:


```
name: github pages

on:
  push:
    branches:
      - main  # Set a branch to deploy
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          # extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: github.ref == 'refs/heads/main'
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```


Now, the local working copy is ready for prototyping!

Create a new post and view it locally to test Hugo and your new theme.


```
hugo new posts/HelloWorld.md
echo "Hello World!" >> posts/HelloWorld.md
hugo server -D
```


> Pro-Tip: you can draft content in Google Docs, then use a Markdown converter extension called “[Docs to Markdown](https://workspace.google.com/u/0/marketplace/app/docs_to_markdown/700168918607)”. Otherwise working from and IDE does the trick also.


### Setting up a custom domain for Firebase project



1. Create a Firebase project for the site
2. Purchase an available domain, let’s say **somenamehere.com/**
3. Add custom domain to Firebase hosting
    1. In Firebase project console, select Hosting from left nav menu
    2. Under the project domains, select “Add custom domains”
    3. Add an entry for **[www.somenamehere.com](http://www.somenamehere.com)**
    4. Add an entry for **somenamehere.com**, select “redirect to an existing website” and redirect to **[www.somenamehere.com](http://www.somenamehere.com)**
    5. Note the IP addresses assigned at these steps, as well as the record types (e.g. “A”)



{{< figure
  src="/images/posts/how_this_all_started/firebase.png#center"
  title="Firebase Hosting"
  caption="Adding custom domain to Firebase hosting"
  link="/images/posts/how_this_all_started/firebase.png"
  target="_blank"
  class="align-center"
>}}



4. Register DNS, return to Google Domains
    1. From Google Domains console, select DNS from left nav menu
    2. Under “Custom Records” select “Manage custom records”
    3. Enter in the custom domain **somenamehere.com** and **[www.somenamehere.com](http://www.somenamehere.com)** here along with the noted IP addresses and the record types.

{{< figure
  src="/images/posts/how_this_all_started/domains.png#center"
  title="Google Domains"
  caption="Updating DNS Register"
  link="/images/posts/how_this_all_started/domains.png" 
  target="_blank"
  class="align-center"
>}}






### Initializing Firebase and deploying the site

1. Initialize Firebase at the root blog directory, in this example it’s been [username].github.io

```
npm install -g firebase-tools
firebase login # will be prompted for firebase login in browser
firebase init
```



In addition to the selections [noted here](https://gohugo.io/hosting-and-deployment/hosting-on-firebase/#initial-setup),
* select gh-pages as the source for the site during setup

Now, the site can be deployed :rocket:

```
hugo && firebase deploy
```

Don't forget to push your built site to Git  :floppy_disk:
