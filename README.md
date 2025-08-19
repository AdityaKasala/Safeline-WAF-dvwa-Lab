# SafeLine WAF + DVWA Home Lab
This lab demonstrates deploying SafeLine WAF to protect the Damn Vulnerable Web Application (DVWA) on Ubuntu Server. It covers setup of DVWA and SafeLine, performing SQL Injection and XSS attacks from Kali Linux, and observing real-time WAF blocking, showcasing practical web app security defense.

## Overview
This project documents a home cybersecurity lab featuring SafeLine Web Application Firewall (WAF) protecting the Damn Vulnerable Web Application (DVWA) on Ubuntu Server.

## Objectives
- Deploy DVWA on Ubuntu with Apache and MySQL
- Install and configure SafeLine WAF as a reverse proxy
- Demonstrate SQL Injection and XSS attacks blocked by SafeLine WAF
- Capture and analyze WAF logs and dashboard statistics

## Environment
- Ubuntu Server 22.04 LTS VM (Apache on port 8080)
- SafeLine WAF Docker containers (listening on port 80)
- Kali Linux VM for attack testing
- Bridged networking enabled for inter-VM communication

## Usage
- Access DVWA securely via SafeLine WAF at `http://192.168.1.215/`
- Perform SQLi and XSS attacks to observe SafeLine protections
- Check SafeLine dashboard for logged attacks and blocking events

## Structure
- [README.md](README.md) — This documentation
- [lab-notes.md](lab-notes.md) — Step-by-step commands, setups, and troubleshooting
- `screenshots/` — Visual proof including block pages and statistics

## Screenshots Highlights
- Access Forbidden page by SafeLine WAF on SQLi attempt
- SafeLine dashboard showing blocked requests
- Kali VM testing connectivity to DVWA Ubuntu Server

## Further Exploration
- Set up DNS with BIND or enhanced `/etc/hosts`
- Enable HTTPS with self-signed SSL certificates
- Use Kali tools like SQLmap and Burp Suite for advanced attacks
- Explore SafeLine advanced features: HTTP Flood defense, Auth Gateway, Custom Deny Rules

---

## How to Run
Follow `lab-notes.md` to replicate the environment and test procedures.

---
