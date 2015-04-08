---
layout: post
title: Emacs everywhere - using Emacs keybindings in all Mac OS X applications!
tags: productivity keybindings mac emacs
published: true
---
Learning one *real* text editor is a life investment. So you'd like that
investment to be really worth it and applicable to everything you do.
This article is for Mac users for whom the text editor choice fell on
Emacs.

# Assumptions

 * You're on Mac OS X 10.9 Mavericks
 * You like to have your left `alt` key configured as `Meta`

# Out of the box: Basic movement

Shells usually come with keybindings for Emacs (and vi) so cursor movement,
copy, paste, etc. work without any effort. `Meta` is bound to `Esc` by default,
you should change that in your terminal app[1] to enable things like `kill-word`
or `backward-kill-word`.

The basic text panes (as in TextEdit, Mail, etc.) of Mac OS X also suport some
Emacs keybindings[^1] without custom configuration but keybindings involving `alt-`
(`alt-f`, `alt-b`, etc.) will produce glyphs instead. This is useful if you're often
using characters that are not available in your basic keyboard layout but not
if you're trying to get ubiquitous Emacs bliss.

# The magic of DefaultKeyBinding.dict

Mac OS X provides a mechanism to override default key bindings system wide
on a per-user basis. The file is called `DefaultKeyBinding.dict` and has to
live in `Library/KeyBindings` below your home directory. The format is described
[here](http://xahlee.info/kbd/osx_keybinding_key_syntax.html).

This is my basic version of the file, also found [on GitHub](https://github.com/noroute/portable-environment/blob/master/Library/KeyBindings/DefaultKeyBinding.dict). It enables
deletions with `alt-`, movements with `ctrl-` and `alt-`, undo and word completion
with familiar Emacs key bindings.

{% highlight text %}
/* emacsify Mac OS X, see http://youtrack.jetbrains.com/issue/IDEA-17392 */
{
 /* Kill alt-bindings that keep me from using emacs-style operations */
  "~f" = "moveWordForward:";
  "~b" = "moveWordBackward:";
  "~d" = "deleteWordForward:";

 /* add some missing emacs features */
  "~<" = "moveToBeginningOfDocument:";
  "~>" = "moveToEndOfDocument:";
  "~v" = "pageUp:";
  "^v" = "pageDown:";
  "^/" = "undo:";
  "~/" = "complete:";
  "^j" = "insertNewline:";
}
{% endhighlight %}

# Fixing IntelliJ IDEA

My main motivation for this key binding hack was that I couldn't get
`alt-f` and `alt-b` to work with IntelliJ IDEA's Emacs key bindings.
Jetbrains provides a reasonable[^2] Emacs keymap but most bindings
involving `alt-` do *not* work on a Mac (which lead to a bunch
of unfixed [issues](http://youtrack.jetbrains.com/issue/IDEA-17392)
in their tracker; one of which contains the solution given here).

The use of `DefaultKeyBinding.dict` fixes IDEA's behaviour! You
might have to extend the `alt-`bindings further if you want to
use more of them in IntelliJ but be aware that this disables
the glyphs produced by the respective keys.

# Bonus: Mark-point everywhere!

As suggested in IDEA's YouTrack [issue](http://youtrack.jetbrains.com/issue/IDEA-17392#comment=27-89063) you can even enable Emacs' mark-point behaviour for cutting
and pasting of regions system-wide.

# Footnotes

[^1]: basically those involving `ctrl-`

[^2]: well, sort of reasonable; I will discusss this in a future post
