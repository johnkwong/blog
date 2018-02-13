---
layout: post
title: Port Forwarding in Windows
tags: [other]
---
Start the command prompt as an administrator and perform the following command:  
```
netsh interface portproxy add v4tov4 listenaddress=localaddress listenport=localport connectaddress=destaddress connectport=destport
```
List all current forwarding rules:  
```
netsh interface portproxy show all
```
To clear all current forwarding rules:  
```
netsh interface portproxy reset
```
