---
title: Emacs Questions
categories: collections
tags: questions emacs
permalink: /:categories/questions/emacs
---

# Active Questions


**Rename open file or buffer.**

# Inactive Questions

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

**Strip trailing whitespace.**

Add the following to Emacs init file to strip whitespace upon saving:

`(add-hook 'before-save-hook 'delete-trailing-whitespace)`

Sources: [EmacsWiki][DeletingWhiteSpace]

**Reload Emacs init file.**

Input `M-x load-file` and accept defaults.

Sources: [Stack Overflow][ReloadEmacsInit]

[DeletingWhiteSpace]: https://www.emacswiki.org/emacs/DeletingWhitespace
[ReloadEmacsInit]: https://stackoverflow.com/questions/2580650/how-can-i-reload-emacs-after-changing-it
[FillCommands]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Fill-Commands.html
[RectangleCommands]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Rectangles.html
[BasicMacros]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Basic-Keyboard-Macro.html