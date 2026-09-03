---
title: "Challenge Name Here"
category: "TryHackMe" # e.g. "TryHackMe", "PicoCTF", "HackTheBox", "Hardware", "Web"
difficulty: "Easy"     # "Easy", "Medium", "Hard", or "Insane"
date: "2026-09-03"
tags: ["Web", "SQLi", "Linux", "PrivEsc"]
summary: "Brief 1-sentence overview of the challenge and how it was solved."
---

# Challenge Name Here

## Description
A brief description of what the challenge or machine is about.

- **Target IP:** `10.10.10.10`
- **Objective:** Obtain user and root flags.

---

## 1. Reconnaissance & Scanning

We begin by scanning the target host using `nmap`:

```bash
nmap -sC -sV -p- 10.10.10.10 -oN nmap_scan.txt
