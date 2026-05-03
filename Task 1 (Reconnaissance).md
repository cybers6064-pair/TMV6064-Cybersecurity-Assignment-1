# Task 1: Reconnaissance
**By: Nur Zulaikha**

## Disclaimer
**This project is for educational purposes only. All testing was performed in a controlled environment or on authorized targets.

## Introduction
In Cybersecurity, reconnaissance refers to the initial phase of a cyber attack that involves systematic information gathering to identify potential vulnerabilities within a target system or network. Similar to military reconnaissance, it focuses on collecting intelligence or information prior to launching an attack. Moreover, reconnaissance can be either passive or active. Passive reconnaissance is where the attackers collect information without directly interacting with the target, while active reconnaissance involves direct techniques such as network scanning, port scanning, and vulnerability scanning. The process typically includes collecting publicly available and technical data, identifying the network scope and IP ranges, detecting security mechanisms such as firewalls or intrusion detection systems, locating open ports and access points, determining the services and versions running on those ports, and mapping the overall network architecture. This structured approach enables attackers to understand the target’s attack surface, identify entry points, and strategically plan subsequent exploitation activities (Sharadin, n.d.).

### Tools
The tools explored for reconnaissance task are:
- NMAP
- Recon-ng
- Hping3
- DNSRecon

### Objective
To demonstrate preliminary information gathering about a target before taking action (such as conducting an investigation) by using three reconnaissance tools within the Kali Linux environment, for the purpose of a more effective and strategic planning prior to initiating the attack.

## 1. NMAP (Network Mapper)
NMAP (Network Mapper) is a free, open-source tool used for network discovery and is pre-installed on Kali Linux. It is utilized for security auditing, assisting administrators to identify active hosts, running services, operating systems, and firewall configurations on a network as it is essential to understand a target’s structure and potential vulnerabilities before taking further action. NMAP is designed to scan both large networks and single hosts, offering flexibility, robustness, and compatibility with major operating systems such as Linux, Windows, and macOS. Additionally, NMAP also includes additional tools like Zenmap for graphical interface support. Due to its effectiveness, ease of use, and strong community support, NMAP has become widely used for reconnaissance task (Nmap, n.d.). Furthermore, this demonstration dives deeper into the three key features of NMAP that explains why it is useful and effective for reconnaissance and security assessments, namely **Host Discovery**, **Port Scanning**, and **Service Version Detection**. This demonstration also follows the tutorial produced by Obialom (2023) and _A quick port scanning tutorial_ (n.d.) from Nmap official website.

### 1.1 Host Discovery
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20host%20discovery.png)

NMAP can be utilized for **host discovery**, which is the initial phase of network reconnaissance. It aims to identify active systems in a target network (_Chapter 3. Host Discovery_, n.d.). The command `nmap -Pn -PE -sn <host IP>`, as shown in the image above, can be used for this purpose. The breakdown of the command is as follows:

- **-Pn**: used to assume host is active (for demonstration purpose and as suggested by NMAP)
- **-PE**: sends ping and wait for echo requests to determine whether the host is active
- **-sn**: disables port scanning to focus solely on identifying active hosts

This command is used to specifically verify whether a target system is active without initiating a full port scan, allowing reconnaissance tasks to focus on identifying active hosts before proceeding to more detailed analysis. Additionally, the host discovery feature narrows large IP ranges into a manageable list of active systems, which improves scanning efficiency. For this feature, NMAP also supports customizable probing techniques, including TCP, UDP, and ICMP scans, which allows users to tailor their approach according to specific objectives and network conditions, such as firewall or filtering bypassing (_Chapter 3. Host Discovery_, n.d.; Obialom, 2023). Therefore, this feature of NMAP enhances the effectiveness of preliminary information gathering during network reconnaissance, which is crucial as identifying active hosts allows professionals, such as security analysts, define the attack surface, prioritize targets, and support more strategic planning for subsequent scanning or security assessment tasks.


### 1.2 Port Scanning
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20port%20scanning.png)

