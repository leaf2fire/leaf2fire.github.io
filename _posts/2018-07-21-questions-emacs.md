---
title: Emacs Questions
categories: collections
tags: questions emacs
permalink: /:categories/questions/emacs
---

# Active Questions

**Change indentation width.**

**Select block or paragraph.**

**Indent, unindent, reindent block.**

**Rename open file or buffer.**

**Column ruler.**

Sources: [EmacsWiki][FillColumnIndicator]



---
# Eliminating Whitespace Ambiguities

What's the difference between a tab width number of spaces and a tab? What's the
difference between a line with and without trailing whitespace? For most text
editors, visually deducing these differences is impossible, because both cases
are visually identical. Being able to visually tell these differences at glance
is critical to navigate through code and text more predictably.

Adding the following snippet inside the Emacs init file eliminates the
whitespace ambiguities mentioned earlier by making each case visually
different. This solution utilizes the whitespace package
[(EmacsWiki)][WhiteSpace].

{% highlight elisp %}
(require 'whitespace)
(setq whitespace-style '(face tabs spaces tab-mark))
(setq whitespace-space-regexp "\\( +$\\)")
(global-whitespace-mode 1)
{% endhighlight %}

Eliminating the possibility of a case appearing also reduces whitespace
ambiguities. Two commands that do exactly that are `M-x untabify` and `M-x
delete-trailing-whitespace`.

Almost all text-based files have no use for trailing whitespace syntactically or
semantically. Save some key-strokes by automatically deleting trailing
whitespace before saving [(EmacsWiki)][DeletingWhiteSpace].

Add the following to the Emacs init file:

{% highlight elisp %}
(add-hook 'before-save-hook 'delete-trailing-whitespace)
{% endhighlight %}

See [Indenting and Tabbing](#indenting-and-tabbing) for details on how to
control when tabs appear.

---
# Selecting

* select word, line, block, paragraph, all
* select rectangle
* edit selection

---
# Indenting and Tabbing

* Insert <tab>
* Indent line, block, or selection
* Unindent line, block, or selection
* Reindent block or selection

# Inactive Questions

**No tabs when auto-indenting.**

`(setq-default indent-tabs-mode nil)`

Sources: [EmacsWiki][NoTabs]

**Select all**.

`C-x h`



**Keyboard macros.**

`<F3>` to start defining macro.

`<F4>` to either end macro definition or execute most recent macro.

Sources: [GNU Emacs][BasicMacros]

**Rectangle select.**

Input `C-x <SPC>` to enable rectangle mark mode.

Sources: [GNU Emacs][RectangleCommands]

**Enforce 80 column rule.**

Input `M-q` to apply to current paragraph.

Change column width with `C-x f`.

Sources: [GNU Emacs][FillCommands]

**Reload Emacs init file.**

Make the init file the current buffer. Input `M-x load-file` and accept
defaults.

Sources: [Stack Overflow][ReloadEmacsInit]

[DeletingWhiteSpace]: https://www.emacswiki.org/emacs/DeletingWhitespace
[ReloadEmacsInit]: https://stackoverflow.com/questions/2580650/how-can-i-reload-emacs-after-changing-it
[FillCommands]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Fill-Commands.html
[RectangleCommands]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Rectangles.html
[BasicMacros]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Basic-Keyboard-Macro.html
[WhiteSpace]: https://www.emacswiki.org/emacs/WhiteSpace
[FillColumnIndicator]: https://www.emacswiki.org/emacs/FillColumnIndicator
[NoTabs]: https://www.emacswiki.org/emacs/NoTabs