---
title: "SSH config file"
date: 2025-02-25
draft: false
description: "ssh config file"
tags: ["snippet", "ssh"]
---

## SSH Local Port Forwarding

- -f run in the background
- -N does not open a shell window
- -L local port forwarding

`$ ssh -f -N -L 8000:yahoo.com:80 root@foo`

## SSH Remote Port Forwarding

> to use this open /etc/ssh/sshd_config and add "GatewayPorts yes" and restart ssh service
> -R remote port forwarding

`$ ssh -R 8000:localhost:3000 root@foo`

## SSH config

>  edit ~/.ssh/config

    Host foo
        HostName 192.168.1.7
        User root
        IdentityFile ~/.ssh/id_rsa
        Port 22


`$ ssh foo`

## SSH escape sequences and codes

- `Ctrl+Z` send ssh connection to the background
