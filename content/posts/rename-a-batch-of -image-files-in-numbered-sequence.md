---
title: "How to Rename a Batch of Files in Numbered Sequence"
date: 2023-03-18T13:30:54-07:00
author: Rodney Maiato
tags: ["bash", "bash script", "rename"]
ShowToc: true
---

I wanted to rename 175 files in a directory where all the images were named with random numbers like this:

```shellscript
4344385-4358439-4357383-n-7768345.jpg
```
to something more descriptive like this:
```shellscript
202301_001.jpg
```
**Solution to the Problem**
```shellscript
#!/bin/bash

read -p "Choose a prefix: " prefix

for file in *; 
do
	mv "$file" "$(printf $prefix"_%03d.jpg" "$i")"
	i=$((i + 1))
done

```

## Solving Everyday Problems With BASH Scripts

I decided to close my instagram account in favor of posting on my own art blog. I downloaded all my posts, and ended up with a bunch of files named like this:

```shellscript
4348385-8758439-9957383-n-7678399.jpg
```

Manually renaming all the photos could take hours. But you can write a bash script in minutes that can do the job in one second.

## The Wish List for a Script to Rename Files in Numerical Order 

I wanted the bash script to take a file and rename with:
- a custom prefix 
- followed by an underscore
- assign sequential numbering padded with leading zeros
- and end with a `.jpg` extension

## Breaking Down the Solution - Step by Step 

### Step 1 - Create a variable to store a prefix

In my version of the script, I wanted to be able to rename image files with a meaningful prefix, so I started the script with a `read -p` command. 

```shellscript
read -p "Choose a prefix: " prefix
```
When I run the script, I get prompted to enter a prefix of my liking and it assigns what I enter to a variable I named `prefix`. If I enter "national_park", that's what gets stored in the `prefix` variable.

### Step 2 - Initiate a counter 

Declare a variable `i`  outside of a `for` loop and assign a starting number. In my case I chose to start numbering with zero, but you could easily assign it to a variable and set a prompt to `read` a starting number at run time.

### Step 3 - Use a for loop to iterate through all the files in your directory

The `for` loop will iterate through each file and perform an action on every file. In my case, each time the loop cycles to the next file, I rename the file with a `mv` command. When there are no files left in the directory to rename, the loop is stopped.

### Step 4 - Use the `mv` command to rename and `printf` to format 

The `mv` command use the `$file` variable declared in the `for` loop and renames it using the `printf` format.

### The `printf` command explained

The `printf` command uses `%03d` to format the variable `i` that is being used as a counter.

```shellscript
"$(printf $prefix"_%03d.jpg" "$i")"
```

`%d` treats the `i` variable as a digit and the `%03d` will give it the 3 zeros for padding the `i` variable.