---
title: "iptables"
date: 2025-02-25
draft: false
description: "iptables"
tags: ["snippet", "iptables"]
---

## Update iptables rules

> 1. Set INPUT chain to default policy
> 2. Flush
> 3. Delete all chains
> 4. Restore iptables rules from file

```sh
$ iptables -P INPUT ACCEPT
$ iptables -F
$ iptables -X
$ iptables-restore < /etc/iptables.up.rules
```
