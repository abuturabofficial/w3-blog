---
draft: false
title: ' GNU Coreutils: ls, vdir, realpath'
imageNameKey: 'gnu-core-utils-part1'
date: '2026-06-04T06:40:37+05:00'
description: "Let's understands the working of ls, vdir, and realpath, Coreutilites. GNU Coreutilties are the collection of numerous unix-based shell commands developed by GNU Project that provide essential file, text and shell based manipulation techniques and features."
author: "AbuTurab"
image: 'gnu-core-utils-part1-cover.webp'
tags: ['Coreutils Series', Linux]
categories: ['SysAdmin']
keywords: ['how to use ls, vdir, realpath', 'tutorial for gnue core utilities', 'tutorial for gnu core file utilities', 'how gnu core utilities work', 'ls - in-depth tutorial']
lastmod: '2026-06-08T18:45:17+05:00'
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

List entries by column (default):
```console{linenos=false}
ls -C
```
![ls --- Default column view](gnu-core-utils-part1-1.webp)

List entries by rows instead of default column view:
```console{linenos=false}
ls -x
```
![ls --- Row view](gnu-core-utils-part1-2.webp)

List one file per line:
```console{linenos=false}
ls -1
```

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

![ls --- Long listing format](gnu-core-utils-part1-3.webp)

To omit group information from long listing format, rest is the same as `-l` flag listing:
```console{linenos=false}
ls -o
```
- `-o`/`-lG`/`-l --no-group` Exclude group information from long listing format

Owner can be omitted as:
```console{linenos=false}
ls -g
```

Print the author information of each file, when used with `-l`:
```console{linenos=false}
ls -l --author
```
- It's useful on multi-user systems to find out of who is the owner of the particular file lingering around.

Print C-Style backslash character (\n, \t, \r etc.) for non-printable and special characters.
```console{linenos=false}
ls -l -b
```
- `--escape`/`-b` flag prints C-Style backslash characters

![ls -l -b](gnu-core-utils-part1-11.webp)
![ls -l | Without Escape Characters](gnu-core-utils-part1-12.webp)

C-Style character map:

| Escape |      Meaning      |
|:------:|:-----------------:|
|   \n   |      Newline      |
|   \t   |        Tab        |
|   \r   |  Carriage Return  |
|  \\\   | Literal Backslash |
|   \0   |  Null character   |
|  \040  |       Space       |

### Symbolic Link Listings

Follow the symbolic link listed on the command line:
```console{linenos=false}
ls -l -H <SYMLINK>
```
- The flags `--dereference-command-line` and `-H` serve the same purpose.
- Only follow the symbolic links if file/DIR is given in CLI argument

![-H flag require CLI argument](gnu-core-utils-part1-13.webp)


Follow the link and show information for the file itself not the symbolic link. This means `ls` will follow the link and display information about the target file or directory, not the link itself.
```console{linenos=false}
ls -l -L
```
- The flags `--dereference` and `-L` are the same.

![Original files info when given as CLI argument](gnu-core-utils-part1-13.webp)
![Target File Info | Remaining are DIRs](gnu-core-utils-part1-14.webp)

### Print Size Information

Print allocated size of each file in blocks:
```console{linenos=false}
ls -s
```
- `--size`/`-s` shows the file size in bytes (blocks) which are 1024 bytes (1 KiB) by default.

You can mention the specific unit yourself:
```console{linenos=false}
ls -s --block-size=M
```
- K, M, G etc. are the powers of 1024(binary) or prefixes like KiB=K, MiB=M, GiB=G and so on.
- KB, MB, GB etc. are the multiples of 1000 (decimal)

To show human-readable size (binary) with flags like `-s` and `-l`:
```console{linenos=false}
ls -sh
```
- `--human-readable`/`-h` are the same

