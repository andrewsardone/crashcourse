# GNU Screen Crash Course

## Introduction

A real quick GNU screen crash course with the key features I use.

`man screen`

  - Emulates terminals in a full-screen window manager
  - Detachable, so shell sessions aren't attached to a login process
  - Retachable, so shell sessions can be resumed between logins (handy for long-running tasks)

## Listing available `screen` sessions

`screen -ls`

## Creating/attaching to a screen session

`screen -d -R foo`

This will attach to the screen session `foo` if it exists, otherwise it will create a screen session named `foo`.

## Detaching from a screen session

Screen sessions are controlled by escaping terminal emulation and sending screen commands.

To escape terminal emulation, you hit your escape keybinding. By default, this is done by holding down the control key and hitting `a`. The notation we'll use is `C-a` (dashes indicate the keys are hit together, spaces mean the keys are hit separately).

The `detach` command is bound to the `d` key, so to detach from a screen session, hit `C-a d`.

### Note

To view the available screen commands, hit `C-a h`. You'll note that you can also verbosely send screen commands via screen's command prompt. Hit `C-a :`, then type the command at the prompt, e.g., `detach`.

## Creating multiple terminals, or "windows"

`C-a c`

## Viewing all your terminals

`C-a "`

Arrow through and hit enter to select a terminal.

## Naming an individual terminal

`C-a A`

## Paging through terminals

`C-a n` (next terminal)

`C-a p` (previous terminal)

## Copy-mode

This is handy for grabbing text, or just navigating through your scroll back.

`C-a [` (enters copy-mode)

Now you can arrow up and down your buffer, or use Vi-style keybindings by default:

  - `j` down
  - `k` up
  - `h` left
  - `l` right
  - `C-u` page up
  - `C-d` page down
  - `$` end of line
  - `^` beginning of line
  - `e` forward-word
  - `b` backward-word

While stile in copy-mode, hit the space bar to start a selection. Navigate to find your selection's end-point, then hit space to send the selection to your copy buffer and exit copy mode.

Paste your selection via `C-a ]`

You can always abort copy-mode via the literal escape key, or the escape key-sequence `C-[`.

## Window splitting

Handy for viewing multiple terminals.

`C-a S`

When splitting, your cursor will gain focus of a split with no terminal in it. Create a new one with `C-a c`.

Cycle through your splits with `C-a TAB`.

Make a split full screen again: `C-a Q`.

## Addendum

Since `C-a` is already bound to `move-beginning-of-line` in most shells (Emacs FTW), you can still obtain this behavior in screen via `C-a a`. FWIW, I rebind my escape keybinding to `C-]` in my [.screenrc](https://github.com/andrewsardone/dotfiles/blob/master/screen/screenrc.symlink#L11).

Also, if you haven't already done so, remap your keyboard's Caps Lock key to Control.
