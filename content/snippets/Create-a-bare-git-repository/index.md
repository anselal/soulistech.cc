---
title: "Create a bare git repository"
date: 2025-02-26
draft: false
description: "create a bare git repository"
tags: ["snippet", "git"]
---

```sh
$ mkdir gitrepo
$ chgrp -R <whatever group> gitrepo
$ chmod -R g+swX gitrepo
$ cd gitrepo
$ git init --bare <reponame.git>
```
