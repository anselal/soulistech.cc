---
title: "Allow nginx to act as a reverse proxy"
date: 2025-04-03
draft: false
description: "Allow nginx to make outbound connections"
tags: ["snippet", "selinux", "nginx"]
---


### Allow Nginx to Make Outbound Connections

Run this command to allow nginx to act as a reverse proxy:

`$ sudo setsebool -P httpd_can_network_connect on`

- P → Makes the change persistent across reboots.
- This allows all outbound connections from nginx (needed for proxy_pass).

