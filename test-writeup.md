---
title: Challenge Name Here
category: TryHackMe
difficulty: Medium
date: 2026-09-03
tags:
summary: Directory
status: COMPLETED
---

# Challenge Name Here

## Description
A brief description of what the challenge or machine is about.
[[TryHackMe/PickleRick/index|index]]
- **Target IP:** `10.10.10.10`
- **Objective:** Obtain user and root flags.

---

## 1. Reconnaissance & Scanning

We begin by scanning the target host using `nmap`:

```bash
nmap -sC -sV -p- 10.10.10.10 -oN nmap_scan.txt
