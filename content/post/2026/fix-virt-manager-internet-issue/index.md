---
draft: false
title: 'Arch Linux: How to Fix KVM Virtual Machine Internet Not Working with Firewall Enabled'
imageNameKey: "fix-virt-manager-internet-issue"
date: '2026-04-28T11:48:01+05:00'
description: "When you install KVM/QEMU based Virtual Machine on your Arch Linux system, sometimes your internet doesn't work inside the VM, almost always your host OS firewall is at the fault."
author: "AbuTurab"
image: "fix-virt-manager-internet-issue-cover.webp"
tags: ['Linux', 'Tips & Tricks']
categories: [Blog]
keywords: ['how to fix internet not working inside virt-manager windows vm', 'fixing kvm/qemu internet not working inside virtual machine', 'omarchy/cachyos internet not working inside the virtual machine']
lastmod: ''
---

If you disable your firewall and the Internet inside your QEMU/KVM virtual machine starts working, then you're at the right place to fix it. If your internet doesn't work even after disabling the Firewall, there might be something else with your network connection, and search online for answer.

Let's allow forwarding for the virtual bridge by editing `/etc/ufw/systcl.conf`:
```console{linenos=false}
sudo nvim /etc/ufw/sysctl.conf # OR use nano for editing
```

Add or uncomment the following lines:

```ini
net/ipv4/ip_forward=1
net/ipv6/conf/default/forwarding=1
net/ipv6/conf/all/forwarding=1
```

Edit the default UFW config inside:
```console{linenos=false}
sudo nvim /etc/default/ufw
```

Set the following:
```bash{linenos=false}
DEFAULT_FORWARD_POLICY="ACCEPT"
```

Add firewall rules to allow all traffic on libvirt network:
```console{linenos=false}
sudo ufw allow in on virbr0
sudo ufw allow out on virbr0
```

You are all set, just reload the firewall to apply those rules:
```console{linenos=false}
sudo ufw reload
```

Turn off the Virtual Machine, and start again, your Internet is working even when the Firewall is active.

## References

- [QEMU-KVM in Arch Linux](https://gist.github.com/tatumroaquin/c6464e1ccaef40fd098a4f31db61ab22) --- Install Virt-Manager on Arch Linux