---
title: "Rename a Batch of Image Files in Numbered Sequence | Shell Scripting"
date: 2023-03-18T13:30:54-07:00
author: Rodney Maiato
tags: ["bash", "bash script", "rename"]
ShowToc: true
---

I recently rewrote a bash script that was heavily inspired by a <a target="blank" href="https://stackoverflow.com/questions/3211595/renaming-files-in-a-folder-to-sequential-numbers">post</a> on Stack Overflow.

The goal to was to rename 175 files in a directory where all the images were named with random numbers like this:

```shellscript
4344385-4358439-4357383-n-7768345.jpg
```
to something more descriptive like this:
```shellscript
202301_01.jpg
```
Below is the BASH script that achieved it.

```shellscript
#!/bin/bash

read -p "Choose a prefix for your image files: " prefix

ls | cat --number | while read lineNumber fName; do mv --no-clobber "fName" "$prefix""_$lineNumber.jpg"; done

```

## Solving Everyday Problems With BASH Scripts

I like posting sketches and paintings on instagram. But I decided to close my instagram account in favor of posting on my own art blog. When I closed my account, I downloaded all my posts, and ended up with 20 directories containing images named like this.

```shellscript
4348385-8758439-9957383-n-7678399.jpg
```

Manually renaming all the photos was going to take hours. But I could write a bash script in minutes and running it would take seconds.

## The Logic Behind Renaming Files in Numerical Order 

I wanted the bash script to take any file name and rename it in such a way that:
-  add a custom prefix 
-  followed by an underscore
-  followed by a number that increments by one every time a new file is renamed 
- add a `.jpg` extension

Seems simple enough unless you're new to scripting in BASH. 

## Breaking Down the Solution - Step by Step 

### Step 1 - Create a variable to store a prefix

In my version of the script, I wanted to be able to rename image files with a meaningful prefix, so I started the script with a `read -p` command. 

```shellscript
read -p "Choose a prefix for your image files: " prefix
```
When I run the script, I get prompted to enter a prefix of my liking and it assigns what I enter to a variable I named `prefix`. If I enter "national_park", that's what gets stored in the `prefix` variable.

### Step 2 - List the files in your directory
The first part of the code is an `ls` command. When you run it, you can add flags like `-a` of `-l`. But there isn't a flag for  generating numbered lines with the `ls` command. Luckily, the `cat` command can.

### Step 3 - Generate numbered lines with the `cat` command

So what next? We need to pipe the output of `ls` into `cat --number`. If you had a directory with 10 `.jpg` files and ran `ls | cat --number`, it would look like this:

![image of ls | cat -n command](/cat_--number.png)

With `cat --number` you get two strings separated by a space. This will be important for the next command.

### Step 5 - Create a loop to read each line 

We need to process the output by the `ls | cat --number` command, one line at a time, so... we need to use a `while` loop.

### Step 6 - Assign each string from the `cat` output to a variable

The `read` command can take input and assign it to a variable. It can take more than one input. You can simply write `read input1 input2 input3` and will take 3 inputs as long as they are separated by a string.


What `cat --number` outputs is a line that contains two strings; the first is the line number and the second is the current file name. In my script, the `read` command takes in the two variable being piped in by the `ls | cat --number` command. 

### Step 7 - Use all three variables in the `mv` command to rename each file 

Use the `mv --no-clobber` command to rename files with the two variables that follow the `read` command. The `--no-clobber` flag ensures files don't get overridden.

In my script, I use very descriptive names so that I know exactly what those variables are storing, `lineNumber` and `fName` (file name). And in step 1, earlier, I took in the `prefix` variable.

All three variables are used in the `mv` command to perform the renaming of each file.

## Conclusion

Simple commands like `ls`, `cat`, and `mv` may seem limited on their own, but piping them into each other opens up a whole new world of possibilities. 