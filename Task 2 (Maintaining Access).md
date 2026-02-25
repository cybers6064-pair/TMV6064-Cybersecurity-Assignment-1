# Task 2: Maintaining Access  
## Disclaimer  
**This project is for educational purposes only. All testing was performed in a
controlled environment or on authorized targets.

## Introduction  
**Maintaining Access** phase or also known as **persistence** in the target system, involves hacker that installs software or make changes to the target machine in order to access the target over time. Hence, allowing the hacker to stay connected with the target machine which prevent the need to start the process from scratch for the same target― *geeksforgeeks*  

**Objective:** To demonstrate post-exploitation techniques for maintaining access on a compromised target server using three distinct tools (*Webshells; Weevely; Cryptcat*).  
**Target Environment:** *Kali Linux* (Attacker) and Vulnerable Target Application (Damn Vulnerable Web Application, *DVWA*)  

## Tool 1: Webshells  
Webshell consist of a single-line script that executes system commands through web browser URL parameters. They are written in web programming languages such as *PHP, Java, Perl* and others. An attacker can control the script and a *command injection vulnerability* occurs.  

**Key Features Used:**  
- Simplicity: Small enough to be hidden inside legitimate website code without drawing attention.
- Firewall Evasion: Traffic blends in perfectly with normal HTTP/HTTPS web browsing
- 