NMAP is highly effective for **port scanning**, which is used to identify open ports on a target host. Port scanning is a fundamental technique for discovering accessible services running on a system. NMAP offers a wide range of scanning options and methods to collect detailed information about open ports on a target system or network (Obialom, 2023). For this demonstration, a basic port scanning tutorial provided by NMAP was followed (_A quick port scanning tutorial_, n.d.). The command used was the standard `nmap -Pn <host IP>`, which performs a default scan by resolving the hostname to an IP address. This command is used to ensure that port scanning continues even if the host blocks ping requests to enable the identification of open ports and exposed services that may represent potential entry points for further security assessment. By default, NMAP scans the top 1,000 most common TCP ports, as applied in this demonstration, though users can also specify particular ports to scan as needed such as the examples below (Obialom, 2023):

- **-p 80:** scans only port 80

- **-p 1–100:** scans all ports within the range of 1–100

- **-p 22, 23, 80:** scans ports 22, 23, 80

- **-p-:** scans all TCP ports

As illustrated in the image above, the output is presented in a human-readable format that displays the target IP address, port numbers, protocols, port states (open, closed, or filtered), associated services, and basic timing statistics. Non-open ports are consolidated as depicted by 'Not shown: 997 filtered tcp ports (no-response)' to minimize unnecessary output clutter and improve readability (_A Quick Port Scanning Tutorial_, n.d.). Therefore, this port scanning feature enabled by NMAP is crucial as identifying open ports and running services helps define the target’s attack surface, allowing security professionals to detect potential vulnerabilities and plan subsequent security assessments or mitigation strategies.


### 1.3 Service Version Detection
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20service%20detection.png)

NMAP also provides service version detection, emphasizing that accurate service and version detection is crucial for vulnerability assessments, identifying applicable exploits, and maintaining an accurate network inventory. NMAP’s version detection actively interrogates open ports with service-specific probes to reveal beyond the service type and version, but also additional details such as service configurations, SSH protocol numbers, Apache modules, configured hostnames, operating system, and device type (_Chapter 7. Service and Application Version Detection_, n.d.). This approach provides a more detailed and reliable understanding of what is truly running on the target system, enhancing the effectiveness of reconnaissance and security assessment activities. As shown in the image above, the results displayed are a clean list of port, port state, and its respective service and version using the command `nmap -Pn -sV <host IP>` that is used to identify which service version are running on the open ports of the targeted host. In this case, the **-sV** option is specifically used to enable service detection (Obialom, 2023). This command accurately identifies the exact services and software versions running on open ports, which is essential for determining potential vulnerabilities and supporting informed decision-making in subsequent security assessments.

## 2. Recon-ng
Recon-ng is a free and open-source tool available on GitHub that is built around Open-Source Intelligence (OSINT), making it useful for reconnaissance activities. Recon-ng runs on Kali Linux and is designed to collect information about a target domain, as well as offers an interactive console with helpful features such as command completion and contextual help. The tool includes numerous modules, supports database interaction, and provides built-in functions that simplify data collection. Moreover, Recon-ng also creates a powerful environment for conducting web-based reconnaissance and gathering organized information about a target. (GeeksforGeeks, 2025a). For this demonstration, a tutorial from GeeksforGeeks (2025a) was followed.

### 2.1 Key Features
The three key features of Recon-ng are as follows (GeeksforGeeks, 2025a):

### 2.1.1 Comprehensive Information-Gathering Modules
Recon‑ng offers a wide variety of specialized modules that can perform tasks, such as subdomain discovery, reverse WHOIS lookups, and other reconnaissance activities. Users can load, configure, and run these modules to collect targeted information efficiently.

### 2.1.2 Marketplace and Modular Design
Recon‑ng offers a built-in marketplace where users can search, install, and manage modules using specific commands. Modules are categorized and organized in a standardized way, making reconnaissance tasks easier to conduct and scalable.

