# Task 1: Reconnaissance
**By: Nur Zulaikha**

## Disclaimer
**This project is for educational purposes only. All testing was performed in a controlled environment or on authorized targets.

## Introduction
In Cybersecurity, reconnaissance refers to the initial phase of a cyber attack that involves systematic information gathering to identify potential vulnerabilities within a target system or network. Similar to military reconnaissance, it focuses on collecting intelligence or information prior to launching an attack. Moreover, reconnaissance can be either passive or active. Passive reconnaissance is where the attackers collects information without directly interacting with the target, while active reconnaissance involves direct techniques such as network scanning, port scanning, and vulnerability scanning. The process typically includes collecting publicly available and technical data, identifying the network scope and IP ranges, detecting security mechanisms such as firewalls or intrusion detection systems, locating open ports and access points, determining the services and versions running on those ports, and mapping the overall network architecture. This structured approach enables attackers to understand the target’s attack surface, identify entry points, and strategically plan subsequent exploitation activities (Sharadin, n.d.). For the purpose of Task 1: Reconnaissance, the demonstration fully follows active reconnaissance.

### Tools
- NMAP
- Recon-ng
- Hping3

### Objectives
To demonstrate preliminary information gathering about a target before taking action (such as conducting an investigation) by using three reconnaissance tools, for the purpose of a more effective and strategic planning prior to initiating the attack.

## 1. NMAP (Network Mapper)
NMAP (Network Mapper) is a free, open-source tool used for network discovery and is pre-installed in Kali Linux. It is utilized for security auditing, assisting administrators to identify active hosts, running services, operating systems, and firewall configurations on a network as it is essential to understand a target’s structure and potential vulnerabilities before taking further action. NMAP is designed to scan both large networks and single hosts, offering flexibility, robustness, and compatibility with major operating systems such as Linux, Windows, and macOS. Additionally, NMAP also includes additional tools like Zenmap for graphical interface support. Due to its effectiveness, ease of use, and strong community support, NMAP has become widely used for reconnaissance task (Nmap, n.d.). Furthermore, this demonstration dives deeper into the three key features of NMAP that explains why it is useful and effective for reconnaissance and security assessments, namely **Host Discovery**, **Port Scanning**, and **Service Detection**, and following the tutorial posted by Obialom (2023).

### 1.1 Host Discovery
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20host%20discovery.png)

NMAP can be utilized for **host discovery**, which is the initial phase of network reconnaissance. It aims to identify active systems in a target network (_Chapter 3. Host Discovery_, n.d.). The command `nmap -Pn -PE -sn <host IP>`, as shown in the image above, can be used for this purpose. The breakdown of the command is as follows:

- **-Pn**: used to assume host is active (for demonstration purpose and as suggested by NMAP)
- **-PE**: sends ping and wait for echo requests to determine whether the host is active
- **-sn**: disables port scanning to focus solely on identifying active hosts

This command is used to specifically verify whether a target system is active without initiating a full port scan, allowing reconnaissance tasks to focus on identifying active hosts before proceeding to more detailed analysis. Additionally, the host discovery feature narrows large IP ranges into a manageable list of active systems, which improves scanning efficiency. For this feature, NMAP also supports customizable probing techniques, including TCP, UDP, and ICMP scans, which allows users to tailor their approach according to specific objectives and network conditions, such as firewall or filtering bypassing (_Chapter 3. Host Discovery_, n.d.; Obialom, 2023). Therefore, this feature of NMAP enhances the effectiveness of preliminary information gathering during network reconnaissance, which is crucial as identifying active hosts allows professionals, such as security analysts, define the attack surface, prioritize targets, and support more strategic planning for subsequent scanning or security assessment tasks.


### 1.2 Port Scanning
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20port%20scanning.png)

Nmap is highly effective for **port scanning**, which is used to identify open ports on a target host. Port scanning is a fundamental technique for discovering accessible services running on a system. Nmap offers a wide range of scanning options and methods to collect detailed information about open ports on a target system or network (Obialom, 2023). For this demonstration, a basic port scanning tutorial provided by Nmap was followed (_A Quick Port Scanning Tutorial_, n.d.). The command used was the standard `nmap -Pn <host IP>`, which performs a default scan by resolving the hostname to an IP address. This command is used to ensure that port scanning continues even if the host blocks ping requests to enable the identification of open ports and exposed services that may represent potential entry points for further security assessment. By default, Nmap scans the top 1,000 most common TCP ports, as applied in this demonstration, though users can also specify particular ports to scan as needed such as the examples below (Obialom, 2023):

- **-p80:** scans only port 80

