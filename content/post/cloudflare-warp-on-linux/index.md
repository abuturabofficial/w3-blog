---
date: '2024-12-18T12:58:09+05:00'
draft: false
title: "Cloudflare Warp on Linux: Setup and Troubleshooting Guide"
keywords: ["cloudflare warp setup on linux", "how to setup warp on linux", "how to troubleshoot warp on linux", "guide to cloudflare warp", "fix issues with warp on linux"]
author: "AbuTurab"
tags: ["Linux", "Security", "VPN"]
categories: ["Blog"]
description: To setup cloudflare warp on linux and fix issues due to systemd-resolved on linux. How to setup and install Warp on Immutable Distros like SilverBlue, OpenSuse Aeon etc.
image: "cloudflare-warp-cover.webp"
lastmod: "2025-01-01"
---

**Cloudflare Warp** is a software solution that routes your internet traffic through Cloudflare's secure network using the Warp protocol. By using Cloudflare’s public IP instead of your ISP’s, it helps protect your data and shield you from certain types of cyberattacks.

A second major benefit is enhanced privacy. Since your traffic is routed through Cloudflare, your ISP cannot monitor your online activities. This also allows you to bypass government-imposed internet blocks and censorship, granting you freer access to the web.

## Installation

There are two major popular types of Linux distros, we will see, how to install Cloudflare Warp on both of them one-by-one.

> [!task]
> This blog has the following goals for installation of Cloudflare Warp client and general troubleshooting.
> - [x] Installation on Traditional/Mutable Linux Distributions
> - [x] Installation on Immutable Linux Distributions
> - [x] Troubleshooting the `systemd-resolved` DNS Resolver with no custom configuration and Warp Client
> - [x] Fixing the issues with custom DNS configuration with `systemd-resolved` and Warp Client