The flag `--si` prints the size information like `-h` but in decimals (powers of 1000):
```console{linenos=false}
ls --si -l
```
- The `--si` flag should be used with either `-s` or `-l` flag

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
- `-t` Sort the newest modified file first
> [!TIP] Tip
> The sort by `-t` and `-t` with `--time=mtime` give the same results. The `-t` alone defaults to the last modification time.

Sort by time, based on birth time (creation time):
```console{linenos=false}
ls -t --time=birth
```
- Combining with `-l` shows the creation/birth time
- It will print newly created item first, flag `-r` can show the oldest birth first by reversing the order.

![Showing oldest created entry first](gnu-core-utils-part1-4.webp)

Sorting based on when a file is last accessed(no modification or write):
```console{linenos=false}
ls -lt --time=atime
```
- `-u` The shorter version of `--time=atime`

![Last accessed entries with timestamp](gnu-core-utils-part1-5.webp)

> [!CAUTION] INFO
> On modern Linux systems, `noatime` mount option reduces the disk I/O operation by cutting down the access time updates. While `relatime` mount option only update access metadata under certain conditions.

Sort by last metadata change time:
```console{linenos=false}
ls -lt --time=ctime
```
- The flag`--time=ctime` can be substituted to `-c`

> [!TIP]
> It records changes to ownership and permissions along with creation and edit timestamps. While `--time=mtime` only records creation and edit timestamps.

![Showing ownership change listed first](gnu-core-utils-part1-6.webp)

### Timestamps Long Listing

> [!NOTE]
> Timestamp information is only shown when using the long listing format with the flag `-l`, so all the below commands must be run with `-l` flag to actually see what's happening with the timestamp information.

#### Timestamp Versions

You can see a different timestamp when listing with `-l` flag, which by-default shows the last modification times. You can achieve this without `-t` command which by-default sorts entries based on `--time=WORD` command. 

Let's list a last access time stamp which the files are last accessed by an editor, `cat`, or commands without modifying the entries order:
```console{linenos=false}
ls -l --time=atime
```
- The short version is `-u`

Print the last metadata change timestamp:
```console{linenos=false}
ls -l --time=ctime
```
- The flags `--time=ctime` and `-c` serve the same purpose


#### Timestamp Display Properties

By default, long listing shows the `locale` timestamp:
```console{linenos=false}
ls -l --time-style=locale
```
![locale timestamps](gnu-core-utils-part1-8.webp)

To show full date and time with minutes precision:
```console{linenos=false}
ls -l --time-style=long-iso
```
![long-iso timestamps](gnu-core-utils-part1-9.webp)

To list timestamps with nanosecond precision and time zone
```console{linenos=false}
ls -l --time-style=full-iso
```
-  The flags `--time-style=full-iso` and`--full-time` serve the same purpose

![full-iso timestamps](gnu-core-utils-part1-10.webp)

### IGNORE Entries via Pattern Matching

Basic ignore via `-B` flag:
```console{linenos=false}
ls -B
```
- `--ignore-backups`/`-B` don't list implied entries ending with `~`
- The `~` at the end of the file is used by different text editors and other programs to store backups of files.

Advance pattern matching:
```console{linenos=false}
ls --ignore=PATTERN
```
- `-I PATTERN`/`--ignore=PATTERN` are the same

Basic Glob Patterns:

| Pattern |        Matches        |
|:-------:|:---------------------:|
|   \*    | Anything (any length) |
|    ?    | Any single character  |
| \[abc]  |     One of these      |
| \*.txt  |    Any `.txt` file    |

Hide all `.text` files:
```console{linenos=false}
ls -I *.txt
```

Hide all JSON backup files:
```console{linenos=false}
ls --ignore=*.json~
```

Hide all file1.txt, file2.txt and so on:
```console{linenos=false}
ls --ignore=file?.txt
```

Hide anything that has `oct` in their name anywhere:
```console{linenos=false}
ls --ignore=*oct*
```
- It's case-sensitive

### `ls` --- Exit Codes

