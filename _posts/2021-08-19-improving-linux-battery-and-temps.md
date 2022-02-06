---
layout: post
title:  "Improving Linux laptop battery and temperature"
date:   2021-08-19 09:00:00 -0500
categories: Linux Tips Bash Terminal 
---

Linux is a great OS to run on older hardware and can be used to breathe new life
into an older machine. I'm writing this post on a Dell XPS M1210, a high-end
laptop that came out around 15 years ago! Although modern operating systems like
Windows 10 and MacOS won't run on this anymore and versions that could are not
supported by security updates. I am able to continue using this laptop by
running a lightweight install of Debian Linux using the XFCE desktop
environment. 

One of the problems that I ran into though was that the laptop was over-heating.
Upon checking the thermals I observed that core temperatures were getting up to
75C and the GPU was climbing into the 80s and 90s. The laptop was certainly not
comfortable to use on my lap.

The first thing I did was open up the laptop and clean the heatsink and apply
fresh thermal paste. This mitigated the issue somewhat. I also cleaned out the
fan (which was still working great after 15 years!) and this did improve the
airflow overall. I was still only able to get the core temps down to 60-65C and
GPU down to 70-75C, the laptop was still hot on my lap.

That's when I started looking into power and cpu temperature managing packages
on Linux, and lo and behold I found some really cool ones!

### TLP

The first one I came across seems to be a pretty popular package that has been
around for ages, even though I was just discovering it. This was
[TLP](https://linrunner.de/tlp/). 

TLP is not an acronym, and is simply a 3 letter name. It's a pure command line
utility that is easy to install and once its installed will automatically run
when your system reboots. The website describes TLP as "affecting power
consumption by tweaking *kernel settings*". To install, simply type in:

```
$ sudo apt update
$ sudo apt install tlp tlp-rdw
```

and to start TLP without waiting for a reboot: 

```
$ sudo tlp start
```

You can always check the status of TLP by typing

```
$ sudo tlp-stat -s
```

Installing TLP certainly helped my thermals quite a bit. However the one
drawback I learned about TLP is that it prevents your CPU from achieving
"turbo-boost". So there is a performance hit that you take as a result of
running TLP.

### auto-cpufreq

I discovered [auto-cpufreq](https://github.com/AdnanHodzic/auto-cpufreq) on
youtube when I came up on a [video](https://www.youtube.com/watch?v=B1iRxoyT4EA)
from the Chris Titus tech channel that talked about tips to improve power usage
and battery life on linux laptops.

auto-cpufreq is an automatic cpu speed & power optimizer that takes into
consideration a laptop's battery state, CPU usage, temperature and system load.
It's easy to install and enable as a Snap package. Here are the steps I
followed.

First, install snap and it's core packages.

```
$ sudo apt update
$ sudo apt install snapd
$ sudo snap install core core18
```

Then run the following command to install auto-cpufreq

```
$ sudo snap install auto-cpufreq
```

And run it using:

```
$ sudo snap run auto-cpufreq
```

That should start the tool and it will run as a daemon automatically in the
background. To check the status, you can run:

```
$ sudo systemctl status snap.auto-cpufreq.service.service
```

And there you have it, auto-cpufreq will work great on it's own and also in
tandem with TLP to give you great power optimization and thermal regulation on
your laptop.

My CPU cores stay at a cool 40C-45C and the GPU is down to 60C-65C. The laptop
finally feels like it can be used on a lap! :)