> [!TIP] 
> You can directly follow the official installation instructions [here](https://pkg.cloudflareclient.com/) and can skip the installation steps. If you have installed and [registered it](#using-warp-client) already then simply go to **[this section](#general-issues-and-fixes)** for the issues and fixes.

### 1. Traditional Linux Distributions

These are your normie distros like Ubuntu, Linux Mint, Arch Linux etc., where **system files, user, and system configuration files** can be created/deleted and modified freely. It allows you to install packages via normal Package managers like `apt`, `pacman`, `yum`, `zypper`, `dnf` etc. If you aren't already familiar with the concept of immutable/atomic Linux distros, you're most probably not using the one.

#### For Ubuntu and Ubuntu Based Distros (Mint, PopOS etc.)

To add Cloudflare GPG keys:

```bash
curl -fsSL https://pkg.cloudflareclient.com/pubkey.gpg | sudo gpg --yes --dearmor --output /usr/share/keyrings/cloudflare-warp-archive-keyring.gpg
```

Add the repo to your APT respositories:

```bash
echo "deb [signed-by=/usr/share/keyrings/cloudflare-warp-archive-keyring.gpg] https://pkg.cloudflareclient.com/ $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/cloudflare-client.list
```

Refresh the APT package database and install the software:

```bash
sudo apt-get update && sudo apt-get install cloudflare-warp
```

#### For RedHat Based Distros (including openSUSE)

Add the repo:

```bash
curl -fsSl https://pkg.cloudflareclient.com/cloudflare-warp-ascii.repo | sudo tee /etc/yum.repos.d/cloudflare-warp.repo
```

Now update the package database:

```bash {linenos=true}
sudo yum update # For RHEL Distros inlcuding Fedora
sudo zypper refresh #OR For openSuSe specifically, you can use this too,
#OR
sudo dnf update # For Fedora Based distros if above command doesn't work
```

Install Cloudflare warp client:

```bash {linenos=true}
sudo yum install cloudflare-warp #For Fedora and other RHEL based distros
sudo zypper install cloudflare-warp #For OpenSUSE
#OR
sudo dnf install cloudflare-warp #For Fedora or its based distros
```

### 2. Immutable/Atomic Linux Distributions

The steps for adding the repo to your sources is similar as above for **Debian/Ubuntu**, **RHEL** based distros. The only difference will be in the installation of the client, as on immutable distros we don't have access to the normal package manager.

### For Fedora/Based Atomic Distributions

After adding the repo to your sources list. Update the package database:

```bash
rpm-ostree update
```

Now layer/install the client on the host image:

```bash
rpm-ostree install cloudflare-warp
```

### For OpenSUSE based Atomic Distros (Aeon etc.)

After adding the source as above you can install the client as follows

```bash
sudo transactional-update pkg install cloudflare-warp
```

> [!TIP]
> If above command can't find the Warp client, simply reboot and then try.

## Using Warp Client

If you have carefully followed the installation instructions, you will have the `warp-cli` in your path. It simply means you would be able to execute `warp-cli` command from your terminal.

Sometimes Warp Systemd service doesn't start automatically while installing, so:

```bash
sudo systemctl enable --now warp-svc.service
```

This will enable and start the systemd service, you will normally able to use `warp-cli` command.

> [!INFO] Here is the **[Official Guide](https://developers.cloudflare.com/warp-client/get-started/linux/)** for `warp-cli` usage and initial setup.

> [!WARNING]
> On Atomic/Immutable distros, you will need to reboot your PC, to get Warp client working. On normal distros, if the `warp-cli` isn't available right away, simply close then reopen the terminal.

First register the client (First timers only)

```terminal
warp-cli registration new
```

Then connect the client:

```terminal
warp-cli connect
```

Check the status:

```terminal
warp-cli status
```

It should say **connected**.

Check if you're connected via Warp protocol:

```terminal
curl https://www.cloudflare.com/cdn-cgi/trace/
```

Look for `warp=on`

{{< figure src="cloudflare-warp-on-linux-2.webp" align="center">}}


## General Issues and Fixes

### `systemd-resolved` with no custom configuration

- For systems using `systemd-resolved` as a DNS resolver, you will need to add following to your `/etc/systemd/resolved.conf` file :

```.conf
[Resolve]
ResolveUnicastSingleLable=yes
```

And restart the `systemd-resolved` service:

```bash
sudo systemctl restart systemd-resolved
#Optionally restart this service too.
sudo systemctl restart systemd-networkd
```

Now connect the `warp-cli` again with the command `warp-cli connect` and check the status `warp-cli status` if it shows **connected** now.

- If you are still unable to get connected, deleting the `resolved.conf` file altogether might help. `NetworkManager` will be to still resolve the DNS.

Instead of deleting, you can do this:
```bash
mv /etc/systemd/resolved.conf /etc/systemd/resolved.conf.bak
```

Now restart the `systemd-resolved` service again. Check `warp-cli status`, you might have the **connection established** and internet access available.

### `systemd-resolved` With Custom Configuration

- I personally use `nextDNS` as my upstream DNS resolver, my `resolved.conf` file looks like this:

{{< figure src="cloudflare-warp-on-linux-3.webp" align="center">}}

So for me, all the above fixes don't work. As `warp-cli` by default tries to connect with `warp` mode which is in normal terms, tries to proxy the **DNS queries** too along with tunneling your normal traffic through Cloudflare Network.

I get the following error:

{{< figure src="cloudflare-warp-on-linux.webp" align="center">}}

- To fix this, we need to change the default mode to `tunnel_only`

Here are the different modes available for `warp-cli` client:

```bash
warp-cli mode --help
```

{{< figure src="cloudflare-warp-on-linux-1.webp" align="center">}}

As the `tunnel_only` mode does not proxy the DNS, this is the mode we need to use alongside our custom DNS for upstream resolution.

- To change the `warp-cli` mode:

```bash
warp-cli mode tunnel_only
```

Now disconnect and connect again:

```bash {linenos=true}
warp-cli disconnect
warp-cli connect #There is no reconnect command to avoid extra step.
```

To verify, you're connected to the tunnel, `warp-cli status`, it should say `connected`.

To verify if I'm still using `nextDNS` (for nextDNS only), I can use:

```bash
curl -L https://test.nextdns.io/
```

It will show if I'm using `nextDNS`or not, also my device name and protocol used.

{{< figure src="cloudflare-warp-on-linux-4.webp" align="center">}}

So, I'm successfully able to route my traffic through Cloudflare network using Warp Protocol and still using my custom upstream DNS provider (nextDNS).

## Final Thoughts
> [!CONCLUSION]
> I hope you're now connected to your **Cloudflare Warp tunnel** successfully. If you need further clarification or help at any step you can comment down below. **Warp on!**