- **-p 1–100:** scans all ports within the range of 1–100

- **-p22, 23, 80:** scans ports 22, 23, 80

- **-p-:** scans all TCP ports

As illustrated in the image above, the output is presented in a human-readable format that displays the target IP address, port numbers, protocols, port states (open, closed, or filtered), associated services, and basic timing statistics. Non-open ports are consolidated as depicted by 'Not shown: 997 filtered tcp ports (no-response)' to minimize unnecessary output clutter and improve readability (_A Quick Port Scanning Tutorial_, n.d.). Therefore, this port scanning feature enabled by NMAP is crucial as identifying open ports and running services helps define the target’s attack surface, allowing security professionals to detect potential vulnerabilities and plan subsequent security assessments or mitigation strategies.


### 1.3 Service Version Detection
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20service%20detection.png)

NMAP also provides service version detection, emphasizing that accurate service and version detection is crucial for vulnerability assessments, identifying applicable exploits, and maintaining an accurate network inventory. NMAP’s version detection actively interrogates open ports with service-specific probes to reveal beyond the service type and version, but also additional details such as service configurations, SSH protocol numbers, Apache modules, configured hostnames, operating system, and device type (_Chapter 7. Service and Application Version Detection_, n.d.). This approach provides a more detailed and reliable understanding of what is truly running on the target system, enhancing the effectiveness of reconnaissance and security assessment activities. As shown in the image above, the results displayed are a clean list of port, port state, and its respective service and version using the command `nmap -Pn -sV <host IP>` that is used to identify which service version are running on the open ports. In this case, the -sV option is specifically used to enable service detection (Obialom, 2023). This command accurately identifies the exact services and software versions running on open ports, which is essential for determining potential vulnerabilities and supporting informed decision-making in subsequent security assessments.

## 2. Recon-ng
Recon-ng is free and open source tool available on GitHub. Recon-ng is based upon Open Source Intelligence (OSINT), the easiest and useful tool for reconnaissance. Recon-ng interface is very similar to Metasploit 1 and Metasploit 2.Recon-ng provides a command-line interface that you can run on Kali Linux. This tool can be used to get information about our target(domain). The interactive console provides a number of helpful features, such as command completion and contextual help. Recon-ng is a Web Reconnaissance tool written in Python. It has so many modules, database interaction, built-in convenience functions, interactive help, and command completion, Recon-ng provides a powerful environment in which open source web-based reconnaissance can be conducted, and we can gather all information (GeeksforGeeks, 2025). For this demonstration, a tutorial from GeeksforGeeks was followed.

### 2.1 Key Features
The three key features of Recon-ng are as follows (GeeksforGeeks, 2025):

### 2.1.1 Comprehensive Information-Gathering Modules
Recon‑ng offers a wide variety of specialized modules that can perform tasks, such as subdomain discovery, reverse WHOIS lookups, and other reconnaissance activities. Users can load, configure, and run these modules to collect targeted information efficiently.

### 2.1.2 Marketplace and Modular Design
Recon‑ng offers a built-in marketplace where users can search, install, and manage modules using specific commands. Modules are categorized and organized in a standardized way, making reconnaissance tasks easier to conduct and scalable.

### 2.1.3 Systematic Data Management
Recon‑ng allows users to create dedicated workspaces to systematically store and manage collected reconnaissance data. Each workspace maintains its own database to ensure structured data organization for the econnaissance tasks.

### 2.2 Step-by-Step Execution
This section explains the step-by-step execution using Recon-ng, reproducing the tutorial provided by GeeksforGeeks (2025).

### Step 1: Installing Recon-ng on Kali Linux
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%201%20clone.png)

By default, Recon-ng is pre-installed on Kali Linux. The command `git clone https://github.com/lanmaster53/recon-ng` is used to install the latest version of Recon-ng provided on Github (Lanmaster, n.d.). Installing the latest version is essential to ensure the software tool runs smoothly.

### Step 2: Downloading and Running Recon-ng
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%202%20download%20and%20run.png)

The command `recon-ng` is used to download or run/start Recon-ng, as shown in the image above. Entering this command ensures that the user of the software tool has entered the Recon-ng interactive shell, changing the shell prompt from `kali@kali` to `[recon-ng][default]` **(as shown in Step 3: Create Workspace)** to indicate a successful change.

### Step 3: Creating Workspace
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%203%20workspaces.png)

The command `workspaces` is used to create a workspace within Recon-ng. The name of the workspace is customizable, however, unnamed workspace automatically uses 'default' as its default workspace name. In Recon-ng, creating a workspace is to ensure that all located and collected data are systematically stored within a dedicated database specific to that workspace (_Recon-NG Tutorial_, 2022).

