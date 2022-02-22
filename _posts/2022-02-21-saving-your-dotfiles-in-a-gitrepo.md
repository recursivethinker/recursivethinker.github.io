---
layout: post
title: "How to create a gitrepo for your config files."
date: Mon 21 Feb 2022 04:13:11 PM PST
categories: Linux, tips, git, config files. 
---
# How to create a gitrepo for your config files.

I stumbled on this cool video by distrotube on youtube -
[https://www.youtube.com/watch?v=tBoLDpTWVOM]. I found the original blog post
mentioned there - [https://www.atlassian.com/git/tutorials/dotfiles] and
proceeded to follow the instructions and set it up for myself.

First, create a bare git repo in the `$HOME` folder.
```
$ git init --bare ~/.config-files
```

Then, setup an alias for the git command that uses the `$HOME` directory as the
working directory and this new `config-files` directory as the git repo.
```
$ alias config-files='/usr/bin/git --git-dir=$HOME/.config-files/ --work-tree=$HOME'
```

Now you can set a flag in this repository to hide files we aren't explicitly
tracking.
```
$ config-files config --local status.showUntrackedFiles no
```

As an extra step you can add this alias to your bashrc file -
```
$ echo "alias config-files='/usr/bin/git --git-dir=$HOME/.config-files/
--work-tree=$HOME'" >> $HOME/bashrc
```

Wit these steps done, you should now be able to add specific files into your
gitrepo like this:
```
$ config-files add .vimrc
```

And commit your changes like so -
```
$ config-files commit -m 'Added the vimrc config'
```

If you have a remote repo somewhere, for example in github, you can now push
these by setting up your remote repo.

```
$ config-files remote add origin <path_to_remote_repo>
```

Now simply type 
```
$ config-files push
``` 

and you should be able to push your configs to github or wherever you like!

Cheers.
