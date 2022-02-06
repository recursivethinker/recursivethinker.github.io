---
layout: post
title:  "Creating a blog with Jekyll and Docker"
date:   2021-08-12 13:28:25 -0500
categories: jekyll update
---

Jekyll is a cool tool to create a static website or blog using simple HTML and
markdown. Learn more about jekyll [here](https://jekyllrb.com/).

This post will cover how to setup a simple Jekyll website on your linux server
that is either self-hosted OR on a VPS using some simple commands. We will be
using Docker and Docker Compose to achieve this. If you are not familiar with
setting up either of those, please check out [Installing
Docker](https://docs.docker.com/engine/install/) and [Installing Docker
Compose](https://docs.docker.com/compose/install/).

To begin, create a directory in your home directory to store your
`docker-compose.yaml`. and then open your favorite text-editor to create the
docker-compose file.

```
user@mycomputer~$ mkdir jekyll
user@mycomputer~$ cd jekyll
user@mycomputer~/jekyll/ vim docker-compose.yaml
```

Copy the following 'docker-compose' code:

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

Now, to create the initial pages for your site, go into your jekyll folder and
type the following command:

```
user@mycomputer~/jekyll$ docker-compose run jekyll /bin/bash
```

This will give you a shell prompt inside your new docker container. Now run -

```
jekyll new --force
```

This will setup the new homepage and files, inside the jekyll directory which
you've mapped to your ~/jekyll directory using the docker-compose file above.
Once this is done, you can exit the shell and then type:

```
user@mycomputer~/jekyll$ docker-compose up -d
```

That will start the docker container and your new site should be available at
`http://localhost:4000'!!

It's that simple, now you can explore the site contents inside
`~/jekyll/\_posts/` and add new markdown files which will automatically be
published on your site. Check out [jekyllrb.com](https://jekyllrb.com) for more
ideas on how to customize and add content to your new site!

Cheers.