### 2.1.3 Systematic Data Management
Recon‑ng allows users to create dedicated workspaces to systematically store and manage collected reconnaissance data. Each workspace maintains its own database to ensure structured data organization for the reconnaissance tasks.

### 2.2 Step-by-Step Execution
This section explains the step-by-step execution using Recon-ng, reproducing the tutorial produced by GeeksforGeeks (2025a).

### Step 1: Installing Recon-ng on Kali Linux
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%201%20clone.png)

By default, Recon-ng is pre-installed on Kali Linux. The command `git clone https://github.com/lanmaster53/recon-ng` is used to install the latest version of Recon-ng provided on Github (Lanmaster, n.d.). Installing the latest version is essential to ensure the software tool runs smoothly.

### Step 2: Downloading and Running Recon-ng
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%202%20download%20and%20run.png)

The command `recon-ng` is used to download or run/start Recon-ng, as shown in the image above. Entering this command ensures that the user of the software tool has entered the Recon-ng interactive shell, changing the shell prompt from `kali@kali` (default Kali Linux prompt) to `[recon-ng][default]`, indicating a successful change **(as shown in Step 3: Create Workspace)**.

### Step 3: Creating Workspace
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%203%20workspaces.png)

The command `workspaces` is used to create a workspace within Recon-ng. The name of the workspace is customizable, however, unnamed workspace automatically uses 'default' as its default workspace name. In Recon-ng, creating a workspace is to ensure that all located and collected data are systematically stored within a dedicated database specific to that workspace (_Recon-NG Tutorial_, 2022).

### Step 4: Discovering Module Through Marketplace
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%204%20marketplace%20search.png)

The command `marketplace search` is used to display a list of available modules, allowing users to explore into reconnaissance and open-source intelligence activities (_Recon-NG Tutorial_, 2022). There are five (5) module categories which are:

- discovery
- exploitation
- import
- recon
- reporting

As shown in the image above, using `marketplace search` command provides a complete table that includes information such as module version, installation status (installed or not installed), last updated date, dependencies, and required keys (_Recon-NG Tutorial_, 2022). Recon-ng utilizes a variety of modules, which are specialized plugins designed to execute reconnaissance tasks. Modules are organized dynamically rather than through traditional file structures to allow efficient discovery, installation, and updates. These modules follow a standardized naming convention, such as `recon/companies-domains/viewdns_reverse_whois`, that indicates the module category (recon), input–output relationship (companies-domains), and specific function (viewdns_reverse_whois). Additionally, modules are logically categorized based on data sources and targets, such as domain-based, company-based, contact-based, host-based, and network-based modules. Each module provides detailed information regarding its purpose, configuration options, and requirements to allow users to understand and configure it appropriately before use (Marc, 2025).

### Step 5: Installing Module
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%205%20install%20module.png)

The command `marketplace install <module name>` is used to install a particular module based on user requirements. In this case, the module installed is `recon/companies-domains/viewdns_reverse_whois`, forming the full command `marketplace install recon/companies-domains/viewdns_reverse_whois`. The selected module utilizes company information as a starting point for reconnaissance activities, such as company profile gathering (Marc, 2025).

### Step 6: Loading Installed Module
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%206%20load%20module.png)

The command `modules load <module name>` is for loading the installed module. For the demonstration, the full command used is `modules load recon/companies-domains/viewdns_reverse_whois`. The shell prompt updates to include the module name at the end, which indicates that the user is now operating within the context of the loaded module (Marc, 2025). For example, as shown in the image above, the `[recon-ng][default]` prompt was updated to `[recon-ng][default][viewdns_reverse_whois]` after loading the installed module.

### Step 7: Setting The Source and Run The Source
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%207%20insert%20source%20and%20run.png)

The command `options set SOURCE <domain name or value>` is used to define the source after loading the module. By default, the **SOURCE** option is set to 'default', which applies to all domains stored in the user’s workspace domain table. Each module may contain different configuration options and corresponding values depending on its function. Once the required options are configured, the `run` command is executed to initiate the module (Marc, 2025) (for the demonstration, the 403 error indicates that the server understood the request but refused to process it (_403 Forbidden_, 2025). Therefore, the demonstration was halted to ensure safety as a third-party domain name was used as the SOURCE following the tutorial). As a result, the system typically displays real-time progress updates followed by a summary of the results (Marc, 2025).

