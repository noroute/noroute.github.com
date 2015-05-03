---
title: Supercharge your Git use - Powerful Git shell aliases
tags: productivity tools shell git
layout: post
published: false
---

If you're using the Git command line client a lot[^1], your shell and
Git itself can grease your workflows quite a bit..

= oh-my-zsh Git module

The famous zsh configuration project has a module which contains many
handy git aliases. My favorites:

 * `gco : git checkout`
 * `gca : git commit -a`
 * `gcm : git checkout master`
 * `gp : git push`
 * `gl : git pull`
 * `grhh : git reset --hard HEAD`

For `git-svn` integration (always helpful):

 * `gsr : git svn rebase` (aka *pull*)
 * `gsd : git svn dcommint` (aka *push*)


[^1]: on a Unix-like system, that is
