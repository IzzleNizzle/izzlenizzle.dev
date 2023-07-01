---
title: Handy rsync Commands
date: 2021-04-30T13:37:00.000Z
description: Some handy rsync commands for working with remote vps using ssh.
tag: web development
author: Isaac
---

I found that my inexpensive VPS (Virtual private server) was too slow for remote coding. So I needed to find another way to update code quickly and easily. I will update code w/ rsync for now.

One day I want to set up some sort of deployment hooks and have the server auto update from a git repo, but until then, this is a quick and dirty way of updating my codebase.

#### send code updates to server

```bash
rsync -zapP --exclude='node_modules/' --exclude='.git'  ~/local-code-folder/ user@<YOUR-VPS-IP-ADDRESS>:/remote-code-folder/
```


#### download files

```bash
rsync -zapP --exclude='node_modules/' --exclude='.git'  user@<YOUR-VPS-IP-ADDRESS>:/remote-code-folder/ ~/local-code-folder/
```

You may want to consider using the `--delete` flag if you want the command to delete files that don't match in both directories. Be cautious with this, as it can delete a lot of files if you format the command wrong. 

There's also a `--dry-run` command that will show you what the command will do before it actually runs, this can help you avoid a lot of heartache. 

#### Explanation

Rsync is a sweet tool to synchronize files in two seperate folders.  I'm gonna stay 30,000 feet here; it's great, and can be trusted. You can find nitty gritty details online.

I'm excluding multiple directories. 

For my use case, I'm synchronizing a npm repo. There is a directory called "node_modules" that I do NOT want to synchronize, so I have added a flag to ignore that, as well as the .git folder to avoid any complications there.

As for the flags, the `-zapP` flags do the following: 

-z,              compress file data during the transfer

-a,               archive mode; (Recursive, Preserves file ownership, copies sym links, etc.)

-p,                 preserve permissions

-P,                  displays progress bar
