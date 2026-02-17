---
draft: true
title: 'Bash Shell Configuration'
imageNameKey: 'bash-shell-configuration'
date: '2026-02-17T10:07:12+05:00'
description:
author: "AbuTurab"
image: 'bash-shell-configuration-cover.webp'
tags: 
categories:
keywords:
lastmod: ''
---

Bash is a default shell on all almost every major Linux distro. Let's see how we can make our life easier while working in the terminal.

> [!CODE]- Click here to view my .bashrc
> You can just add it to your `.bashrc` and start using, if you know what are you doing.
> ```bash
> # Bash History
> HISTSIZE=10000
> HISTFILESIZE=200000
> ## HISTFILE location
> export HISTFILE="$HOME/.bash_history"
> ## Ignore duplicates
> HISTCONTROL=ignoredups:erasedups
> ## Append history
> shopt -s histappend
> ## Clear, Reload and Append
> PROMPT_COMMAND="history -a; history -c; history -r"
>
> # Smarter TAB Completion
> bind -s 'set completion-ignore-case on'
>
> # Custom Environment Variables
> #export PATH=~/.cargo/bin/:$PATH
> #export PATH=~/.npm-global/bin:$PATH
> #export PATH=~/.local/bin:$PATH
> #export EDITOR="nvim"
> #export BUNDLE_PATH=~/.gems
>
> # Custom Aliases
> ## Smarter Copy and Move
> alias cp='cp -vi'
> alias mv='mv -vi'
> ## Better ls command
> alias ls='ls --color=auto'
> alias ll='ls -l --color=auto'
> alias la='ls -al --color=auto'
> alias lah='ls -alh --color=auto'
> ## Even Prettier ls (requires lsd)
> #alias ls='lsd'
> #alias ll='lsd -l'
> #alias la='lsd -al'
> ## better cat
> alias cat='less -N'
> #alias cat='cat -n' # Pipe it to less
> ## bat: a (cat) with wings
> #alias cat='alias bat'
> #alias cat='alias batcat' #Debian-based systems
> ## rm 
> alias `rm` = `rm -vi`
> ## Even Better rm (trash)
> #alias rm='trash -vi' #needs trash-cli package
> ```
> > [!CAUTION] ''
> > This bashrc might break your shell, as some configurations need extra packages to be first installed on the system. I have commented out all those settings/aliases which require extra packages. 

Now, let's explain the configuration:

## Bash History

To select a bash history file:
```bash{linenos=false}
export HISTFILE="$HOME/.bash_history"
```

```bash{linenos=false}
HISTSIZE=10000
HISTFILESIZE=200000
```
- `HISTSIZE` Keeps up to 10,000 commands in the session memory
- `HISTFILESIZE` Keeps up to 100,000 commands in the history file

### Avoid Duplicates

To avoid duplicates in your history file:

```bash{linenos=false}
HISTCONTROL=ignoredups:erasedups
```

### Append and Update History

When multiple terminal windows are opened, each session's won't overwrite the others.

```bash{linenos=false}
shopt -s histappend
```

To append latest command, clear, reload history file back into memory:

```bash{linenos=false}
PROMPT_COMMAND="history -a; history -c; history -r"
```

- `history -a` Append the latest command(s) from the current session to the history
- `history -c` clear the in-memory history of the current shell
- `history -r` read the history files back into memory


## <kbd>TAB</kbd> Completion

When you try to change directory using `cd`, and hit <kbd>TAB</kbd>, it completes the path for you. Default is case-sensitive completion, let's change it:

```bash{linenos=false}
bind -s 'set completion-ignore-case on'
```

Now using shell commands when you write `dow` and hit <kbd>TAB</kbd>, it will autocomplete to `Download` ignoring the case.

## Custom Environment Variables

Some necessary variables for development:

```bash{linenos=false}
export PATH=~/.cargo/bin/:$PATH
export PATH=~/.npm-global/bin:$PATH
export PATH=~/.local/bin:$PATH
export EDITOR="nvim"
export BUNDLE_PATH=~/.gems
```

## Custom Aliases

You can set custom aliases to have some quality of life improvements:

### `cp` and `mv`

```bash{linenos=false}
cp -vi [Source] [Destination]
```

```bash{linenos=false}
mv -vi [Source] [Destination]
```

- `--verbose`/`-v` Explains what is being done
- `--interactive`/`-i` Prompt before overwrite

Let's make them an alias:

```bash{linenos=false}
alias cp='cp -vi'
alias mv='mv -vi'
```

So, it will show what are you copying, and before overwriting anything it will ask for confirmation \[Reply with `y` to continue].

### `ls` Or `lsd`

By default, `ls` output is not colorized.

Let's make it better:
```bash{linenos=false}
alias ls='ls --color=auto'
```

![](bash-shell-configuration-1.webp)

Other improvements:

```bash{linenos=false}
alias ll='ls -l --color=auto'
alias la='ls -al --color=auto'
alias lah='ls -alh --color=auto'
```

- `-l` Use a long listing format
- `-a`/`--all` show hidden files and DIRS (starting with `.`)
- `-h`/`--human-readable` Print human-readable sizes

We can go a step further and replace `ls` with `lsd`, which is even prettier with icons support.

First install `lsd` package available on Fedora (`dnf`), Debian/Debian-based distros(`apt`), and Archlinux(`pacman`), with your respective package manager.

```bash{linenos=false}
alias ls='lsd'
alias ll='lsd -l'
alias la='lsd -al'
```

We don't need `-h` as it's the default behavior for `lsd`
![](bash-shell-configuration-2.webp)

### `cat` OR `bat`

The `cat` command output what's in the file, without any beautification. Lets:
```bash{linenos=false}
alias cat='less -N'
```
- `less` Interactively show contents of the files
- `-N`/`--LINE-NUMBERS` Causes a line number to be displayed at the beginning of each line.

> [!INFO] ''
> The `less` command doesn't support concatenation of outputs. If you rely on the feature use:
> 
> ```bash{linenos=false}
> cat -n FILE1 | less
> ```
> - `|` Pipes the output of previous command to next command

The more modern option is `bat`, which shows pretty colors with numbering, header with filename, and interactive viewing. 

> [!INFO] ''
> You will need the `bat` package on your system.

```bash{linenos=false}
alias cat='alias bat'
OR
alias cat='alias batcat' #Debian-based systems
```

For full feature list [visit](https://github.com/sharkdp/bat).
![](bash-shell-configuration-3.webp)

### `rm` OR `trash`

The `rm` command deletes files or directories from the system.

```bash{linenos=false}
alias `rm` = `rm -vi`
```
- `-v`/`--verbose` Explain what is being done
- `-i` Prompt before every removal

The `rm` command directly removes the files from the system without first moving them to the trash/recycle bin.

A better way to remove files is using `trash-cli`. It moves files to the recycle bin, so any accidental deletion would be fine. It also removes directories to without any further flag/s needed. 
> [!INFO] '' 
> Please install `trash-cli` package first on your distro of choice.

```bash{linenos=false}
alias rm='trash -vi'
```