---
title: "How to Create a Gitignore File for a Hugo Site"
date: 2023-03-17T07:12:52-07:00
author: Rodney Maiato
tags: ["git"]
ShowToc: true
description: "Master the art of crafting the perfect .gitignore file for your Hugo site! 🚀 Uncover the secrets behind the directory structure and learn why certain files, like /public/ and .hugo_build.lock, deserve to be ignored. Streamline your Git repository for ultimate efficiency! 💻🔗 #Hugo #GitTips #CodeEfficiency"
---
Creating a useful gitignore file means you understand the hugo directory structure.

At the very least, a `.gitignore` file for a Hugo site should contain these lines:

```shellscript
/public/
/resources/
.hugo_build.lock

```

When you create a hugo site, it will create the following file structure in your project:

```shellscript
example/
├── archetypes/
│   └── default.md
├── assets/
├── content/
├── data/
├── layouts/
├── public/
├── static/
├── themes/
└── config.toml

```

Getting to know why Hugo creates these files and folders will help you understand which files or folders to add to your  `.gitignore` file. In other words, the files you want to tell git **not to track**.

##  The Reasons We Can Ignore Certain Files in Our Project

### The `public` Folder

The `public` folder is generated at build time. If you wanted to go live, you could simply run the `hugo` command. Hugo would do things like convert all your markdown pages to html pages and place them in your `public` folder.

So, you don't need to back up the `public` folder, you need to back up the files used to create it.

### The `resources` Folder

The `resources` folder is not created by default. You can still create a site with Hugo without a `resources` folder.

The Hugo documentation states that the `resources` folder is primarily used to cache files to speed things up at build time. And, stores Sass files to avoid a preprocessor being installed. Basically, the folder can be ignored.

### The `.hugo_build.lock` File

The `.hugo_build.lock` file is an empty and temporarily created by your system. I opened my `.hugo_build.lock` file in a text editor, and it was in fact empty.

It's use is to let other applications know that a resource is being used, should not be accessed. So, this file can also be ignored.

## Conclusion

Github repositories can get bloated unnecessarily. Understanding, what files are and what they do is a worthwhile investment of your time. A big reason we use Hugo is for speed. Why slow things down with unnecessary files.












