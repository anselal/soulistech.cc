---
title: "SSHFS"
date: 2025-03-03
draft: false
description: "sshfs"
tags: ["snippet", "sshfs"]
---

## Install SSHFS

```sh
$ sudo apt update
$ sudo apt install sshfs
```

## Mounting the Remote Filesystem

```sh
$ sudo mkdir /mnt/myblog
$ sudo sshfs -o allow_other,default_permissions user@your_other_server:~/ /mnt/myblog
```

> `allow_other` allows other users to have access to this mount

> `default_permissions` so that it otherwise uses regular filesystem permissions

## Permanently Mounting the Remote Filesystem

```sh
$ sudo nano /etc/fstab
$ user@your_other_server:~/ /mnt/myblog fuse.sshfs noauto,x-systemd.automount,_netdev,reconnect,identityfile=/home/user/.ssh/id_rsa,allow_other,default_permissions 0 0
```

> `fuse.sshfs` specifies the driver being used to mount this remote directory

> `noauto,x-systemd.automount,_netdev,reconnect` are a set of options that work together to ensure that permanent mounts to network drives behave gracefully in case the network connection drops from the local machine or the remote machine

> `0 0` signifies that the remote filesystem should never be dumped or validated by the local machine in case of errors. These options may be different when mounting a local disk

## Mount a WSL2 folder as a Network Drive in Windows 10+?

For some reason, although you can access a wsl folder from windows explorer, you cannot map it as network drive.

There is though a workaround to do this using the windows command prompt:

`subst z: \wsl.localhost\Ubuntu\mnt\myblog`

where is the windows drive letter.

To delete the mapped drive via the command line run the following:

`subst z: /d`

### Resources:

- https://www.digitalocean.com/community/tutorials/how-to-use-sshfs-to-mount-remote-file-systems-over-ssh
- https://superuser.com/questions/1738361/how-to-mount-a-wsl2-folder-as-a-network-drive-in-windows-10
