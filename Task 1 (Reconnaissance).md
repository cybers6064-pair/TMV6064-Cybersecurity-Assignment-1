# Task 1: Reconnaissance
**By: Nur Zulaikha**

## Disclaimer
**This project is for educational purposes only. All testing was performed in a controlled environment or on authorized targets.

## Introduction
In Cybersecurity, reconnaissance refers to the initial phase of a cyber attack that involves systematic information gathering to identify potential vulnerabilities within a target system or network. Similar to military reconnaissance, it focuses on collecting intelligence or information prior to launching an attack. Moreover, reconnaissance can be either passive or active. Passive reconnaissance is where the attackers collects information without directly interacting with the target, while active reconnaissance involves direct techniques such as network scanning, port scanning, and vulnerability scanning. The process typically includes collecting publicly available and technical data, identifying the network scope and IP ranges, detecting security mechanisms such as firewalls or intrusion detection systems, locating open ports and access points, determining the services and versions running on those ports, and mapping the overall network architecture. This structured approach enables attackers to understand the target’s attack surface, identify entry points, and strategically plan subsequent exploitation activities (Sharadin, n.d.). For the purpose of Task 1: Reconnaissance, the demonstration fully follows active reconnaissance.

**Tools:** NMAP, Recon-ng, and Hping3

**Objectives:** To demonstrate preliminary information gathering about a target before taking action (such as conducting an investigation) by using three reconnaissance tools, for the purpose of a more effective and strategic planning prior to initiating the attack.

## 1. NMAP (Network Mapper)
NMAP (Network Mapper) is a free, open-source tool used for network discovery and is pre-installed in Kali Linux. It is utilized for security auditing, assisting administrators to identify active hosts, running services, operating systems, and firewall configurations on a network as it is essential to understand a target’s structure and potential vulnerabilities before taking further action. NMAP is designed to scan both large networks and single hosts, offering flexibility, robustness, and compatibility with major operating systems such as Linux, Windows, and macOS. Additionally, NMAP also includes additional tools like Zenmap for graphical interface support. Due to its effectiveness, ease of use, and strong community support, NMAP has become widely used for reconnaissance task (Nmap, n.d.). Furthermore, this demonstration dives deeper into the three key features of NMAP that explains why it is useful and effective for reconnaissance and security assessments, namely **Host Discovery**, **Port Scanning**, and **Service Detection**, and following the tutorial posted by Obialom (2023).

## 1.1 Host Discovery
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20host%20discovery.png)

NMAP can be utilized for **host discovery**, which is the initial phase of network reconnaissance. It aims to identify active systems in a target network (_Chapter 3. Host Discovery_, n.d.). The command `nmap -Pn -PE -sn <host IP>`, as shown in the image above, can be used for this purpose. The breakdown of the command is as follows:

- **-Pn**: used to assume host is active (for demonstration purpose and as suggested by NMAP)
- **-PE**: sends ping and wait for echo requests to determine whether the host is active
- **-sn**: disables port scanning to focus solely on identifying active hosts

This command is used to specifically verify whether a target system is active without initiating a full port scan, allowing reconnaissance tasks to focus on identifying active hosts before proceeding to more detailed analysis. Additionally, the host discovery feature narrows large IP ranges into a manageable list of active systems, which improves scanning efficiency. For this feature, NMAP also supports customizable probing techniques, including TCP, UDP, and ICMP scans, which allows users to tailor their approach according to specific objectives and network conditions, such as firewall or filtering bypassing (_Chapter 3. Host Discovery_, n.d.; Obialom, 2023). Therefore, this feature of NMAP enhances the effectiveness of preliminary information gathering during network reconnaissance, which is crucial as identifying active hosts allows professionals, such as security analysts, define the attack surface, prioritize targets, and support more strategic planning for subsequent scanning or security assessment tasks.


## 1.2 Port Scanning
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20port%20scanning.png)

Nmap is highly effective for **port scanning**, which is used to identify open ports on a target host. Port scanning is a fundamental technique for discovering accessible services running on a system. Nmap offers a wide range of scanning options and methods to collect detailed information about open ports on a target system or network (Obialom, 2023). For this demonstration, a basic port scanning tutorial provided by Nmap was followed (_A Quick Port Scanning Tutorial_, n.d.). The command used was the standard `nmap -Pn <host IP>`, which performs a default scan by resolving the hostname to an IP address. This command is used to ensure that port scanning continues even if the host blocks ping requests to enable the identification of open ports and exposed services that may represent potential entry points for further security assessment. By default, Nmap scans the top 1,000 most common TCP ports, as applied in this demonstration, though users can also specify particular ports to scan as needed such as the examples below (Obialom, 2023):

- **-p80:** scans only port 80

- **-p 1–100:** scans all ports within the range of 1–100

- **-p22, 23, 80:** scans ports 22, 23, 80

- **-p-:** scans all TCP ports

