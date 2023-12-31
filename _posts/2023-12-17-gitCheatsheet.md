---
layout: post
title: Git Cheatsheet
subtitle: A Place For My Common Git Commands
#cover-img: /assets/img/path.jpg
#thumbnail-img: /assets/img/thumb.png
#share-img: /assets/img/path.jpg
tags: [git, cheatsheet]
author: Sam White
---

These are the commands that I commonly use in git. Some are used every day. Some are not used every day.

To view the state of the working directory:
````
git status
````

To add specific files into the staging area:
````
git add <filename>
````
You can add multiple files at once using this method:
````
git add <filename1> <filename2> <filename3>
````
To add all changes:
````
git add --all
````
This is the shorted version of the "--all":
````
git add -A
````
To specify the current directory:
````
git add .
````
To use git's interactive adding mode:
````
git add -i
````

To remove a file that you've staged:
````
git rm --cached <filename>
````
To remove all staged files:
````
git reset HEAD -- <directory-name>
````
