---
title: "How to Setup the Official Hugo Module for Bootstrap 5 SCSS and JS"
date: 2023-10-29T17:56:08-07:00
author: Rodney Maiato
tags: ["hugo"]
draft: true 
---

To get started, head over to the official Hugo Bootstrap repository. You can find detailed instructions in the <a href="https://github.com/gohugoio/hugo-mod-bootstrap-scss#readme" target="_blank">README</a> file. 

The README assumes that you're already pretty experienced with Hugo modules. But if you're in the same boat as me and don't have a lot of experience with them, don't worry. I'm going to walk you through the setup step by step.

Now, let's dive into the process of setting everything up without a hitch. Here's a complete, easy-to-follow guide that will help you get things up and running smoothly. 

To use this guide, make sure that you have a Hugo site in development and that you have a Github repository set up.

## Step 1 - Initialize your project as a Hugo module 
You'll need to run `hugo mod init github.com/your username/repository name]` in your terminal followed by where your repository the URL of your repository. 

Once you run that code, a new file named `go.mod` will be created at the root of your project.

## Step 2 - Add the code for the Hugo Bootstrap module to your config file
Your project's configuration file will be named config.toml, or in recent hugo versions, the config file is named hugo.toml. The toml format is used by default, but it also accepts config files in yaml, or jason format. The code below is in .toml format. Convert the code accordingly if you prefer yaml or json format. 

Add the following code to your config.toml or hugo.toml file:
```
[module]
[[module.imports]]
path = "github.com/gohugoio/hugo-mod-bootstrap-scss/v5"
```
## Step 3 - Update the module that you just added
In step 2, you added the code for the module, but now you have to tell hugo to download the module to your project. Run `hugo mod get -u` in your terminal. Once completed, you'll have a new file at the root of your project named `go.sum` which contain the modules.

## Step 4 - Create the necessary files and folders for the SCSS and JS in the Assets Directory

## Step 5 - Add the the necessary CSS and JS links in the head of your project. 