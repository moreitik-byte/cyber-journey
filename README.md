# Cyber Journey

My learning log as I move from general CS into cybersecurity.

## Goal
Building toward a career in cybersecurity — currently exploring offense vs defense to find my niche, aiming for freelance/bug bounty work and eventually a long-term security project.

## Progress Log

### 22 sept 2026 - Started
- Created TryHackMe account, began Pre Security path
- Created this repo

### 2 Oct 2026 - First lab solved
- Switched to PortSwigger Web Security Academy, chose web app security as my lane
- Installed Burp Suite Community Edition
- Started Server-side vulnerabilities - Apprentice path
- Started and solved my first lab: File path traversal, simple case
- **Vulnerability**: in this lab, the file path is built directly from a user-controlled parameter 'filename' with no validation, so anyone can change the parameter's value without being stopped
- **Attack method**: by using Burp Suite Community to check the server's traffic in the Proxy page, I can then find the requests containing the filename parameter and send them to the Repeater, which lets me modify the request and send the new request to the server to get the wanted response, which in our case was the password file "etc/passwd", which contained usernames and an 'x' placeholder instead of actual password data, indicating that the (hashed) passwords were stored elsewhere, typically in a file called /etc/shadow
- **Impact**: attacker can read any files he wants and get critical important information such as user credentials from a config file necessary to gain access to the database, or a session secret key which could let him forge sessions as any user including admins, or the source code itself to understand how the app works and find other bugs. Here we gained access to 'etc/passwd'
- **Fix**: reject '../' usages in the filename parameter, or restrict the type/pattern of value entered into the parameter
- **Learned**: how to use Burp's Proxy and Repeater to capture and modify requests

## Notes
(Writeups and notes from rooms/labs will go here as I progress)
