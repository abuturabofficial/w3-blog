---
draft: false
title: 'SysRq: The Secret Key to Safely Shutting Down a Frozen Linux System'
imageNameKey: "linux-sysrq-key"
date: '2025-01-13T09:47:13+05:00'
description: "Sometimes when your Linux system freezes, the magic SysRq key is your only hope for rescue."
author: "AbuTurab"
image: linux-sysrq-key-cover.webp
tags: ["Linux", "Troubleshooting Guide"]
categories: ["Blog"]
keywords: ["system rescue", "magic sysrq key on linux", "emergency system rescue", "how to rescue/shutdown frozen linux system", "what to do when my linux system freezes", "troubleshooting a frozen system"]
latmod:
---

We all remembered the classic blue screen of death on Windows, I still get its nightmares too 🥲. And we all escaped to Linux. But over here, everything isn't sunshine and rainbows either.

Sometimes your system gets locked up, and no <kbd>key</kbd> input or `tty` terminal works. At this time, your only hope left, to gracefully shutdown/reboot the system is **Magic SysRq Key**.

## Magic SysRq Key

It's a command consisting of key combinations which works at low level regardless of your system state, to recover your computer from **freezes** or to **reboot/shutdown** it, without corrupting the filesystem. <kbd>SysRq</kbd> aggressively remount the filesystem, terminate/kills the system processes and writes the unwritten data to the disk.

You can power off your system using the <button>Hardware RESET</button> button on your PC, but this doesn't make sure your filesystem/OS gets powered down elegantly.

<kbd>SysRq</kbd> key doesn't work when there is a kernel panic or hardware failure. Honestly, You have got bigger problems than smoothly shutting down your PC.

## Requirements

- Have `root/sudo` access
- Kernel compiled with `CONFIG_MAGIC_SYSRQ` kernel parameter (All mainstream distros has this feature built-in)
- <kbd>SysRq</kbd> or <kbd>PrtSc</kbd> key on your <kbd>QWERTY</kbd> keyboard
- On some systems/Laptops, you may need to hold <kbd>Fn</kbd> key during invoke process

## Configuration

> [!caution]
> The various combinations of the `SysRq` command are possible. We will proceed with `176` as a normal user, that's enough to effortlessly reboot/shutdown the frozen system. Do your due diligence to enable advanced functionality, as it can **arguably** weaken system security if it is a multi-access or modem attached system.
> 
> **See the [References](#references) section for more study guides on alleged security concerns.**

Check what value for `SysRq` is currently set:

```bash
cat /proc/sys/kernel/sysrq
```

> [!TIP]
> `0` means SysRq is disabled, `1` means all features are enabled.

We will set the `SysRq` value to <u>176</u>. The value 176 corresponds to specific SysRq functions enabled in the Linux kernel. It is calculated as follows:
-  **128**: Allow reboot/poweroff
- **32**: Enable remounting filesystems as read-only
- **16**: Enable sync command

Thus, 128+32+16=176 allows these functionalities while disabling others

Edit this file `/etc/sysctl.d/90-sysrq.conf` (need sudo privileges) using your favorite text editor and add this line:

```text
kernel.sysrq = 176
```

To apply these changes immediately:

```bash
sudo sysctl -p /etc/sysctl.d/90-sysrq.conf
```

To verify, changes have been applied:

```bash
cat /proc/sys/kernel/sysrq
```

The output should be <u>**176**</u>.

The configuration done this way, will persist across reboots.


## SysRq Usage

When your system becomes unresponsive and doesn't react at all, do this:

- Press and hold <kbd>Alt</kbd> key
- Press <kbd>Fn</kbd> + <kbd>PrtSc</kbd> OR <kbd>SysRq</kbd> keys, and release both while holding <kbd>Alt</kbd> key and press:
  - <kbd>s</kbd> to sync
  - <kbd>r</kbd> to remount
  - <kbd>e</kbd> to terminate the processes
  - <kbd>i</kbd> to kill the processes
  - <kbd>b</kbd> to reboot

That's how you can get back your locked/frozen system to life again, without using <button>Hardware RESET</button> button.

---

## References

- [What is SysRq Key?](https://en.wikipedia.org/wiki/Magic_SysRq_key) --- A detailed Wikipedia article about all the functions and commands.
- [How to enable all SysRq functions on Linux](https://linuxconfig.org/how-to-enable-all-sysrq-functions-on-linux) --- A pretty good tutorial which lists down all the functions.
- [How can the Magic SysRq key be dangerous for Linux users?](https://security.stackexchange.com/questions/138658/how-can-the-magic-sysrq-key-be-dangerous-for-linux-users) --- Some people do not consider SysRq to be a security concern.
- [Restricting the use of the Magic SysRq key](https://www.debian.org/doc/manuals/securing-debian-manual/restrict-sysrq.it.html) --- Debian docs advise restricting it, if the system is modem connected, has an unauthorized access possibility, or in a virtualized environment.
- [Linux Magic System Request Key Hacks](https://www.kernel.org/doc/html/latest/admin-guide/sysrq.html) --- Kernel docs about SysRq