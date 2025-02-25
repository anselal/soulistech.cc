---
title: "Extract *.msi file content"
date: 2025-02-25
draft: false
description: "extract msi content"
tags: ["snippet", "windows", "command line"]
---

## Extract *.msi file content

```sh
msiexec /a c:\testfile.msi /qb TARGETDIR=c:\temp\test 
```