As illustrated in the image above, the output is presented in a human-readable format that displays the target IP address, port numbers, protocols, port states (open, closed, or filtered), associated services, and basic timing statistics. Non-open ports are consolidated as depicted by 'Not shown: 997 filtered tcp ports (no-response)' to minimize unnecessary output clutter and improve readability (_A Quick Port Scanning Tutorial_, n.d.). Therefore, this port scanning feature enabled by NMAP is crucial as identifying open ports and running services helps define the target’s attack surface, allowing security professionals to detect potential vulnerabilities and plan subsequent security assessments or mitigation strategies.


## 1.3 Service Version Detection
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20service%20detection.png)

NMAP also provides service version detection, emphasizing that accurate service and version detection is crucial for vulnerability assessments, identifying applicable exploits, and maintaining an accurate network inventory. NMAP’s version detection actively interrogates open ports with service-specific probes to reveal beyond the service type and version, but also additional details such as service configurations, SSH protocol numbers, Apache modules, configured hostnames, operating system, and device type (_Chapter 7. Service and Application Version Detection_, n.d.). This approach provides a more detailed and reliable understanding of what is truly running on the target system, enhancing the effectiveness of reconnaissance and security assessment activities. As shown in the image above, the results displayed are a clean list of port, port state, and its respective service and version using the command `nmap -Pn -sV <host IP>` that is used to identify which service version are running on the open ports. In this case, the -sV option is specifically used to enable service detection (Obialom, 2023). This command accurately identifies the exact services and software versions running on open ports, which is essential for determining potential vulnerabilities and supporting informed decision-making in subsequent security assessments.

## 2. Recon-ng
Recon-ng is free and open source tool available on GitHub. Recon-ng is based upon Open Source Intelligence (OSINT), the easiest and useful tool for reconnaissance. Recon-ng interface is very similar to Metasploit 1 and Metasploit 2.Recon-ng provides a command-line interface that you can run on Kali Linux. This tool can be used to get information about our target(domain). The interactive console provides a number of helpful features, such as command completion and contextual help. Recon-ng is a Web Reconnaissance tool written in Python. It has so many modules, database interaction, built-in convenience functions, interactive help, and command completion, Recon-ng provides a powerful environment in which open source web-based reconnaissance can be conducted, and we can gather all information (GeeksforGeeks, 2025). For this demonstration, a tutorial from GeeksForGeeks was followed.

## 2.1 Key Features

## 2.2 Step-by-Step Execution
**Step 1: Installing Recon-ng on Kali Linux**
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%201%20clone.png)

The command `git clone https://github.com/lanmaster53/recon-ng` is used to install Recon-ng on Kali Linux.


**Step 2: Downloading and Running Recon-ng**
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%202%20download%20and%20run.png)

The command `recon-ng` is used to download and Run Recon-ng.

**Step 3: Create Workspace**
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%203%20workspaces.png)

The command `workspaces` is used to create a workspace to set up environment for reconnaissance in Recon-ng. Unnamed workspace uses default as its default workspace name.

**Step 4: Marketplace Search**
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%204%20marketplace%20search.png)

The command `marketplace search` is used to display a list of modules for installation purpose.

**Step 5: Module Installation**
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%205%20install%20module.png)

The command `marketplace install (module name)` is used to install a particular module of interest. In this case, the module installed is (insert module), displayed by the command `marketplace install recon/companies-domains/viewdns_reverse_whois`.

**Step 6: Loading Installed Module**
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%206%20load%20module.png)

The command `modules load recon/companies-domains/viewdns_reverse_whois` is used to load the installed module.

**Step 7: Setting The Source and Run The Source**
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/main/Task%201%20(Reconnaissance)/images-recon-ng/recon%20command%207%20insert%20source%20and%20run.png)

The command `options set SOURCE (domain name)` is used to set the source and run it.

## 3. Hping3

## 3.1

## 3.2

## 3.3

## Comparison of NMAP, Recon-ng, and Hping3
(insert description)

## References/Credits
**NMAP**
- _A quick port scanning tutorial._ (n.d.). NMAP Network Scanning. https://nmap.org/book/port-scanning-tutorial.html
- _Chapter 3. Host Discovery._ (n.d.). NMAP Network Scanning. https://nmap.org/book/host-discovery.html
- _Chapter 7. Service and Application Version Detection._ (n.d.). NMAP Network Scanning. https://nmap.org/book/vscan.html
- Nmap. (n.d.). https://nmap.org/
- Obialom, B. (2023, November 29). A guide to using NMAP on Kali Linux. Medium. https://medium.com/@bukkyobialom/a-guide-to-using-nmap-on-kali-linux-c0e6894834a8
- Sharadin, G. (n.d.). What is Cybersecurity Reconnaissance | Types & Protection | Imperva. Learning Center. https://www.imperva.com/learn/data-security/cybersecurity-reconnaissance/

**Recon-ng**
- GeeksforGeeks. (2025, July 23). _Reconng Information gathering tool in Kali Linux_. GeeksforGeeks. https://www.geeksforgeeks.org/linux-unix/recon-ng-installation-on-kali-linux/

**Hping3**
1. ref-1