### Step 4: Discovering Module Through Marketplace
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%204%20marketplace%20search.png)

The command `marketplace search` is used to display a list of available modules, allowing users to explore into reconnaissance and open-sour intelligence activities (_Recon-NG Tutorial_, 2022). There are five (5) module categories which are:

- discovery
- exploitation
- import
- recon
- reporting

As shown in the image above, using `marketplace search` command provides a complete table that includes information such as module version, installation status (installed or not installed), last updated date, dependencies, and required keys (_Recon-NG Tutorial_, 2022). Recon-ng utilizes a variety of modules, which are specialized plugins designed to execute reconnaissance tasks. Modules are organized dynamically rather than through traditional file structures to allow efficient discovery, installation, and updates. These modules follow a standardized naming convention, such as `recon/companies-domains/viewdns_reverse_whois`, that indicates the module category (recon), input–output relationship (companies-domains), and specific function (viewdns_reverse_whois). Additionally, modules are logically categorized based on data sources and targets, such as domain-based, company-based, contact-based, host-based, and network-based modules. Each module provides detailed information regarding its purpose, configuration options, and requirements to allow users to understand and configure it appropriately before use (Marc, 2025).

### Step 5: Installing Module
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%205%20install%20module.png)

The command `marketplace install <module name>` is used to install a particular module based on user requirements. In this case, the module installed is `recon/companies-domains/viewdns_reverse_whois`, forming the full command as follows: `marketplace install recon/companies-domains/viewdns_reverse_whois`. The selected module utilizes company information as a starting point for reconnaissance activities, such as company profile gathering (Marc, 2025).

### Step 6: Loading Installed Module
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%206%20load%20module.png)

The command `modules load <module name>` is for loading the installed module. For the demonstration, the full command used is `modules load recon/companies-domains/viewdns_reverse_whois`. The shell prompt updates to include the module name at the end, which indicates that the user is now operating within the context of the loaded module (Marc, 2025). For example, as shown in the image above, the `[recon-ng][default]` prompt was updated to `[recon-ng][default][viewdns_reverse_whois]` after loading the installed module.

### Step 7: Setting The Source and Run The Source
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%207%20insert%20source%20and%20run.png)

The command `options set SOURCE <domain name or value>` is used to define the source after loading the module. By default, the **SOURCE** option is set to 'default', which applies to all domains stored in the user’s workspace domain table. Each module may contain different configuration options and corresponding values depending on its function. Once the required options are configured, the `run` command is executed to initiate the module (Marc, 2025) (for the demonstration, the 403 error indicates that the server understood the request but refused to process it (_403 Forbidden_, 2025). Therefore, the demonstration was halted to ensure safety as a third-party domain name was was used as the SOURCE following the tutorial). As a result, the system typically displays real-time progress updates followed by a summary of the results (Marc, 2025).

## 3. Hping3
Hping3 is an advanced open-source packet crafting tool widely used by cybersecurity professionals, such as penetration testers and network administrators. It operates via a command-line interface on Unix-like systems and provides precise control over TCP/IP protocols. It is primarily employed for security auditing, firewall analysis, network scanning, and advanced reconnaissance, while also supporting detailed packet‑level examination of network communications. Unlike traditional ping tools that rely mainly on ICMP, Hping3 can send TCP, UDP, and RAW-IP packets with customizable flags and payloads, which allows detailed analysis of target systems, firewall behavior, packet filtering, and network routes. These capabilities make Hping3 a valuable tool for ethical hacking, penetration testing, and network diagnostics (Vaishnavi, 2025). Furthermore, its key features, which are port scanning, firewall testing, and network path discovery (tracerouting) are demonstrated from Section 3.1 to 3.3, following the tutorial provided by WebAsha (Vaishnavi, 2025).

### 3.1 Port Scanning
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-hping3/hping3-port-scanning.png)

The command used for Hping3 port scanning is `sudo hping3 -S -p 80 -c 5 <target ip address>`. The breakdown of the command is as follows (Achipra, 2025; GeeksforGeeks, 2023; Vaishnavi, 2025):

- **sudo:** for root privileges as Hping3 crafts raw TCP packets require administrative access
- **-S:** Sets the SYN flag bit to initiate a TCP connection attempt to determine port status based on the returned TCP flags
- **-p 80:** Specifies port 80 (HTTP services) to check whether a web server is running
- **-c 5:** Sends five packets to improve scan reliability and reduce the impact of packet loss

