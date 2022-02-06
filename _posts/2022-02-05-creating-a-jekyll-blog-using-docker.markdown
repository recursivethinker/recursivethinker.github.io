---
layout: post
title:  "Creating a Jekyll blog using docker"
date:  Sun 06 Feb 2022 01:15:15 AM PST
categories: jekyll update
---
# Deploying a Jekyll blog using docker.

[Jekyll](https://jekyllrb.com) is a static website generator that can be used to
generate websites from markdown. It's a great tool for folks that like to write
blogs in markdown and have a quick and easy way to publish it on the web. One of
the popular blogging platforms [GitHub Pages](https://pages.github.com/) is
powered by Jekyll.

[Docker](https://docs.docker.com/get-started/overview/) is a platform to build
and deploy "containerized" software. A docker container packages everything you
need to run a piece of software and abstracts away the challenging aspects of
configuring your computer, it almost works like a mini-vm on your server that
runs the application you want.

Docker is used to containarize practicaly everything, and luckily enough there
is a [Docker container](https://hub.docker.com/r/jekyll/jekyll) available for Jekyll!

In this post I will outline how you can use the Jekyll docker container to
create a blog and deploy it on a server. For starters, this will all be on your
local machine, I will cover how to set it up on a remote server in a future
post.

## Pre-requisistes

I assume here that you have already [installed-docker](https://docs.docker.com/engine/install/) on your computer and that you
have [docker-compose](https://docs.docker.com/compose/install/) setup.

## Create a docker-compose file for jekyll

I found this excellent
[blog](https://matthiaslischka.at/2018/12/22/jekyll-docker-compose/) by Matthias Lischka that had a sample docker-compose
which I will use here:

```
version: '3'

services:
  jekyll:
      image: jekyll/jekyll:latest
	  command: jekyll serve --watch --force_polling --verbose
	  ports:
		- 4000:4000
	  volumes:
		- .:/srv/jekyll
```
I should also mention this
[blog](https://ddewaele.github.io/running-jekyll-in-docker/) by David De Waele that helpmed me troubleshoot
at places I got stuck.

## Run docker-compose up -d

Once you have the docker-compose.yaml file created, simply run `docker-compose
up -d` to spin up your container. You will notice at this point that the
directory you mapped to /srv/jekyll in the compose file will now contain a _site
folder.

At this point, your container has been created and within that container the
command `jekyll serve` is telling it to serve pages in the /srv/jekyll directory
as a website and it created the `_site` folder.

## Create your blog and build it

You need to run the commands `jekyll new <PATH>` and `jekyll build` to really
create the blog in this container with all the styles and extra folders you
need. In order to do that you must first get a shell prompt inside your docker
container. 

Run:
```
$ docker container exec -it jekyll /bin/bash
```

Replce jekyll with whatever you named your container if you need to. This should
give you a prompt inside the container, now run:

```
# jekyll new . --force
```

This will create the scaffolding for your blog in the /srv/jekyll directory,
which should be where your prompt is after you run the previous step.

Now if you try `ls` you'll see some new file inside the directory such as a
`_config.yml` file and a `Gemfile`. These will come into play later. For now,
just run

```
# jekyll build
```

This will build the _site again.

Now you can exit the shell inside the container and if you go to
`http://localhost:4000` on your machine you should be able to see your blog up
and running!!

## Conclusion

And there it is, a quick way to get your jekyll site set up. You will want to
read the instructions in your index.html page that was generated to get more
tips on how to customize your site.

In a future post I will outline how to change your theme and deploy your blog on
a server somewhere.

Cheers.
