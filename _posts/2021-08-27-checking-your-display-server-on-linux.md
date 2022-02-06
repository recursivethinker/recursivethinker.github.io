---
layout: post
title:  "Checking your Display Server on Linux"
date:   2021-08-27 09:00:00 -0500
categories: Linux Tips Bash Terminal 
---

A display server on linux controls how windows are displayed on your monitor. It
is used by your Desktop Environment (such as GNOME, KDE or XFCE) to render
everything on your screen. The most popular display server used on linux is X or
X11. However this is quite old and a new display server has been making the
rounds. This new display server is called "Wayland" and has some advantages over
the older system. However, it is yet to be fully widely adopted and as a result,
there is a chance that the machine you ar running is still using X11 instead of
Wayaland. 

So how can you figure this out?

I found this cool [forum post](https://unix.stackexchange.com/questions/202891/how-to-know-whether-wayland-or-x11-is-being-used) that has the answer! 

Basically what you want to do is this,

First find your session id by running:

```
$ loginctl
```

This should give you an output that looks like:

```
SESSION  UID USER 	SEAT  TTY 
      2 1000 username   seat0 tty2
```

Now type:

```
$ loginctl show-session <SESSION_ID> -p Type
```

And this should out put either ```Type=X11``` or ```Type=Wayland```. 

And that's it! for a more detailed list of attributes about your session, you
could try:

```
$ loginctl show-session <SESSION_ID>
```

Cheers!
