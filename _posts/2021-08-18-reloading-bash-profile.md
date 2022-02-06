---
layout: post
title:  "Reload your bash profile"
date:   2021-08-18 09:00:00 -0500
categories: Linux Tips Bash Terminal 
---

Sometimes when you launch your terminal in linux, your custom commands that are usually found in the `~/.bin` directory aren't always loaded up properly. If you find yourself in this situation, use the following command:

```
$ source ~/.profile
```

That will reload the bash profile and include your bin files!

