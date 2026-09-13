---
creation_date: 2025-11-30
tags:
challenge: CrackTheGate1
category: Web Exploitation
difficulty: Easy
platform: PicoCTF
solved: true
---
# Crack The Gate 1

## 1. Description
> [!quote] We’re in the middle of an investigation. One of our persons of interest, ctf player, is believed to be hiding sensitive data inside a restricted web portal. We’ve uncovered the email address he uses to log in: `ctf-player@picoctf.org`. Unfortunately, we don’t know the password, and the usual guessing techniques haven’t worked. But something feels off... it’s almost like the developer left a secret way in. Can you figure it out?

## 2. Solution
We were given a link to a login page, we already have the email address but what is the password? 

Looking at the page source, it contains an encoded comment. 
`ABGR: Wnpx - grzcbenel olcnff: hfr urnqre "K-Qri-Npprff: lrf" `
I tried to decode using ROT 13 and I got 
`NOTE: Jack - temporary bypass: use header "X-Dev-Access: yes" `

Using burpsuite I intercepted the request and added a new Header `X-Dev-Access: yes` that allows login access without password. 

Logging in shows an alert containing the flag

##  3. The Flag
> [!SUCCESS] Flag `picoCTF{brut4_f0rc4_1a386e6f}`

## References 

