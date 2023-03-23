---
title: "How to Create a Gitignore File for a Hugo Site"
date: 2023-03-17T07:12:52-07:00
author: Rodney Maiato
tags: ["git"]
---
Creating a useful gitignore file means you understand the hugo directory structure.

When you create a hugo site, it will create the following file structure in your project:

```bash
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

Getting to know why Hugo creates these files and folders will help you understand which files or folders to add to your .gitignore file. In other words, the files you want to tell git to not track.

My `.gitignore` file contains these lines:

```git
/public/
/resources/
.hugo_build.lock
```

## Why I Don't Track These Files and Folders



### Why I Don't Track the Public Folder



