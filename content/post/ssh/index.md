---
title: ssh - cheat sheet
description: 
slug: ssh
date: 2023-11-16
image: matrix.jpg
categories:
    - Coding
tags:
    - Coding
---

## ssh key

Create ssh key

```bash {linenos=false}
    ssh-keygen -t ed25519 -C "example@example.com"
```

Copy public key to remote server

```bash {linenos=false}
    ssh-copy-id
```

## ssh agent

Use ssh-agent in remote server

```bash {linenos=false}
    exec ssh-agent bash
```

Start ssh agent

```bash {linenos=false}
    eval $(ssh-agent -s)
```

Add key to agent

```bash {linenos=false}
    ssh-add ~/.ssh/[key file]
```

Enable agent forwarding in the local ssh config

```bash {linenos=false}
      ForwardAgent yes
```

Enable agent forwarding in the remote ssh server config

```bash {linenos=false}
    vi /etc/ssh/sshd_config
```

## ssh server

Start and stop ssh server

```bash {linenos=false}
    systemctl status sshd
    systemctl start sshd
```

## jump host

```bash {linenos=false}
    ssh -J user@jumphost -R 8080:localhost:8080 user@hiddenhost
    ssh -R 8080:hiddenhost:8080 user@jumphost
```