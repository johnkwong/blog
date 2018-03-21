---
layout: post
title: Can not access to a MySQL database remotely
tags: [database]
---
I try to access to MySQL database from remote client today. It show me this error message:  
```
Host 'xxx.xx.xxx.xxx' is not allowed to connect to this MySQL server
```
One of Solution is adding a new administrator account
```
CREATE USER 'newusername'@'localhost' IDENTIFIED BY 'newuserpassword';  
GRANT ALL PRIVILEGES ON *.* TO 'newusername'@'localhost' WITH GRANT OPTION;  
CREATE USER 'newusername'@'%' IDENTIFIED BY 'newuserpassword';  
GRANT ALL PRIVILEGES ON *.* TO 'newusername'@'%' WITH GRANT OPTION;
```
