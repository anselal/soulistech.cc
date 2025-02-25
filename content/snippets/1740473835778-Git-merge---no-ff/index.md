---
title: "Git merge --no-ff"
date: 2025-02-25
draft: false
description: "How to merge a branch without fast forward"
tags: ["snippet", "git"]
---

# How to merge a branch without fast forward

- Create a new branch named dev and check it out

```sh
$ git checkout -b dev
```

- Merge dev to master [https://i.sstatic.net/FMD5h.png]

```sh
$ git checkout master
$ git pull origin master
$ git merge --no-ff develop
```

![Git merge --no-ff](git-merge-no-ff.png)