## 3. Hping3
Hping3 is an advanced open-source packet crafting tool that is widely used by cybersecurity professionals, such as penetration testers and network administrators. It operates via a command-line interface on Unix-like systems and provides precise control over TCP/IP protocols. It is primarily employed for security auditing, firewall analysis, network scanning, and advanced reconnaissance, while also supporting detailed packet‑level examination of network communications. Unlike traditional ping tools that rely mainly on ICMP, Hping3 can send TCP, UDP, and RAW-IP packets with customizable flags and payloads, which allows detailed analysis of target systems, firewall behavior, packet filtering, and network routes. These capabilities make Hping3 a valuable tool for ethical hacking, penetration testing, and network diagnostics (Vaishnavi, 2025). Furthermore, its key features, **Port Scanning**, **Network Path Discovery (Tracerouting)**, and **Banner Grabbing**, are demonstrated from Sections 3.1 to 3.3, following the tutorial produced by WebAsha (Vaishnavi, 2025).

### 3.1 Port Scanning
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-hping3/hping3-port-scanning.png)

The command used for Hping3 port scanning is `sudo hping3 -S -p 80 -c 5 <target ip address>`. The breakdown of the command is as follows (Achipra, 2025; GeeksforGeeks, 2023; Vaishnavi, 2025):

- **sudo:** for root privileges as Hping3 crafts raw TCP packets that requires administrative access
- **-S:** Sets the SYN flag bit to initiate a TCP connection attempt to determine port status based on the returned TCP flags
- **-p 80:** Specifies port 80 (HTTP services) to check whether a web server is running
- **-c 5:** Sends five packets to improve scan reliability and reduce the impact of packet loss

The command works by performing a TCP SYN scan on port 80 to determine its status, and the **-S** option enables the SYN flag in the crafted TCP packet. When this packet is sent to the target, an open port responds with a SYN-ACK packet, which indicates that port 80 is open and an HTTP service is active, whereas a closed port responds with a RST-ACK packet (Achipra, 2025).

In this demonstration, 5 SYN packets were sent, and 3 responses were received, resulting in 40% packet loss that may have occurred due to firewall filtering. The returned TCP flags were RST‑ACK (RA), which indicates that port 80 is closed. However, the received responses were sufficient to determine the port state. Hence, by checking these responses using the command, Hping3 can determine whether the target port is open or closed.

### 3.2 Network Path Discovery (Tracerouting)
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-hping3/hping3-traceroute.png)

The command used for tracerouting is `sudo hping3 --traceroute -V -S -p 80 -c 4 <target ip address>`, which helps to identify the network path between the source and the target using TCP packets instead of ICMP (GeeksforGeeks, 2023; Vaishnavi, 2025). Unlike traditional traceroute tools that rely on ICMP packets, Hping3 utilizes TCP SYN packets, which are less commonly blocked by firewalls. This makes TCP-based tracerouting more effective in network environments where ICMP traffic is restricted or filtered (Otw, 2023). The commands breakdown is as follows (Achipra, 2025; GeeksforGeeks, 2023; Vaishnavi, 2025):

- **sudo:** to access root privileges
- **--traceroute:** to trace the path taken by packets to reach their destination
- **-V:** verbose (detailed) output
- **-S:** Sets the SYN flag bit to initiate a TCP connection attempt to determine port status based on the returned TCP flags
- **-p 80:** Specifies port 80 (HTTP services) to check whether a web server is running
- **-c 4:** Sends four packets to improve scan reliability and reduce the impact of packet loss

### 3.3 Banner Grabbing
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-hping3/hping3-banner-grabbing.png)

