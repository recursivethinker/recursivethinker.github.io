---
layout: post
title:  "Linux Reinstall"
date:   2021-06-05 10:10:41 -0500
categories: Linux Tips Bash Terminal 
---

So I've been messing around with the Dell XPS all day. I still can't believe
this computer is nearly 15 years old, or actually even older than that. I went
out and bought a new hard disk to insert into this, and did quick Debian
reinstall. 

I love having Debian on a keyring, it's now my most favorite distro to install.
I think I like it because it's pretty basic and doesn't come with a lot of
bloat. I also like that you can set it up to run with XFCE out of the box and
it takes up barely any ram on the system.

The drawback is of course that it doesn't come with proprietary drivers needed
for things like Wifi and the GPU. I always have to figure out some way of
tethering the computer to the LAN network while I download non-free drivers for
Wifi and configure them.

I also noticed that on the Dell XPS M1210, the computer is so old that nvidia
drivers for this are not available on Debian Stretch. It's using nouveau
drivers by default. So far, they seem to be working well so I don't see any
problems.

I love the XFCE desktop once I learned to customize it a bit. Here are the main
changes I made (thanks to the Youtube video that I watched today to help me out
with this.)

* The first thing to do is usually to get rid of the bottom panel Simply open
  Panel preferences and remove it.
* The second thing is to customize the top panel, remove the default
  'Applications' menu and add something called 'Whisker menu' this is a much
more stylized Start menu like option and works a lot better.
* Then, optionally move the panel to the bottom of the desktop for a more
  'windows-like' feel.
	* I generally like gnome better than the KDE / Windows feel, however my
	  workflow is mostly keyboard based now and I find it easy to launch
apps by summoning things with the super-key and simply typing out the app I
want. For a mouse workflow, I think the Windows approach is a lot better.
* The third thing to do is customize the "Appearance" AND "Window manager"
  settings. This was the secret sauce I was missing. I didn't realize that in
XFCE to get a consistent look and feel throughout the desktop you need to setup
the same theme in both 'Appearance' AND 'Window Manager' as they both take care
of slightly different things.
	* The default debian packages don't come with a lot of cool themes
	  afaict.  However I did manage to find that it has the 'Materia' gtk
theme and also the 'Papirus' icon theme.

I installed both of these easily by typing: ``` sudo apt search 'materia' sudo
apt search papirus ```

and you get the idea..

* With that the only thing left to do is to install
  'lightdm-gtk-greeter-settings'. This package allows you to configure the
lightdm settings using the GUI which is much nicer, and with that you can
pretty much customize everything.

I went with Dejavu-Sans fonts throughout the system, it gives it a nice classy
feel. And everything looks fantastic!

Mozilla Firefox is my default browser, I have a few customizations I do with
that as well, but once that's done. It's all smooth sailing.

Well, this turned out to be a bit of a longer rant than I expected. So I'll
sign off here now. 
