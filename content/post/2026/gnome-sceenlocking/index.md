---
draft: false
title: 'GNOME: ScreenIdle and ScreenLock Customization'
imageNameKey: 'gnome-screenlocking'
date: '2026-02-19T15:16:50+05:00'
description: "If you want to control GNOME screen turn off, and screen lock separately like KDE, you came to the right place."
author: "AbuTurab"
image: 'gnome-screenlocking-cover.webp'
tags: ['Linux', 'Tips & Tricks']
categories: ['Blog']
keywords: ['GNOME power customization', 'How to turn off only screen when idle on GNOME','gnome controlling screen idle and screen lock separately']
lastmod: '2026-02-19T15:37:31+05:00'
---

GNOME GUI Settings manager `gnome-control-center` doesn't allow turning off the screen on idle without locking it first.

The `gsettings` tool comes to our rescue. It's a built-in command-line tool to manage configuration settings on GNOME.

Let's enable Screen Idle after 60 seconds:
```console{linenos=false}
gsettings set org.gnome.desktop.session idle-delay 60
```
- The `idle-delay` basically means, the screen will turn off after 60 seconds of inactivity.

Enable the screen saver:
```
gsettings set org.gnome.desktop.screensaver lock-enabled true
```

Now set the Screen Lock delay to 600 seconds (10 minutes)
```
gsettings set org.gnome.desktop.screensaver lock-delay 600
```

Now, the PC screen will turn off after 60 seconds, without locking it. After 10 minutes, if no activity is detected, it will lock the screen.