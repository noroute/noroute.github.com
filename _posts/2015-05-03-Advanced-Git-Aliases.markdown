---
title: Supercharge your Git use - Advanced aliases
tags: productivity tools shell git basics
layout: post
published: true
---
Git's great and numerous advanced features are often hidden behind
hard to remember command line options. Fortunately, Git has a built-in
aliases system that gets you there faster.

Here are some of my frequently used aliases. As they are internal to
git[^1], use them like `git p`. Add them to the `[alias]` section of
your `~/.gitconfig` file or see
[my gitconfig](https://github.com/noroute/portable-environment/blob/master/gitconfig):

{% highlight text %}
# Pull in remote changes for the current repository and all its submodules:
p = !"git pull; git submodule foreach git pull origin master"

# Credit an author on the latest commit:
credit = "!f() { git commit --amend --author \"$1 <$2>\" -C HEAD; }; f"

# Interactive rebase with the given number of latest commits:
reb = "!r() { git rebase -i HEAD~$1; }; r"

# Find commits by commit message:
fm = "!f() { git log --pretty=format:'%C(yellow)%h %Cblue%ad %Creset%s%Cgreen [%cn] %Cred%d' --decorate --date=short --grep=$1; }; f"

# Find commits by source code (!!!):
fc = "!f() { git log --pretty=format:'%C(yellow)%h %Cblue%ad %Creset%s%Cgreen [%cn] %Cred%d' --decorate --date=short -S$1; }; f"

# Remove branches that have already been merged with master:
dm = "!git branch --merged | grep -v '\\*' | xargs -n 1 git branch -d"

# List contributors with number of commits:
contributors = shortlog --summary --numbered
{% endhighlight %}

[^1]: You could perfectly define these as shell aliases for the shell of your choice; using git's internal aliases is independent from the shell you're using and should be completely portable
