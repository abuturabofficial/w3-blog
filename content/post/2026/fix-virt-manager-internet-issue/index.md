---
draft: false
title: "Arch Linux: How to Fix KVM Virtual Machine's Internet Not Working with the Firewall Enabled"
imageNameKey: "fix-virt-manager-internet-issue"
date: '2026-04-28T11:48:01+05:00'
description: "When you install KVM/QEMU based Virtual Machine on your Arch Linux system, sometimes your internet doesn't work inside the VM, almost always your host OS firewall is at the fault."
author: "AbuTurab"
image: "fix-virt-manager-internet-issue-cover.webp"
tags: ['Linux', 'Tips & Tricks']
categories: [Blog]
keywords: ['how to fix internet not working inside virt-manager windows vm', 'fixing kvm/qemu internet not working inside virtual machine', 'omarchy/cachyos internet not working inside the virtual machine']
lastmod: '2026-04-28T17:03:04+05:00'
---

If you disable your firewall (UFW) and the Internet inside your QEMU/KVM virtual machine starts working again, then you're at the right place to fix it.

> [!NOTE] If your internet doesn't work even after disabling the Firewall, there might be something else wrong with your VM's network connection, and research online for specific answers.

Let's allow **forwarding** for the virtual bridge by editing `/etc/ufw/systcl.conf`:
```console{linenos=false}
sudo nvim /etc/ufw/sysctl.conf # OR use nano for editing
```

Add or uncomment the following lines:

```ini{linenos=false}
net/ipv4/ip_forward=1
net/ipv6/conf/default/forwarding=1
net/ipv6/conf/all/forwarding=1
```

Edit the default UFW config:
```console{linenos=false}
sudo nvim /etc/default/ufw
```

Set the following option:
```bash{linenos=false}
DEFAULT_FORWARD_POLICY="ACCEPT"
```

Add firewall rules to allow all incoming and outgoing traffic on libvirt network:
```console{linenos=false}
sudo ufw allow in on virbr0
sudo ufw allow out on virbr0
```

You are all set, just reload the firewall to apply those rules:
```console{linenos=false}
sudo ufw reload
```

Turn off the Virtual Machine, and start it again, now your Firewall won't block your VM's Internet Connection.

## References

- [QEMU-KVM in Arch Linux](https://gist.github.com/tatumroaquin/c6464e1ccaef40fd098a4f31db61ab22) --- Install Virt-Manager on Arch Linux