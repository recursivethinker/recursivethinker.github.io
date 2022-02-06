---
layout: post
title:  "Adjusting text size on Ubuntu in CLI"
date:   2021-10-31 09:00:00 -0500
categories: Linux Tips Bash Terminal Ubuntu Gnome UI 
---

The font sizes when you use Ubuntu 20.04 LTE can be a bit too small by default. There are several methods to improve / increase the font size to make it easier to use your computer. This [article](https://vitux.com/how-to-change-text-size-in-ubuntu/) on vitux goes through them really well.

In the methods listed in that article. Method 3 is my preferred choice since it accomplishes it through a single command from bash.

```
$ gsettings set org.gnome.desktop.interface text-scaling-factor [scaling-factor-value]
```

```
$ gsettings set org.gnome.desktop.interface text-scaling-factor 1.6```

This is elegant, and straightforward.
