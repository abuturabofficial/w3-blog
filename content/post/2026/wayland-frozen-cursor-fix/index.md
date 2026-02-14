---
draft: false
title: 'Linux: Regaining Control of Frozen Cursor After Suspend/Sleep on Wayland'
imageNameKey: 'wayland-frozen-cursor-fix'
date: '2026-02-14T10:58:44+05:00'
description: "Sometimes, when you put your computer to sleep/standby, on wakeup, cursor gets frozen. You will need to reload the Kernel module for respective mouse/touchpad driver to unfreeze your cursor."
author: "AbuTurab"
image: 'wayland-frozen-cursor-fix-cover.webp'
tags: ['Linux', 'Troubleshooting Guide']
categories: ['Blog']
keywords: ['how to unfreeze cursor on linux', 'frozen cursor issue on linux when waking up from sleep', 'toucpad froze on wake up from sleep', 'cursor disappeared after waking up from sleep']
lastmod: '2026-02-14T12:07:39+05:00'
---

There is a bug affecting Fedora and Archlinux systems, where system cursor gets frozen in a place when your PC wakes up from the sleep.

> [!INFO] ''
> I have tested this fix on my ThinkPad only, both on Archlinux and Fedora.

## Archlinux

To regain the control of your cursor, it's quite easy, you need to reload the `psmouse` module.

From the Terminal, run this:
```console{linenos=false}
sudo modprobe -r psmouse
```
It will remove the `psmouse` Kernel module.

Then, to reload the module:
```console{linenos=false}
sudo modprobe psmouse
```

Voilà, your cursor is back.
- `modprobe` Add or remove Kernel modules
- `-r`/`--remove` Removes the specified Kernel module
- `psmouse` General Kernel module for Touchpads and Mouse.

## Fedora

When you run the command:
```console{linenos=false}
sudo modprobe -r psmouse
```

It spits the following error:
![](wayland-frozen-cursor-fix-1.webp)

To regain control of a cursor on Fedora, you need the exact driver name of your Mouse/Touchpad.

First, to find out the name of your Touchpad/Mouse name:
```console{linenos=false}
cat /proc/bus/input/devices
```

Look for your Mouse/Touchpad name
![](wayland-frozen-cursor-fix-2.webp)

Note the `event_id`, then run following command replacing `<event_id>` with your handlers ID.
```console{linenos=false}
readlink /sys/class/input/<event_id>/device/device/driver
```

Note the driver name, in my case it was `elan_i2c`:
![](wayland-frozen-cursor-fix-3.webp)

Now, to remove the Kernel module of touchpad/mouse:
```bash{linenos=false}
sudo modprobe -r elan_i2c #replace with your own driver module name
```

Then, reload the driver:
```bash{linenos=false}
sudo modprobe elan_i2c #replace with your own driver module name
```

Voilà, your cursor is unfrozen on Fedora too.