---
title: "How to Rename a Batch of Files in Numbered Sequence"
date: 2023-03-18T13:30:54-07:00
author: Rodney Maiato
tags: ["bash", "bash script", "rename"]
ShowToc: true
description: "Transform chaos into order with this incredible BASH script! 🚀 Rename your .jpg files effortlessly in a custom sequence. Say goodbye to cryptic names and hello to organized bliss! 💡🔄 #BASHMagic #FileOrganization #TechTips"
---
To rename files in numbered sequence, use a simple Bash script in the directory.

```bash
#!/bin/bash

# Step 1: Choose a prefix
read -p "Choose a prefix: " prefix

# Initialize a counter
i=1

# Step 3: Use a for loop to iterate through the files
for file in *; do
  # Step 4: Use the mv command to rename and printf to format
  mv "$file" "$(printf "$prefix"_%03d.jpg "$i")"
  i=$((i + 1))
done
```

## Solving Everyday Problems With BASH Scripts

Are you stuck with a bunch of .jpg files with cryptic names? Renaming them manually can be time-consuming, but with a simple Bash script, you can rename them in seconds.

**Let's imagine you wanted your to rename files with the following criteria:**

- A custom prefix
- Followed by an underscore
- Sequential numbering padded with leading zeros
- End with a .jpg extension

## Breaking Down the Solution - Step by Step

### Step 1 - Create a variable to store a prefix

In the script, we start by asking you to choose a prefix with the `read -p` command. This prefix is stored in a variable named "prefix." For example, if you enter "national_park," it becomes your chosen prefix.

### Step 2 - Initiate a counter

We declare a variable "i" to serve as a counter. In our example, we start numbering with 1, but you can modify it to start from any number you prefer.

### Step 3 - Use a for loop to iterate through all the files in your directory

A for loop is used to cycle through each file in the directory. The loop continues until all files have been processed.

### Step 4 - Use the mv command to rename and printf to format

We use the `mv` command to rename each file. The new name is constructed using `printf`. The `%03d` format specifier pads the variable "i" with leading zeros to ensure the numbers have the desired format.

So there you go! With this script, you can quickly and efficiently rename multiple files in your directory with a custom prefix and sequential numbering. It's a time-saver for tasks like organizing your image files.