Banner grabbing is an information-gathering technique that used in both offensive and defensive cybersecurity to identify services running on open ports of a target system. A banner is the text response provided by a server that reveals details such as the software name, version, and sometimes operating system information. By collecting this data, attackers and security professionals can determine potential vulnerabilities associated with specific software versions. Banner grabbing can be performed actively, where packets are sent directly to a target server to analyze its response, or passively, where information is captured indirectly without establishing a direct connection. This technique can be applied to various protocols, including HTTP (port 80), FTP (port 21), and SMTP (port 25). Since identifying service versions allows security analysts or attackers to search for known exploits, banner grabbing is considered a critical reconnaissance step in penetration testing and ethical hacking (GeeksforGeeks, 2025b). In this demonstartion, the command used for Hping3 banner grabbing is `sudo hping3 -S -p 21 -c 5 <target ip address>`, which probes the FTP service on port 21 to obtain banner information, allowing identification that can then be analyzed for potential vulnerabilities (Vaishnavi, 2025). The commands breakdown is as follows (Achipra, 2025; GeeksforGeeks, 2023; Vaishnavi, 2025):

- **-S:** Sets the SYN flag bit to initiate a TCP connection attempt to determine port status based on the returned TCP flags
- **-p 21:** Specifies port 21 to target the FTP service
- **-c 5:** Sends four packets to improve scan reliability and reduce the impact of packet loss

## 4. DNSRecon
DNS reconnaissance is an important step in gathering network information and software like DNSRecon are widely used to support this process (TechMindXperts, 2023). DNSRecon is a command-line tool designed for security professionals to gather important domain-related data such as subdomains, IP addresses, and various types of DNS records (TechMindXperts, 2023). It can execute several tasks, such as subdomain enumeration, DNS record retrieval, brute-forcing hidden subdomains, zone transfers, and reverse DNS lookups, all of which help detect potential vulnerabilities in a target network (TechMindXperts, 2023). DNSRecon is written in Python, works across multiple operating systems (Linux, Windows, MacOS), and comes preinstalled in Kali Linux (TechMindXperts, 2023). For this assignment, three key features of DNSRecon are discussed, which are enumeration of subdomains, retrieval of DNS records, and Reverse DNS lookups. The steps conducted for all key features are following the tutorial produced by TechMindXperts (2023).

### 4.1 Enumeration of Subdomains
DNS enumeration is essential during the reconnaissance stage of penetration testing as it provides detailed information about a target's network infrastructure (Issa, 2024). It involves discovering DNS records, subdomains, IP addresses, and related configurations, which can aid in network mapping, detecting potential vulnerabilities, and plan prospective attack paths (Issa, 2024). Since manual DNS enumeration can be time-consuming and prone to errors, automated tools like DNSRecon are commonly used to increase efficiency (Issa, 2024). DNS enumeration provides valuable information for ethical hackers to better understand the target ecosystem and identify potential vulnerabilities (Issa, 2024). For the example, the enumeration process is conducted following the tutorial from TechMindXperts (2023) and using the command `dnsrecon -d <target domain name>`. This command is used so that the DNSRecon returns a list of full set of DNS records for the target domain, such  as name servers, mail servers, IP addresses, text records, and service records, which helps to map the target domain’s infrastructure and configuration altogether. It also identified a total of 2 service records (SRV) during the scan.

![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5793f4cbf3f207f6e9a791a1c7265934b8267be9/Task%201%20(Reconnaissance)/images-dnsrecon/enumeration%20subdomain%201.png)
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5793f4cbf3f207f6e9a791a1c7265934b8267be9/Task%201%20(Reconnaissance)/images-dnsrecon/enumeration%20subdomain%202.png)
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5793f4cbf3f207f6e9a791a1c7265934b8267be9/Task%201%20(Reconnaissance)/images-dnsrecon/enumeration%20subdomain%203.png)

