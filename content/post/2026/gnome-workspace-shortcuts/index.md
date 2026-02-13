---
draft: false
title: "GNOME Tips: Keyboard Shortcuts for More Than 4 Workspaces"
imageNameKey: 'gnome-workspace-shortcuts'
date: '2026-02-13T14:48:19+05:00'
description: "GNOME Settings app only allows assigning shortcuts to four workspaces. If you need to set shortcut for more than 4 workspaces you are own your own. This blog will tell 2 methods for assign workspace keybinds."
author: "AbuTurab"
image: 'gnome-workspace-shortcuts-cover.webp'
tags: ['GNOME', 'Linux']
categories: ['Blog']
keywords: ['extending gnome workspaces shortcuts past 4', 'overcoming gnome 4 workspaces shortcut limit', 'gnome tips and tricks', 'how to add shortcut for gnome workspaces, for more than 4 workspaces', 'how to add shortcut for gnome workspace 5 or 6 or 7']
lastmod: '2026-02-13T16:01:23+05:00'
---

From GNOME settings GUI, you can only add keyboard shortcuts for up to 4 workspaces.

If your workflow depends on more than 4 workspaces, you cannot add them via `gnome-control-center` aka **GNOME Settings** GUI.

There are two methods to add shortcuts for up-to 12 workspaces.

## dconf Editor

Open the `dconf Editor`, accept the risk associated with changing default settings via `dconf Editor`

![](gnome-workspace-shortcuts-1.webp)

Then navigate to:
<button>org</button> > <button>gnome</button> ><button>desktop</button> > <button>wm</button> > <button>keybindings</button>

Or click on `search` 🔎 icon, and put this in the search bar:

```text{linenos=false}
/org/gnome/desktop/wm/keybindings/
```

![](gnome-workspace-shortcuts-2.webp)

1. Click on `switch-to-workspace-5` (not available via `gnome-control-center`)

2. Turn off `Use default value`
3. Add your `Custom value` for key binding, i.e. <kbd>Super</kbd> + <kbd>5</kbd>
```text{linenos=false}
['<Super><Shift>5']
```

![](gnome-workspace-shortcuts-3.webp)

Then go back to `/org/gnome/desktop/wm/keybindings/` and click on `move-to-workspace-5`.

Using the previous steps, add this shortcut <kbd>Super</kbd> + <kbd>Shift</kbd> + <kbd>5</kbd> (To move focused app to workspace-5) to `Custom value` field.

```text{linenos=false}
['<Super><Shift>5']
```

## Terminal: Using `gsettings` (Recommended)

The more direct and easy method is using `gsettings` via terminal. This command is available on GNOME desktop by default.

- To assign a shortcut to switch to workspace#6 (Just an example you select any number up-to 12)

```console{linos=false}
gsettings set  org.gnome.desktop.wm.keybindings switch-to-workspace-6 "['<Super>6']"
```

Then you can use <kbd>Super</kbd> +<kbd>6</kbd> to switch to workspace#6.

- If you also want a shortcut to send apps to workspace#6, run in the terminal

```console{linenos=false}
gsettings set  org.gnome.desktop.wm.keybindings move-to-workspace-6 "['<Super><Shift>6']"
```

Now you can use <kbd>Super</kbd> + <kbd>Shift</kbd> + <kbd>6</kbd> key binding to move a focused app to workspace#6.

> [!TIP]''
> Repeat the same process for assigning shortcuts to more workspaces by substituting workspace numbers.