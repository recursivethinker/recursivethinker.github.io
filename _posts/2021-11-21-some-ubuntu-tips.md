---
layout: post
title:  "Some Ubuntu Tips & Tricks"
date:   2021-11-21 09:00:00 -0500
categories: Linux Tips Ubuntu Desktop Extensions Tweaks GNOME 
---

So recently I switched from Pop!\_OS to Ubuntu. The reason for my switch was
primarily hardware support. I purchased a Lenovo Thinkpad L13 Yoga Gen2 and I
tried installing various versions of Linux on it but was only successful with
Ubuntu. Perhaps it was because the laptop has a touchscreen and other distros
didn't have the appropriate drivers. I used this as a chance to familiarize
myself with Ubuntu and understand its pros and cons.

Having previously used Pop! and Debian I was finally trying out the distro
in-between. Here are some of the things I learned that improved my experience:

## Getting used to GNOME

Some people find it hard to adjust to the new style of GNOME, it's different
than Windows and not quite the same as a Mac, its it's own thing. And that's ok.
Just as with everything else, there is a bit of a learning curve but once you're
over the bump things get easier.

The first thing to realize is that the 'SUPER' key is your friend. If you hit
the SUPER key, it opens a view that shows all running apps and allows you to
search for anything you need. Once I got to the habit of simply hitting 'SUPER'
and just typing in the application I wanted to launch, my workflow to launch
apps has become much faster than any other Desktop Environment. This is much
better than using your mouse to click on the Applications box, and then scan
through a long list of apps to find and click the one you're looking for. GNOME
gently steers you towards using the keyboard more, and personally I good about
it.

In fact, Once you get used to hitting SUPER and typing for anything you need, a
lot of the things that people complain about GNOME start to not become concerns
anymore. For example, I don't know how to organize the Apps in my App menu by
dragging them around into groups or organizing them alphabetically or anything
like that. Because I use SUPER + start typing I really don't care about it at
all!

## Customizing the look and feel.

The default Desktop background and theme and icons that come installed with
GNOME on Ubuntu are ugly. To be honest I considered not using this distro just
for that reason. The process to customize the look and feel is also strange, and
all the options are not immediately available to see. This was a challenge.
However once I figured out what I needed to do, and was able to customize just a
few things, my experience with this desktop was improved significantly. Here's
what I did:

### Install gnome-tweaks and customize the Theme and Background.

```
sudo apt install gnome-tweaks
```

It's as simple as that. This adds a new application called 'Tweaks' that you can
open up and gives you many more options to customize the look and feel of your
desktop. [itsfoss.com](itsfoss.com) has a great
[article](https://itsfoss.com/install-switch-themes-gnome-shell/) that explains
how to do this very easily. I updated my themes to use the
[Vimix-Dark-Doder](https://www.gnome-look.org/p/1013698/) from
[gnome-look.org](gnome-look.org) and changed my background to something more
pleasing and my desktop experience just feels awesome now.

### Text sizing.

The default text sizing on Ubuntu can be a bit weird. I used the 'Scaling
factor' option unde 'Fonts' in the Tweaks tool and set the value to 1.1, this
has worked out well for me.

The above two steps should cover the basic things you need to make the Ubuntu
Desktop experience really good. However I went ahead and did a few more things
to make it better:

### gnome-shell-extensions and the browser integration.

This is the part about customizing gnome that I wish were explained better. In
addition to the 'Tweaks' tool to do more advanced customization within GNOME you
ned to install gnome-shell-extensions. 

```
sudo apt install gnome-shell-extensions
```

I don't fully understand this but basically this package 'extends the
functionality of the GNOME shell and redefines user interactions with the GNOME
desktop.' I feel that this should come by default in GNOME, but perhaps this is
still something that's considered experimental and sometime in the future will
just be a part of the GNOME DE. Once you have gnome-shell-extensions installed,
you will be able to see and control extensions using an app called 'Extensions'.

Extensions are available on the website -
[extensions.gnome.org](extensions.gnome.org). And to install these extensions
you need a browser addon for either firefox or chrome called [GNOME Shell
integration](https://addons.mozilla.org/en-US/firefox/addon/gnome-shell-integration). 

This is confusing because, why would you need a web-browser add on to customize
your desktop??? The short answer is, these extensions are created by a plethora
of developers and making it available on this website might be the easiest way
for the team behind it. The browser add-on is just a connector that downloads
these extensions and makes them available in your 'Extension' app. I feel this
whole thing could be a lot easier if the extension app itself had a menu to
search for and add/remove extensions and avoid the whole browser add-on
entirely. But what do I know!

Well, once you've wrapped your head around that tricky bit above, you're now
ready to enable any extensions you like from the
[extensions.gnome.org](extensions.gnome.org) site. Here are the ones I
recommend:

#### [Tiling-Assistant](https://extensions.gnome.org/extension/3733/tiling-assistant/)

This is a really cool extension that adds more tiling options to GNOME. You can
now tile windows to the 4 corners and also enable auto-tiling. 

#### [CPU-Power-Manager](https://extensions.gnome.org/extension/945/cpu-power-manager/)

This one allows you to set your CPU to Energy saving mode if you'd like to run
your system at low power when you're not doing intensive work and crank it up
when you need to. It also displays the current CPU frequency on the top-bar for
easy viewing.

#### [Vim Alt-Tab](https://extensions.gnome.org/extension/2212/vim-alt-tab/)

This extension allows you to use the vim keys 'hjkl' in your ALT+TAB menu to
quickly switch between apps. This is pretty neat if you're used to the vim flow.

## Conclusion

In conclusion, I think that once you're able to customize the DE just a bit, and
improve the look and feel of your desktop the Ubuntu distro really comes alive.
There's great support for a lot of applications out there on Ubuntu and with
snap packages you have the added option to install software from another
repository. For desktop users I think this is a great win and it improves your
chances of findin an app that works getting you unblocked on the things you need
to do!

Cheers!
