---
title: Input Injection
category: Binary Exploitation
difficulty: Medium
date: 2026-09-03
tags:
status: Ongoing
---
# Crack the Power

## 1. Challenge Description

> [!quote] We received an encrypted message. The modulus is built from primes large enough that factoring them isn’t an option, at least not today. See if you can make sense of the numbers and reveal the flag. Download the [message](https://challenge-files.picoctf.net/c_amiable_citadel/4f048da6d1e55c5459752585d7c58f12d94f2b02fbe0fe739ad81716dc9191d0/message.txt).

### Solution

```
#!/usr/bin/env python3
# Final exploit script
from pwn import *

r = remote('target', 1337)
# payload here
r.interactive()
```

##  The Flag

> [!SUCCESS] Flag `ctf{FLAG_GOES_HERE}`