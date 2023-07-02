---
title: Rsync Cheatsheet
date: 2023-07-01T13:37:00.000Z
description: Some handy rsync commands for working with remote vps using ssh.
tag: web development
author: Isaac
---

I've got a few rsync commands I use as reference. They include a lot of options that I appreciate and use often. I'm putting them here for my own reference, but also for anyone else who might find them useful.

I usually use rsync between remote machines, so these commands are written with that in mind.  I'm using a VPS, so I'm using ssh to connect to the remote machine.  If you're using a different method, you'll need to adjust the commands accordingly. For example if your using rsync across directories on the same machine, you just need the paths to the directories, you can exclude the ssh info.


### Send code updates to server

```bash
rsync -zaP --exclude='node_modules/' --exclude='.git'  ~/local-code-folder/ -e 'ssh -p <PORT-NUMBER>' user@<YOUR-VPS-IP-ADDRESS>:/remote-code-folder/
```


### Download files

```bash
rsync -zaP --exclude='node_modules/' --exclude='.git'  user@<YOUR-VPS-IP-ADDRESS>:/remote-code-folder/ ~/local-code-folder/
```

An example with all the flags included: 

```bash
rsync -zaP --exclude='node_modules/' --exclude='.git' --delete --dry-run ~/local-code-folder/ -e 'ssh -p <PORT-NUMBER>' user@<YOUR-VPS-IP-ADDRESS>:/remote-code-folder/
```


## Explanation

Rsync is a sweet tool to synchronize files in two seperate folders.  I'm gonna stay 30,000 feet here; it's great, and can be trusted. You can find nitty gritty details online.

For my use case, I'm synchronizing a npm repo. There is a directory called "node_modules" that I do NOT want to synchronize, so I have added a flag to ignore that, as well as the .git folder to avoid any complications there.

As for the flags, the `-zaP` flags do the following: 

-z              compress file data during the transfer

-a             archive mode; (Recursive, Preserves file ownership, copies sym links, etc.)

-P             displays progress bar

You can also add these flags if desired:

--delete        delete extraneous files from dest dirs

--dry-run       perform a trial run with no changes made

--exclude       exclude files matching pattern
