---
title: "How to Create a Gitignore File for a Hugo Site"
date: 2023-03-17T07:12:52-07:00
draft: false
---
A requirement to being capable of creating a useful gitignore file is having a good understanding of the  hugo directory structure.

Knowing which files need to be tracked means you know what the files do during the build process.

My `.gitignore` file contains these lines:

```git
/public/
/resources/
.hugo_build.lock
```
