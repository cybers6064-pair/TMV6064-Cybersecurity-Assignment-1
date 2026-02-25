# Task 1: Reconnaissance
**By: Nur Zulaikha**

## Disclaimer
**This project is for educational purposes only. All testing was performed in a controlled environment or on authorized targets.

## Introduction
**(add Reconnaissance description)**

**Tools:** NMAP, Recon-ng, and Hping3

**Objectives:** To demonstrate preliminary information gathering about a target before taking action (such as conducting an investigation) by using three reconnaissance tools, for the purpose of a more effective and strategic planning prior to initiating the attack.

## 1. NMAP (Network Mapper)
NMAP (Network Mapper) is a free, open-source tool used for network discovery and is pre-installed in Kali Linux. It is utilized for security auditing, assisting administrators to identify active hosts, running services, operating systems, and firewall configurations on a network as it is essential to understand a target’s structure and potential vulnerabilities before taking further action. NMAP is designed to scan both large networks and single hosts, offering flexibility, robustness, and compatibility with major operating systems such as Linux, Windows, and macOS. Additionally, NMAP also includes additional tools like Zenmap for graphical interface support. Due to its effectiveness, ease of use, and strong community support, NMAP has become widely used for reconnaissance task (Nmap, n.d.). Furthermore, this demonstration dives deeper into the three key features of NMAP that explains why it is useful and effective for reconnaissance and security assessments, namely **Host Discovery**, **Port Scanning**, and **Service Detection**, and following the tutorial posted by Obialom (2023).

## 1.1 Host Discovery
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20host%20discovery.png)

NMAP can be utilized for **host discovery**, which is the initial phase of network reconnaissance. It aims to identify active systems in a target network (_Chapter 3. Host Discovery_, n.d.). The command `nmap -Pn (host IP)`, as shown in the image above, can be used for this purpose. The breakdown of the command is as follows:

- **-Pn**: used to assume host is active
- **-PE**: sends ping and wait for echo requests to determine whether the host is active
- **-sn**: disables port scanning to focus solely on identifying active hosts

Additionally, the host discovery feature narrows large IP ranges into a manageable list of active systems, which improves scanning efficiency. For this feature, NMAP also supports customizable probing techniques, including TCP, UDP, and ICMP scans, which allows users to tailor their approach according to specific objectives and network conditions, such as firewall or filtering bypassing (_Chapter 3. Host Discovery_, n.d.; Obialom, 2023). Therefore, this feature of NMAP enhances the effectiveness of preliminary information gathering during network reconnaissance, which is crucial as identifying active hosts allows professionals, such as security analysts, define the attack surface, prioritize targets, and support more strategic planning for subsequent scanning or security assessment tasks.


## 1.2 Port Scanning
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20port%20scanning.png)

**Port Scanning** is mainly used to scan and find available open ports of the targeted host using the command "nmap [host IP address or name]".
Note that the command -Pn is used in this task due to the suggestion provided before the successful scan to assume that the host is active, as well as
skipping the host discovery. This also allows a faster scan.

## 1.3 Service Detection
![image alt](https://github.com/cybers6064-pair/TMV6064-Cybersecurity-Assignment-1/blob/5dc67d9f9b9907055df5dffdbbb65fa01ad32612/Task%201%20(Reconnaissance)/images/nmap%20service%20detection.png)

**Service Detetction** is...

## 2. Recon-ng

## 2.1

## 2.2

## 2.3

## 3. Hping3

## 3.1

## 3.2

## 3.3

## Comparison of NMAP, Recon-ng, and Hping3
(insert description)

## References/Credits
**NMAP**
1. Nmap. (n.d.). https://nmap.org/
2. Chapter 3. Host Discovery. (n.d.). NMAP Network Scanning. https://nmap.org/book/host-discovery.html
3. A quick port scanning tutorial | NMAP Network Scanning. (n.d.). https://nmap.org/book/port-scanning-tutorial.html
4. Obialom, B. (2023, November 29). A guide to using NMAP on Kali Linux. Medium. https://medium.com/@bukkyobialom/a-guide-to-using-nmap-on-kali-linux-c0e6894834a8

**Recon-ng**
1. ref-1

**Hping3**
1. ref-1
