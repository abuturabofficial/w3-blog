---
draft: true
title: 'Fedora: Things to Do After Installation'
imageNameKey: 'fedora-post-installation-guide'
date: '2026-02-23T10:27:43+05:00'
description:
author: "AbuTurab"
image: 'fedora-post-installation-guide-cover.webp'
tags: ['Linux', 'Tips & Tricks']
categories: ['Blog']
keywords:
lastmod: ''
---

## DNF5 Configuration `dnf.conf`

To improve package cache, colored display output etc., add the following lines to your `/etc/dnf/dnf.conf` file.

```conf
[main]
color=true
max_parallel_downloads=10
keepcache=true
defaultyes=true
```
- `color` Enables color output during `DNF` operations
- `max_parallel_downloads` Enables parallel downloading for faster updates & installations
- `keepcache` Keep downloaded packages in the Cache
- `defaultyes` If enabled default answer to user confirmation prompt will be **Yes**
![](fedora-post-installation-guide-1.webp)

You can also add:
```
fastestmirror=true
```

It will rate the mirror based on latency. But not all mirrors have up-to-date packages, you might see mirror errors during updates and installations.
![](fedora-post-installation-guide-2.webp)

## Beautiful Cursor

![](fedora-post-installation-guide-3.webp)

First install `gnome-tweaks`, it will be helpful in many ways.
```console{linenos=false}
sudo dnf install gnome-tweaks
```

Download the [Bibata Cursors](https://github.com/ful1e5/Bibata_Cursor/releases), from their release page, or with the following command directly:
```console{linenos=false}
wget https://github.com/ful1e5/Bibata_Cursor/releases/latest/download/Bibata.tar.xz
```

Let's make an `icon` directory:
```console{linenos=false}
mkdir -p ~/.local/share/icons
```

Now let's extract the `Bibata.tar.xz` to the `icons` directory:
```console{linenos=false}
tar -xvf Bibata.tar.xz -C ~/.local/share/icons
```
- `tar` Archival and extraction utility
- `-x`/`--extract` Extract files from an archive
- `-v`/`--verbose` Verbosely list files processed
- `-f`/`--file=ARCHIVE` Use archive filename or device ARCHIVE
- `-C``--directory=DIR` Change to **DIR** before performing any operations

Now just open `gnome-tweaks` app, go to `Appearance`. Under `Styles > Cursors`, change it to your liking:
![](fedora-post-installation-guide-4.webp)

## RPM Fusion: Free and Non-Free

RPM Fusion repos are necessary to obtain pieces of software which are not available in the Official Repos due to licensing restrictions like multimedia codecs, GPU driver etc.

Using `DNF`:
```console{linenos=false}
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

To enable WebRTC support:
```console{linenos=false}
sudo dnf config-manager --enable fedora-cisco-openh264
```

[Appstream metadata](https://www.freedesktop.org/wiki/Distributions/AppStream/?__goaway_challenge=meta-refresh&__goaway_id=8d16de108595959949421d02eb36d6b0&__goaway_referer=https%3A%2F%2Frpmfusion.org%2F) provide GUI way to install RPM Fusion packages via GNOME Software or KDE Discover.
```bash{linenos=false}
sudo dnf update @core

# Since DNF5(F41 & later), the Fedora groups cannot be extended by RPM Fusion. So you need to mention the package explicitly

sudo dnf install rpmfusion-\*-appstream-data
```

> [!TIP]
> Official Configuration [Guide](https://rpmfusion.org/Configuration) for RPM Fusion Setup

## Multimedia Codecs

It's a good idea to switch to full `ffmpeg` package to avoid version mismatches.
```console{linenos=false}
sudo dnf swap ffmpeg-free ffmpeg --allowerasing
```

 ### Install Additional Codecs

To play all kinds of multimedia in Browsers as well through multimedia players.
```console{linenos=false}
sudo dnf update @multimedia --setopt="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin
```

### Hardware Accelerated Codec

#### Intel

For Intel Recent Hardware (rpmfusion-nonfree):
```console{linenos=false}
sudo dnf install intel-media-driver
```
For Broadwell (5th gen) and newer chipsets particularly Ice Lake (10th gen) and newer.

For older Hardware (rpmfusion-free):
```console{linenos=false}
sudo dnf install libva-intel-driver
```

#### Hardware codes with AMD (mesa)

This is needed since Fedora 37 and later. It mainly concerns the AMD hardware:
```console{linenos=false}
sudo dnf swap mesa-va-drivers mesa-va-drivers-freeworld
```

If using i686 compact libraries (for steam or a likes)
```console{linenos=false}
sudo dnf swap mesa-va-drivers.i686 mesa-va-drivers-freeworld.i686
```

> [!TIP]
> For NVIDIA, Broadcom Network Drivers, DVD drivers, [checkout](https://rpmfusion.org/Howto/Multimedia) the official detailed guide.

> [!INFO]
> [Checkout](https://fedoraproject.org/wiki/Hardware_Video_Acceleration) Official Hardware Video Acceleration Guide for Fedora. Also, Firefox Hardware Acceleration [Guide](https://fedoraproject.org/wiki/Firefox_Hardware_acceleration).


## References

- [Fedora 43 Post Install Guide](https://github.com/devangshekhawat/Fedora-43-Post-Install-Guide) --- A Great Optimization Guide
- [Bash CLI Tips & Tricks](/bash-terminal-tips-tricks/) --- Learn Terminal Superpowers
- [Practical BASHRC Tweaks](/bash-shell-configuration/) --- Make Your Terminal, a Beautiful Place to Spend Time
- [How to Diagnose and Fix Slow Boot on SystemD-based Linux Distros](/investigating-long-startup-time-on-linux/) --- Investigate and Fix Slow Boot-up
- [GNOME: ScreenIdle and ScreenLock Customization](/gnome-sceenlocking/) --- If You Love KDE Screen Idle and Lock Settings
- [Managing dotfiles the Right Way: GNU Stow and ln -s](/linux-dotfiles-management/) --- How to Manage Linux Configuration Files Across Distros
- [GNOME Tips: Keyboard Shortcuts for More Than 4 Workspaces](/gnome-workspace-shortcuts/) --- Need More than 4 Default Workspaces