### 4.2 Retrieval of DNS Records
DNSRecon can also be used to retrieve DNS records for a target domain, such as MX, NS, SOA, TXT, and other related record types. Below is an example of DNS records retrieval process using the command `dnsrecon -d <target domain> -t std` (TechMindXperts, 2023). This command is used to perform standard DNS enumeration on a target domain, returning or  retrieving key DNS records such as name servers, mail servers, IP addresses, text records, and service records. Additionally, the 8 records found indicates that DNSRecon successfully identified eight service records which represent different network services and the servers supporting them within the target domain.

![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/9ce13e51bb22b7cfc1305c586300a723ee6cc0b0/Task%201%20(Reconnaissance)/images-dnsrecon/retrieve%20dns%20record%201.png)
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/c2c25c22e9d6d4656b4f051835c277ce6b015680/Task%201%20(Reconnaissance)/images-dnsrecon/retrieve%20dns%20record%202.png)

### 4.3 Reverse DNS Lookups
Reverse DNS (rDNS) lookup involves resolving an IP address back to its domain name using Pointer records (PTR) (Borges, 2024). These records are stored in specified locations, such as _in-addr.arpa_ for IPv4 and _ip6.arpa_ for IPv6 (Borges, 2024). Reverse DNS lookup helps to identify domain names associated with certain IP addresses that makes it useful for defining a target's infrastructure and disclosing hostnames that would be difficult to uncover using standard enumeration methods (Borges, 2024). It can also provide insights into internal naming schemes and server roles as well as the discovery of potential virtual hosts and security issues (Borges, 2024). Additionally, this is where tools like DNSRecon become helpful as it can automate this reverse DNS lookups across IP ranges (Borges, 2024). To perform Reverse DNS Lookups, the command `dnsrecon -r <IP Range>` is executed, where the `-r` is used to activate the lookup process. The command is used to return domain names associated with IP addresses within a specified range through reverse DNS lookups and retrieving PTR records where available. Moreover, to improve execution time, a smaller IP range (173.245.59.0/24) was used instead of the tutorial’s larger range that requires a much longer scanning duration (OpenAI, 2026). The 196 records found indicates that DNSRecon successfully retrieved 196 reverse DNS records during the scan where IP addresses within the specified range were mapped back to their associated domain names.

![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/c2c25c22e9d6d4656b4f051835c277ce6b015680/Task%201%20(Reconnaissance)/images-dnsrecon/reverse%20lookup%201.png)
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/a3c3308ad2b0e335bf52fc74e67fe4e7b9a8aafa/Task%201%20(Reconnaissance)/images-dnsrecon/reverse%20lookup%202.png)

## Comparison Discussion
Although all four tools support reconnaissance activities, they differ in scope and functionality. NMAP efficiently performs host discovery, port scanning, and service version detection that provides a clear view of the target’s network and potential entry points. Contrastingly, Recon-ng collects publicly available information such as domains, subdomains, and WHOIS data, organizing the collected intelligence within structured workspaces, where this structured approach helps building a comprehensive profile of the target environment. DNSRecon, similarly, focuses on DNS reconnaissance by extracting DNS-related information such as subdomains, IP addresses, mail servers, DNS records, and reverse DNS mappings. This helps to better understand the target’s domain structure and identify possible misconfigurations or exposed services. On the other hand, Hping3 enables precise packet-level analysis that allows users to craft and send customized TCP/IP packets for tasks such as port scanning, tracerouting, and banner grabbing, offering more control over packet behavior. Despite these differences, the tools share the common goal of supporting reconnaissance and complement one another rather than compete. Recon-ng can gather background intelligence, NMAP can identify accessible hosts and services, DNSRecon can perform DNS reconnaissance by extracting information such as subdomains, IP addresses, DNS records, and reverse DNS mappings, and Hping3 can further analyze system responses through crafted packets, offering a more systematic and layered reconnaissance process through these combinations.

## Conclusion
In conclusion, reconnaissance is a critical phase in cybersecurity that establishes the foundation for understanding a target’s network, systems, and potential vulnerabilities. The four tools explored demonstrate complementary strengths, where NMAP facilitates network discovery and service identification, Recon-ng gathers and organizes open-source information, DNSRecon focuses on DNS reconnaissance by extracting information such as subdomains, IP addresses, DNS records, and reverse DNS mappings to reveal domain-level infrastructure details, and Hping3 probes network responses with customized packets. When used together, these tools can provide a comprehensive approach that enhances reconnaissance effectiveness, supports informed decision-making, and ensures a strategic understanding of the target’s attack surface before further security assessments.