Following are some useful exit codes:

<kbd>0</kbd> OK

<kbd>1</kbd> There is some minor problem, like subdirectory is not accessible etc.

<kbd>2</kbd> Serious issue, i.e., cannot access CLI argument

> [!NOTE]
> Modern Linux systems might just show the issue descriptively instead of an error code to simplify the troubleshooting process. To show an error code:
> `ls [argument] ; echo $?`

### Useful Tips

Show colored output:
```console{linenos=false}
ls --color=auto
```
- Shows different color for different entry types
- Can be combined with other commands

![Colored ls output](gnu-core-utils-part1-22.webp)

Show version information and exit:
```console{linenos=false}
ls --version
```

Distinguish between directories and files:
```console{linenos=false}
ls -F
```
- Shows `/` with DIRs

![Directories listing with /](gnu-core-utils-part1-7.webp)

Show help information:
```console{linenos=false}
ls --help
```

See manual pages:
```console{linenos=false}
man ls
```

Print index number of each file
```console{linenos=false}
ls -i
```
- `--inode`/`-i` print the index number

## `vdir` --- List Directory Contents

The command `vdir` is equivalent to `ls -l -b`; that is, by default files are listed in the long format and special characters are represented by C-Style backslash escape sequences.

![vdir](gnu-core-utils-part1-15.webp)

The advantage over `ls -l -b` is, `vdir` acts as a shorthand and chaining more flags becomes rather easy.

The size information (in powers of 1000):
```console{linenos=false}
vdir --si
```

Instead of writing:
```console{linenos=false}
ls -l -b --si
```

> [!TIP]
> You can chain other `ls` flags with `vdir`, i.e., `--time`, `--block-size`, `--full-time`, `--reverse`, `--ignore=PATTERN` and so on. The `vdir` command has basically all the same flags and options as `ls`.

## `realpath` --- Resolve Symlink Paths

The command `realpath` prints the resolved symbolic link paths.

Resolve symlinks as encountered (default):
```console{linenos=false}
realpath /path/to/file
```
- The flag `-P`/`--physical` prints the same information as `realpath` alone. It defaults to this, so we don't need to write the whole flag.

The flag `-E`, all but the last component must exist (default):
```console{linenos=false}
realpath -E /path/to/file
```
- `--canonicalize`/`-E`
- If parent directory exists, it will show the path as is, doesn't matter if symlink file exists or not
- That's the default flag for `realpath`

![ghost.txt doesn't exists but still prints the path](gnu-core-utils-part1-16.webp)
![Default behavior is same as flag -E](gnu-core-utils-part1-17.webp)

It will only throw error if parent directory for the given file doesn't exist
- In our examples' ghost.txt doesn't exist but the parent directory `/tmp`exist, so no error
- In the following picture, parent directory `../ghost/` doesn't exist, so `-E` flag throws an error.

![](gnu-core-utils-part1-20.webp)

Shows an error when the file/link doesn't exist:
```console{linenos=false}
realpath -e /path/to/file
```
- Only prints the path, if symbolic link exists for the given path.
- The flags `-e`/`--canonicalize-existing` are the same.

![All components of the path must exist](gnu-core-utils-part1-18.webp)
![The whole path is valid](gnu-core-utils-part1-19.webp)

The `-m`/`--canonicalize-missing` flag doesn't resolve anything, so no path or file existence is needed.
```console{linenos=false}
realpath -m /path/to/file
```

![The whole path doesn't exist](gnu-core-utils-part1-21.webp)

> [!NOTE]
> There is a `readlink` command, which has almost similar functionality. It might be useful in shell scripts. [Check out](https://man.archlinux.org/man/readlink.1.en) the docs.

## References

- [GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html#ls-invocation) --- GNU Official Manual
- [GNU Core Utilities](https://en.wikipedia.org/wiki/GNU_Core_Utilities) --- Wikipedia
- `man` PAGES