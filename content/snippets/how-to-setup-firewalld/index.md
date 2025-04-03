---
title: "How to setup firewalld"
date: 2025-04-03
draft: false
description: "firewall-cmd commands"
tags: ["snippet", "firewalld"]
---

## 1. Checking current firewall rules

`$ sudo firewall-cmd --list-all`

This will show:

- Active zones
- Services allowed
- Ports opened
- Other rules

## 2. Adding rules

### A. Add a service (Predefined in firewalld) 

```sh
$ sudo firewall-cmd --zone=public --add-service=http --permanent
$ sudo firewall-cmd --zone=public --add-service=https --permanent
```

- `--zone=public` → Specifies the firewall zone (default: public)
- `--add-service=http` → Allows the HTTP service
- `--permanent` → Makes it persist after a reboot

### B. Add a specific port

```sh
$ sudo firewall-cmd --zone=public --add-port=8080/tcp --permanent
$ sudo firewall-cmd --zone=public --add-port=3478/udp --permanent
```

- `8080/tcp` → Opens TCP port 8080
- `3478/udp` → Opens UDP port 3478

## 3. Removing rules

### A. Remove a service

`$ sudo firewall-cmd --zone=public --remove-service=http --permanent`

### B. Remove a specific port

`$ sudo firewall-cmd --zone=public --remove-port=8080/tcp --permanent`

## 4. Applying changes

After adding/removing rules, reload firewalld to apply changes:

`$ sudo firewall-cmd --reload`

## 5. Checking open ports & services

`$ sudo firewall-cmd --list-services`
`$ sudo firewall-cmd --list-ports`

## 6. Allowing services temporarily (Non-Persistent)

If you want to **temporarily** allow a port or service (will reset after a reboot of firewall reload):

```sh
$ sudo firewall-cmd --zone=public --add-port=9090/tcp
$ sudo firewall-cmd --zone=public --add-service=ftp
```

These rules **won't persist** after a reboot or firewall reload.

