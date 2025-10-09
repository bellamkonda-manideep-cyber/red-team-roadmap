# Week 2: Advanced Recon, Web Discovery & Metasploit Basics


## Overview
**Objective:** Move from basic recon (Week 1) to deeper enumeration, vulnerability discovery, and safe exploitation inside your lab. You will master Nmap scripting, directory brute-forcing, automated web scanning, and Metasploit usage on Metasploitable2.


**Time Commitment:** 1.5–3 hours per day.


**Tools:** Nmap, Nikto, Gobuster, Dirb, SecLists, sqlmap, Metasploit, curl, nc, openssl


---


## Day 1 — Nmap Deep Scanning & NSE


### Commands
```bash
export TARGET_IP=192.168.56.101 (Your Metasploitable2 IP Address.)
nmap -sS -p- -T4 -Pn -sV -sC --reason -oN ~/week2_day1_nmap_full.txt $TARGET_IP
nmap -p 80,8080 --script=http-title,http-headers,http-enum -oN ~/week2_day1_http_nse.txt $TARGET_IP
nmap -p 139,445 --script=smb-enum-shares,smb-os-discovery,smb-vuln* -oN ~/week2_day1_smb_nse.txt $TARGET_IP
```


### Expected Output
```
PORT STATE SERVICE VERSION
21/tcp open ftp vsftpd 2.3.4
22/tcp open ssh OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
80/tcp open http Apache httpd 2.2.8 ((Ubuntu) DAV/2)
445/tcp open microsoft-ds Samba smbd 3.X
```


**Verify:** Output saved in `~/week2_day1_nmap_full.txt`. Check for known vulnerable versions.