The command works by performing a TCP SYN scan on port 80 to determine its status, and the **-S** option enables the SYN flag in the crafted TCP packet. When this packet is sent to the target, an open port responds with a SYN-ACK packet, which indicates that port 80 is open and an HTTP service is active, whereas a closed port responds with a RST-ACK packet (Achipra, 2025).

In this demonstration, 5 SYN packets were sent, and 3 responses were received, resulting in 40% packet loss. The returned TCP flags were RST‑ACK (RA), which indicates that port 80 is closed. The packet loss may have occurred due to firewall filtering. However, the received responses were sufficient to determine the port state. Hence, by checking these responses using the command, Hping3 can determine whether the target port is open or closed.

### 3.2 Network Path Discovery (Tracerouting)
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-hping3/hping3-traceroute.png)

The command used for tracerouting is `sudo hping3 --traceroute -V -S -p 80 -c 4 <target ip address>`, which helps to identify the network path between the source and the target using TCP packets instead of ICMP (GeeksforGeeks, 2023; Vaishnavi, 2025). Unlike traditional traceroute tools that rely on ICMP packets, Hping3 utilizes TCP SYN packets, which are less commonly blocked by firewalls. This makes TCP-based tracerouting more effective in network environments where ICMP traffic is restricted or filtered (Otw, 2023). The commands breakdown is as follows:

- **sudo:** to access root privileges
- **--traceroute:** to trace the path taken by packets to reach their destination
- **-V:** verbose (detailed) output
- **-S:** Sets the SYN flag bit to initiate a TCP connection attempt to determine port status based on the returned TCP flags
- **-p 80:** Specifies port 80 (HTTP services) to check whether a web server is running
- **-c 4:** Sends four packets to improve scan reliability and reduce the impact of packet loss

### 3.3 Banner Grabbing
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-hping3/hping3-banner-grabbing.png)

The command used for Hping3 banner grabbing is `sudo hping3 -S -p 21 -c 5 <target ip address>`.

## Comparison Discussion
(insert description)

## Conclusion
(insert description)

## References/Credits

_403 Forbidden_. (2025, July 4). MDN. https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/403

_A quick port scanning tutorial._ (n.d.). NMAP Network Scanning. https://nmap.org/book/port-scanning-tutorial.html

Achipra, S. (2025, September 3). _Introduction to Hping3_. Tutorials. https://www.zframez.com/articles/testing-tools/introduction-to-hping3

_Chapter 3. Host Discovery._ (n.d.). NMAP Network Scanning. https://nmap.org/book/host-discovery.html

_Chapter 7. Service and Application Version Detection._ (n.d.). NMAP Network Scanning. https://nmap.org/book/vscan.html

GeeksforGeeks. (2023, November 4). _hping3 Command in Linux_. GeeksforGeeks. https://www.geeksforgeeks.org/linux-unix/hping3-command-in-linux/

GeeksforGeeks. (2025, July 23). _Reconng Information gathering tool in Kali Linux_. GeeksforGeeks. https://www.geeksforgeeks.org/linux-unix/recon-ng-installation-on-kali-linux/

Lanmaster. (n.d.). _Getting started_. GitHub. https://github.com/lanmaster53/recon-ng/wiki/Getting-Started/226a2c2541c6bba6f15a77b227c0c4bed8c572aa

Marc, D. (2025, July 17). Recon-ng: a powerful reconnaissance tool for hackers (Red Team, Pentesters). _Dark Marc | Cybersecurity, Hacking & Tech_. https://darkmarc.substack.com/p/recon-ng-a-powerful-reconnaissance

Nmap. (n.d.). https://nmap.org/

Obialom, B. (2023, November 29). _A guide to using NMAP on Kali Linux_. Medium. https://medium.com/@bukkyobialom/a-guide-to-using-nmap-on-kali-linux-c0e6894834a8

Otw. (2023, December 10). _Port Scanning and Reconnaissance with Hping3_. https://hackers-arise.com/port-scanning-and-reconnaissance-with-hping3/

_Recon-NG Tutorial_. (2022, November). Hacker Target. https://hackertarget.com/recon-ng-tutorial/#:~:text=When%20using%20Recon%2Dng%20workspaces%20%2C,%5Brecon%2Dng%5D%5Bdefault%5D%20%3E%20workspaces%20create%20example_name

Sharadin, G. (n.d.). _What is Cybersecurity Reconnaissance | Types & Protection | Imperva_. Learning Center. https://www.imperva.com/learn/data-security/cybersecurity-reconnaissance/

Vaishnavi. (2025, June 18). _What is Hping3 Tool? Features, installation, commands & use cases explained_. WebAsha Technologies. https://www.webasha.com/blog/what-is-hping3-tool-features-installation-commands-use-cases-explained