## References

_403 Forbidden_. (2025, July 4). MDN. https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/403

_A quick port scanning tutorial._ (n.d.). NMAP Network Scanning. https://nmap.org/book/port-scanning-tutorial.html

Achipra, S. (2025, September 3). _Introduction to Hping3_. Tutorials. https://www.zframez.com/articles/testing-tools/introduction-to-hping3

Borges, E. (2024, April 1). What is DNS Enumeration? Top Tools and Techniques Explained. https://www.recordedfuture.com/threat-intelligence-101/tools-and-techniques/dns-enumeration
_Chapter 3. Host Discovery._ (n.d.). NMAP Network Scanning. https://nmap.org/book/host-discovery.html

_Chapter 7. Service and Application Version Detection._ (n.d.). NMAP Network Scanning. https://nmap.org/book/vscan.html

GeeksforGeeks. (2023, November 4). _hping3 Command in Linux_. GeeksforGeeks. https://www.geeksforgeeks.org/linux-unix/hping3-command-in-linux/

GeeksforGeeks. (2025a, July 23). _Reconng Information gathering tool in Kali Linux_. GeeksforGeeks. https://www.geeksforgeeks.org/linux-unix/recon-ng-installation-on-kali-linux/

GeeksforGeeks. (2025b, July 23). What is Banner Grabbing? GeeksforGeeks. https://www.geeksforgeeks.org/ethical-hacking/what-is-banner-grabbing/

Issa, A. (2024, February 29). A Beginner’s Guide to DNS Reconnaissance (Part 1). Medium. https://infosecwriteups.com/a-beginners-guide-to-dns-reconnaissance-part-1-6cd9f502db7d

Lanmaster. (n.d.). _Getting started_. GitHub. https://github.com/lanmaster53/recon-ng/wiki/Getting-Started/226a2c2541c6bba6f15a77b227c0c4bed8c572aa

Marc, D. (2025, July 17). Recon-ng: a powerful reconnaissance tool for hackers (Red Team, Pentesters). _Dark Marc | Cybersecurity, Hacking & Tech_. https://darkmarc.substack.com/p/recon-ng-a-powerful-reconnaissance

Nmap. (n.d.). https://nmap.org/

Obialom, B. (2023, November 29). _A guide to using NMAP on Kali Linux_. Medium. https://medium.com/@bukkyobialom/a-guide-to-using-nmap-on-kali-linux-c0e6894834a8

OpenAI. (2026). _ChatGPT_ (April 2026 version) [Large language model]. https://chat.openai.com/chat

Otw. (2023, December 10). _Port Scanning and Reconnaissance with Hping3_. https://hackers-arise.com/port-scanning-and-reconnaissance-with-hping3/

_Recon-NG Tutorial_. (2022, November). Hacker Target. https://hackertarget.com/recon-ng-tutorial/#:~:text=When%20using%20Recon%2Dng%20workspaces%20%2C,%5Brecon%2Dng%5D%5Bdefault%5D%20%3E%20workspaces%20create%20example_name

Sharadin, G. (n.d.). _What is Cybersecurity Reconnaissance | Types & Protection | Imperva_. Learning Center. https://www.imperva.com/learn/data-security/cybersecurity-reconnaissance/

TechMindXperts. (2023, April 16). What is dnsrecon Full Guide. Medium. https://medium.com/@techmindxperts/what-is-dnsrecon-full-guide-with-examples-355aba308332

Vaishnavi. (2025, June 18). _What is Hping3 Tool? Features, installation, commands & use cases explained_. WebAsha Technologies. https://www.webasha.com/blog/what-is-hping3-tool-features-installation-commands-use-cases-explained
