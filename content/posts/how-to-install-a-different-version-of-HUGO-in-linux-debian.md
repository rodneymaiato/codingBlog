---
title: "How to Install a Different Version of Hugo in Linux Debian"
date: 2023-03-16T17:39:56-07:00
ShowToc: true
author: Rodney Maiato
tags: ["hugo"]
---

Being new to Linux, I find it surprisingly easy to use. But once in a while, something you would expect to be super simple, turns out to be a brain teaser. For example, I couldn't figure out how to upgrade to the latest version of Hugo. 

During a youtube tutorial on how to create themes with Hugo, I noticed that my version of hugo was older than the version used in the tutorials. And some of those videos were over a year old.

So, I ran `sudo apt update` and `sudo apt upgrade`.

Then I ran `hugo version` and still no upgrade. At the time of this writing hugo was at version 0.111.3 and I was still on version 0.92 which dated back to Feb 2022.

## An Alternative Way to Install Hugo

The official installation instructions for Hugo found on [gohugo.io](https://gohugo.io) is to enter the following command: `sudo apt install hugo`. It's usually the best way to install any package. 

`Apt` (Advanced Package Tool) is a package manager used for installing, upgrading and uninstalling packages. It does a very good job and the recommended way to install packages.

But, packages found in that repository aren't always updated as quickly as some people would like.

The alternative is to use `dpkg` (Debian Package Management System). You can read the manual in your terminal window with `man dpkg`.

Installing the version of Hugo that is currently available through the advanced package tool involves one simple command: `sudo apt install hugo`.

With the Debian Package Management System `dpkg`, there are a few more steps, but nothing too complicated.

## Uninstall Hugo Before Beginning to Install a New Version

Enter the following command:

```bash
sudo apt autoremove hugo
```

## Steps to Install a Different Version of Hugo With `sudo dpkg -i` 

1. Go to [gohugo.io/hugo/reases](https://github.com/gohugoio/hugo/releases)

2. Download the Hugo version that you would like to install by simply clicking on the version which should end up in your `Downloads` folder.
3. Enter the following command to install the Hugo version: `sudo dpkg -i`  followed by the name of the `.deb` file that you downloaded. For me it was this: 

```bash
sudo dpkg -i 'hugo_extended_0.111.3_linux-amd64.deb'
```

4. Follow the prompts and you're done.
5. Run `hugo version` to check that you have the version you wanted.