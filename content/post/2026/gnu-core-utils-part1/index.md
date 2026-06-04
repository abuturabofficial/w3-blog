---
draft: true
title: ' GNU Coreutils: ls, vdir, realpath'
imageNameKey: 'gnu-core-utils-part1'
date: '2026-06-04T06:40:37+05:00'
description:
author: "AbuTurab"
image: 'gnu-core-utils-part1-cover.webp'
tags: ['COREUTILS SERIES', Linux]
categories: ['SysAdmin']
keywords: ['how to use mkdir, rmdir, ls, touch', 'tutorial for gnue core utilities', 'tutorial for gnu core file utilities', 'how gnu core utilities work']
lastmod: ''
---

It's a part of multi blogs [series](/tags/coreutils-series/), which will explain how to use GNU Core Utilities, useful for novice and professionals alike. GNU Coreutils are file, shell, and text manipulation commands/tools which are available on every GNU based Linux system.

In today's blog, you will learn about Coreutils that are used in everyday file operations. Let's begin:

> [!NOTE]
> I will only explain those functions and commands which are in my opinion add value to everyday usage and management of the Linux Systems.

## `ls` --- list directory contents

To show the contents of a directory:
```console{linenos=false}
ls
```
- This command will list only non-hidden directories and files.

List subdirectories and their content recursively:
```console{linenos=false}
ls -R
```
- `--recursive`/`-R` Useful for investigation of unknown directories and their content

### Show Hidden Entries

To list entries started with `.` (hidden):
```console{linenos=false}
ls -a
```
- `--all`/`-a` lists hidden files and directories

The flag `--all` also shows `.` And `..` Which represent current directory and parent directory respectively. To hide those:
```console{linenos=false}
ls -A
```
-`--almost-all`/`-A` It doesn't list implied `.` and `..`

### Show Long Listings

To show long listing format:
```console{linenos=false}
ls -l
```
- `-l` Shows permissions, owner, group, size and timestamps, along with the entries

To omit group information from long listing format rest is same as `-l` flag:
```console{linenos=false}
ls -o
```
- `-o`/`-lG`/`-l --no-group` Exclude group information from long listing format

Owner can be omitted as:
```console{linenos=false}
ls -g
```

### Timestamp Listing

### Print Size Information

### Sorting Order

To list directories before files:
```console{linenos=false}
ls --show-directories-first
```
- It can be combined with `-l` `-a` flags

Reverse order while sorting:
```console{linenos=false}
ls -r
```
- `--reverse`/`-r` Reverse the current order of listings

Sort by file size:
```console{linenos=false}
ls -S
```
- `--size`/`-S` Sort the largest sized file first, doesn't help with directories

To sort by time:
```console{linenos=false}
ls -t
```
- `-t` Sort the newest file first


## References

- [GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html#ls-invocation) --- GNU Official Manual
- [GNU Core Utilities](https://en.wikipedia.org/wiki/GNU_Core_Utilities) --- Wikipedia
- `man <command name>` --- The source for commands and the most flags used here taken for manual pages bundled with the COREUTILS package installed on Linux