---
draft: false
title: 'Thunar File Manager: Open any Terminal via Open Terminal Here'
imageNameKey: "thunar-open-terminal"
date: '2026-04-23T14:33:56+05:00'
description: "Open any terminal via Open Terminal Here, from right click context menu of Thunar File Manager."
author: "AbuTurab"
image: "thunar-open-terminal-cover.webp"
tags: ["Linux", "Tips & Tricks"]
categories: ["Blogs"]
keywords: ['how to open terminal here in thunar file manager', 'open terminal here in thunar with alacritty', 'use kitty as open terminal here for thunar file manager', 'using custom terminal for open terminal here context menu of thunar file manager']
lastmod: '2026-04-23T15:06:04+05:00'
---

Add the following line to the `helpers.rc` file in the `~/.config/xfce4/` directory, if the file doesn't exist, create a new one.
```ini{linenos=false}
TerminalEmulator=alacritty
```

Confirm via terminal by running this command:
```sh{linenos=false}
exo-open --launch=TerminalEmulator
```

Or right click anywhere in your **Thunar File Manager** window. Then click `Open Terminal Here`, it should open the current directory in your terminal of choice, it's alacritty for example given here.


## References

- [Thunar: Open Terminal Here](https://wiki.archlinux.org/title/Thunar#Open_Terminal_Here) --- ArchWiki