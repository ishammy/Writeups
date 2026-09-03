---
title: Pickle Rick
category: TryHackMe
difficulty: Easy
date: 2026-09-03
tags:
  - Web
  - SQLi
  - Linux
  - PrivEsc
summary: Uwuga
---

# Pickle Rick

## Description
A brief description of what the challenge or machine is about.

- **Target IP:** `10.10.10.10`
- **Objective:** Obtain user and root flags.

---

## 1. Reconnaissance & Scanning

We begin by scanning the target host using `nmap`:

```bash
nmap -sC -sV -p- 10.10.10.10 -oN nmap_scan.txt
