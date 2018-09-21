---
title: Emacs Questions
permalink: /:categories/questions/emacs
date: 2018-09-16
categories:
  - collections
tags:
  - questions
  - emacs
---

# Active Questions

**Change indentation width.**

**Select block or paragraph.**

**Indent, unindent, reindent block.**

**Rename open file or buffer.**

**Column ruler.**

Sources: [EmacsWiki][FillColumnIndicator]

# Emacs Bookmarks

* [GNU Emacs Manual](https://www.gnu.org/software/emacs/manual/html_node/emacs/index.html)
* [EmacsWiki](https://www.emacswiki.org/)

## Text Insertion

Keys | Command
--- | ---
`C-q` | `quoted-insert`

### Insert newline

Keys | Command | Details
--- | --- | ---
`RET` | `newline` | Indents after new line
`C-j` | | New line only

### Erasing Text

Keys | Command | Details
--- | --- | ---
`<DEL>` | `delete-backward-char` | Delete before point
`C-d` | `delete-char` | Delete after point

## Cursor Movement

Keys | Command | Unit
--- | --- | ---
`C-f` | `forward-char` | Character
`C-b` | `backward-char` | Character
`M-f` | `forward-word` | Word
`M-b` | `backward-word` | Word
`C-a` | `move-beginning-of-line` | Line
`C-e` | `move-end-of-line` | Line
`C-n` | `next-line` | Line
`C-p` | `previous-line` | Line
`M-r` | `move-to-window-line-top-bottom` | Screen
`M-<` | `beginning-of-buffer` | Buffer
`M->` | `end-of-buffer` | Buffer

## Screen Movement

Keys | Command | Unit
--- | --- | ---
`C-v` | `scroll-up-command` | Screen
`M-v` | `scroll-down-command` | Screen
`C-l` | | Screen

## Search

Keys | Command | Type
--- | --- | ---
`M-g c` | | Character index
`M-g <TAB>` | | Column index
`M-g g` | `goto-line` | Line index


# Eliminating Whitespace Ambiguities

What's the difference between a tab width number of spaces and a tab? What's the
difference between a line with and without trailing whitespace? For most text
editors, visually deducing these differences is impossible, because both cases
are visually identical. Being able to visually tell these differences at a
glance is critical to navigate through code and text more predictably.

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

{% highlight elisp %}
(add-hook 'before-save-hook 'delete-trailing-whitespace)
{% endhighlight %}

See [Indenting and Tabbing](#indenting-and-tabbing) for details on how to
control when tabs appear.

[WhiteSpace]: https://www.emacswiki.org/emacs/WhiteSpace
[DeletingWhiteSpace]: https://www.emacswiki.org/emacs/DeletingWhitespace

# Selecting

* select word, line, block, paragraph, all
* select rectangle
* edit selection

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

[ReloadEmacsInit]: https://stackoverflow.com/questions/2580650/how-can-i-reload-emacs-after-changing-it
[FillCommands]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Fill-Commands.html
[RectangleCommands]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Rectangles.html
[BasicMacros]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Basic-Keyboard-Macro.html

[FillColumnIndicator]: https://www.emacswiki.org/emacs/FillColumnIndicator
[NoTabs]: https://www.emacswiki.org/emacs/NoTabs
