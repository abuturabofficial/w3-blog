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

## Idle/Lock Settings

> [!ERROR] Unintended Consequences, please see [this section](#sleep-settings).

Let's enable Screen Idle after 60 seconds:
```console{linenos=false}
gsettings set org.gnome.desktop.session idle-delay 60
```
- The `idle-delay` basically means, the screen will turn off after 60 seconds of inactivity.

Now, let's check the set value:
```console{linenos=false}
gsettings get org.gnome.desktop.session idle-delay
```

Enable the screen saver:
```console{linenos=false}
gsettings set org.gnome.desktop.screensaver lock-enabled true
```

To check the set value:
```console{linenos=false}
gsettings get org.gnome.desktop.screensaver lock-enabled
```

Now set the Screen Lock delay to 600 seconds (10 minutes)
```console{linenos=false}
gsettings set org.gnome.desktop.screensaver lock-delay 600
```

To know set values:
```
gsettings get org.gnome.desktop.screensaver lock-delay 
```


Now, the PC screen will turn off after 60 seconds, without locking it. After 10 minutes, if no activity is detected, it will lock the screen.

## Sleep Settings

> [!WARNING]
> The one side effect of using `gsettings` to control ScreenLock and Screen-idle is, missing **Sleep settings** on battery/power via Settings GUI.

But these settings can be set via `gsettings` too.

### Suspend/Sleep State

To check available sleep/suspend states on battery:
```console{linenos=false}
gsettings range org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type
```

On AC:
```console{linenos=false}
gsettings range org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type
```

To disable automatic sleep on AC:
```console{linenos=false}
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'nothing'
```

To re-enable, just replace `'nothing'` with `'suspend'`

### Suspend/Sleep Duration

To set a sleep delay on AC (in seconds):
```
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 1800
```

To check the set value on AC:
```
gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout
```

To set a sleep value on Battery (in seconds):
```
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 1200
```

To check the set value on Battery:
```
gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout
```