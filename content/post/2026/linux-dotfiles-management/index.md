---
draft: true
title: 'Managing dotfiles the Right Way: GNU Stow and ln -s'
imageNameKey: 'linux-dotfiles-management'
date: '2026-02-18T11:42:12+05:00'
description: 'Even if you are a Linux novice or a Pro, you are always experimenting stuff, which can go anywhere from a pleasant experience to disastrous end. So, it is a wise idea to keep track of changes to all the configuration files AKA dotfiles via public or private git repo, to easily rollback whenever needed.'
author: "AbuTurab"
image: 'linux-dotfiles-management.webp'
tags: ['Linux', 'Tips & Tricks']
categories: ['Blog']
keywords: ['gnu stow vs ln -s, which is better for dotfiles', 'how manage dotfiles on linux', 'dealing with configuration files on linux', 'the unix way of managing dotfiles/configs', 'a guide to dotfiles management on linux']
lastmod: ''
---

There are various methods and tools to manage your dotfiles on your Linux/Unix system. But we will discuss only two of them:
1. `GNU Stow` A Beginner friendly tool
2. `ln -s` Simple but effective without using any 3<sup>rd</sup> Party tool

## GNU Stow

## References

- [dotfiles](https://wiki.archlinux.org/title/Dotfiles) --- An ArchWiki Guide
- [My dotfiles repo](https://github.com/abuturabofficial/dotfiles) --- A mess but still do its job