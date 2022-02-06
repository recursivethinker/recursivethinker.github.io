---
layout: post
title:  "Keychron Keyboard and Linux"
date:   2021-05-31 09:00:00 -0500
categories: Linux, External Keyboard
---

By default, the Keychron keyboards don't work very well with linux. The function keys in particular are a problem because they don't work as intended and sometimes pressing the 'fn' key doesn't help either. I spent quite some time researching this on the internet until I finally found my answer.

Bastian Venthur has an excellent [blog](https://venthur.de/2021-04-30-keychron-c1-on-linux.html) summarizing the problem and giving a great solution. The solution appears to be to set 'fnmode' to 2 in a sys module named 'hid_apple'. I'm not entirely sure how it all works but here's what you do -

```
# as root:
echo 2 > /sys/module/hid_apple/parameters/fnmode
```

According to the blog, this should now make the F-Keys simply work by pressing them and the multimedia keys by pressing 'fn+F-key'. To switch to default mode press and hold 'fn+X+L' for 4 seconds.

To make this change permanent you can create a file called hid_apple.conf and place the following line within it -

```
touch /etc/modprobe.d/hid_apple.conf
# inside the file -
options hid_apple fnmode=2
```
