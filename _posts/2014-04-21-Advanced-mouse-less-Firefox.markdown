---
title: Advanced mouse-less Firefox - Emacs style
tags: productivity keybindings browser firefox emacs
layout: post
published: true
---

If you are comfortable using Firefox mostly without touching
your mouse (see the [previous]({% post_url 2014-04-06-Lose-your-mouse-Keyboard-Driven-Firefox %})
article) *and* you're a passionate Emacs user, today I'd suggest to
incorporate your known and loved Emacs keybindings to Firefox
(KeySnail) and add even speedier link clicking foo (HoK).

# Introducing KeySnail
[KeySnail](https://github.com/mooz/keysnail/wiki) is a Firefox
extension for Emacs users. It comes pre-configured with many sensible
Emacs keybindings but
[here's](https://github.com/noroute/portable-environment/blob/master/.keysnail.js)
my take (place it in `~/.keysnail.js`).

Important and surprising keybindings (Emacs notation, note that `M-` is `Cmd`):
{% highlight text %}
F1-b (Show all key bindings)
C-x 1 (Close all tabs but current)
C-x l (focus to location bar)
C-x t (focus to first textarea)
C-x s (focus to first button)
C-c u (undo close tab)
C-M-y (select text from kill buffer)
F3    (Start macro recording!!!)
F4    (Stop recording/play)
{% endhighlight %}

Basic Emacs goodness:
{% highlight text %}
C-x 3 (New Tab)
C-x k (Close Tab)
C-g (Abort)
B (Back)
F (Forward)
R (Reload)
C-s (incremental search)
Movement and copy/yank behavior works with C- and M-
{% endhighlight %}

# HoK - Turbo navigation
The [plugin](https://github.com/mooz/keysnail/wiki/plugin) section of
KeySnail has HoK, a
[hit-a-hint](https://addons.opera.com/en/extensions/details/hit-a-hint-for-opera/)
clone that adds ad-hoc short keybindings to links, button and text
fields. This enables you to navigate most pages without any keyboard
use.

My prefixes (contained in `.keysnail.js`):
{% highlight text %}
C-c c   (open link)
C-c l   (open link in backgorund)
C-c y   (yank link)
C-c C-e (continous HoK mode)
{% endhighlight %}

HoK has different dynamics as find-as-you-type for links:

 * You have to look up the shortcuts on the screen and cannot go after the links text.
 * Lookup keys are much shorter in HoK.
 * You can also navigate to text fields in HoK.

*Try HoK and see if it changes your workflow.*
