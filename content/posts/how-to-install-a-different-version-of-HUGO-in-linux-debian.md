---
title: "Upgrading Hugo on Linux: A Step-by-Step Guide to Any Version You Need"
date: 2023-03-16T17:39:56-07:00
ShowToc: true
author: Rodney Maiato
tags: ["hugo"]
---
Before we dive into the details, here's the code you'll need to upgrade Hugo to a specific version using dpkg:

```bash
# Uninstall the existing Hugo version
sudo apt autoremove hugo

# Download your desired Hugo version from the Hugo releases page, e.g., 0.111.3
# Replace 'hugo_extended_0.111.3_linux-amd64.deb' with the file you downloaded
sudo dpkg -i 'hugo_extended_0.111.3_linux-amd64.deb'

# Verify your Hugo version
hugo version
```

## Introduction:
In this tutorial, we'll explore how to upgrade Hugo on your Linux system to a specific version of your choice using dpkg. Linux may be known for its user-friendliness, but updating certain software, like Hugo, can sometimes be a perplexing task. We'll delve into an alternative method that provides you with the freedom to select and install any Hugo version you require, ensuring you stay up-to-date with the latest features and improvements.

## The Hugo Dilemma:
If you're new to Linux, you've probably found it surprisingly easy to use for most tasks. However, every now and then, you'll encounter something that appears deceptively simple but turns into a puzzling challenge. One common challenge is updating Hugo to a newer version, especially if you follow tutorials or documentation that reference different Hugo versions.

I recently faced this issue while following a YouTube tutorial on creating Hugo themes. The tutorial was more than a year old, and I noticed that my Hugo version was significantly outdated compared to the version used in the tutorial. The tutorial used Hugo version 0.111.3, while my system was stuck on version 0.92, dating back to February 2022. I attempted the usual "sudo apt update" and "sudo apt upgrade" commands, but Hugo remained at its old version.

## The Alternative Installation Method:
The default way to install Hugo on Linux is by using the Advanced Package Tool (APT) with the command "sudo apt install hugo." APT is a package manager that efficiently handles package installations, upgrades, and removals. While it's a reliable method, it may not always provide the latest Hugo updates as quickly as you'd like.

For those who want to take matters into their own hands and choose a specific Hugo version, the Debian Package Management System (dpkg) comes to the rescue. While the dpkg method involves a few extra steps, it's a flexible way to ensure you get the exact Hugo version you need.

## Here's a step-by-step guide to updating Hugo to the version of your choice:

1. ### Uninstall Your Existing Hugo Version:
   To clear the path for the new Hugo version, uninstall your existing installation by running the following command:
   ```bash
   sudo apt autoremove hugo
   ```

2. ### Download Your Desired Hugo Version:
   Visit the official Hugo releases page at [gohugo.io/hugo/releases](https://gohugo.io/hugo/releases) and choose the Hugo version you want to install. Simply click on your chosen version, and it will typically end up in your Downloads folder.

3. ### Install Your Chosen Hugo Version with dpkg:
   Once you've downloaded the Hugo version you desire, open your terminal and run the following command. Make sure to replace the file name with the one you downloaded:
   ```bash
   sudo dpkg -i 'hugo_extended_0.111.3_linux-amd64.deb'
   ```

4. ## Follow the Prompts:
   The installation process will prompt you for any necessary actions or confirmations. Follow these prompts to complete the installation.

5. ## Verify Your Hugo Version:
   After installation, you can double-check that you have successfully updated to the version you wanted by running:
   ```bash
   hugo version
   ```

## Conclusion:
Upgrading Hugo on your Linux system to any specific version you need is a straightforward process, thanks to the flexibility of the dpkg method. With this alternative approach, you can ensure that you have the latest features and improvements, making your Hugo experience as up-to-date as possible. Whether you're following tutorials or working on your projects, this method allows you to have the right tools at your disposal, no matter how old or new they may be.
