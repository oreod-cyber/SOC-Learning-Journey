# Network Protocols and Common Ports

## Definition of a Network Protocol

A **network protocol** is a set of rules and standards that define how devices communicate and exchange data over a network. These rules ensure that devices from different manufacturers can understand each other, transmit data correctly, and communicate reliably.

Think of a network protocol as a common language. Just as people need a shared language to communicate effectively, computers and other network devices rely on protocols to send and receive information.

Without network protocols, devices would not know how to establish connections, format data, detect errors, or interpret messages.

---

# Definition of a Port

A **port** is a logical communication endpoint used by a computer to identify a specific application or service running on a device. While an **IP address** identifies a device on a network, a **port number** identifies the particular service or application on that device.

For example, a web server may have the IP address **192.168.1.100**, but it listens for web traffic on **port 80 (HTTP)** or **port 443 (HTTPS)**.

### Think of it this way:

* **IP Address** = The address of a building.
* **Port** = The specific office or room inside the building.

This combination allows data to reach both the correct device and the correct application.

---

# Common Network Protocols and Ports

The table below lists some of the most commonly used network protocols, their default ports, transport protocols, and primary functions.

| Protocol   | Full Meaning                          | Default Port | Transport Protocol | Purpose                                                                     |
| ---------- | ------------------------------------- | -----------: | ------------------ | --------------------------------------------------------------------------- |
| HTTP       | Hypertext Transfer Protocol           |           80 | TCP                | Transfers web pages over the internet.                                      |
| HTTPS      | Hypertext Transfer Protocol Secure    |          443 | TCP                | Securely transfers encrypted web traffic using TLS/SSL.                     |
| FTP        | File Transfer Protocol                |           21 | TCP                | Transfers files between computers.                                          |
| SFTP       | SSH File Transfer Protocol            |           22 | TCP                | Securely transfers files over SSH.                                          |
| SSH        | Secure Shell                          |           22 | TCP                | Provides secure remote administration of systems.                           |
| Telnet     | Telecommunication Network             |           23 | TCP                | Provides remote terminal access without encryption (not recommended today). |
| SMTP       | Simple Mail Transfer Protocol         |           25 | TCP                | Sends outgoing email messages.                                              |
| DNS        | Domain Name System                    |           53 | TCP/UDP            | Translates domain names into IP addresses.                                  |
| DHCP       | Dynamic Host Configuration Protocol   |        67/68 | UDP                | Automatically assigns IP addresses and network settings to devices.         |
| TFTP       | Trivial File Transfer Protocol        |           69 | UDP                | Transfers small files without authentication.                               |
| HTTP Proxy | Hypertext Proxy Service               |         8080 | TCP                | Common alternative port for web proxy services and web applications.        |
| POP3       | Post Office Protocol Version 3        |          110 | TCP                | Retrieves email from a mail server.                                         |
| NTP        | Network Time Protocol                 |          123 | UDP                | Synchronizes time between network devices.                                  |
| IMAP       | Internet Message Access Protocol      |          143 | TCP                | Synchronizes email while keeping messages on the server.                    |
| SNMP       | Simple Network Management Protocol    |      161/162 | UDP                | Monitors and manages network devices.                                       |
| LDAP       | Lightweight Directory Access Protocol |          389 | TCP/UDP            | Accesses and manages directory services such as Active Directory.           |
| LDAPS      | LDAP Secure                           |          636 | TCP                | Secure version of LDAP using encryption.                                    |
| SMB        | Server Message Block                  |          445 | TCP                | Provides file and printer sharing on Windows networks.                      |
| Syslog     | System Logging Protocol               |          514 | UDP (commonly)     | Sends system and security log messages to a central log server.             |
| RDP        | Remote Desktop Protocol               |         3389 | TCP                | Allows remote graphical access to Windows computers.                        |

---

# Explanation of Common Protocols

## HTTP (Port 80)

HTTP is the standard protocol used to transfer web pages between a web browser and a web server. Because HTTP traffic is not encrypted, attackers can intercept or modify the data being transmitted.

---

## HTTPS (Port 443)

HTTPS is the secure version of HTTP. It uses **TLS (Transport Layer Security)** to encrypt communication between clients and servers, protecting sensitive information such as passwords, financial data, and personal information.

---

## FTP (Port 21)

FTP is used to transfer files between computers on a network. Traditional FTP does not encrypt usernames, passwords, or transferred data, making it unsuitable for sensitive information.

---

## SFTP (Port 22)

SFTP provides secure file transfers by operating over SSH. It encrypts both authentication credentials and transferred files, making it much safer than traditional FTP.

---

## SSH (Port 22)

SSH provides secure remote access to servers and network devices. System administrators commonly use SSH to manage Linux systems and network equipment.

---

## Telnet (Port 23)

Telnet allows remote access to computers but sends all data, including usernames and passwords, in plain text. Because it lacks encryption, SSH has largely replaced Telnet.

---

## SMTP (Port 25)

SMTP is responsible for sending email between mail servers and from email clients to outgoing mail servers.

---

## DNS (Port 53)

DNS converts human-readable domain names, such as **example.com**, into IP addresses that computers use to locate one another on a network.

---

## DHCP (Ports 67/68)

DHCP automatically assigns IP addresses and other network configuration settings, reducing the need for manual configuration.

---

## TFTP (Port 69)

TFTP is a lightweight file transfer protocol commonly used for transferring configuration files or firmware to network devices. It provides no authentication or encryption.

---

## POP3 (Port 110)

POP3 downloads email from a mail server to a client device. Messages are often removed from the server after download.

---

## NTP (Port 123)

NTP synchronizes the clocks of computers and network devices. Accurate time is critical for log analysis, authentication, and incident investigations.

---

## IMAP (Port 143)

IMAP allows users to access and synchronize email across multiple devices while keeping messages stored on the mail server.

---

## SNMP (Ports 161/162)

SNMP enables administrators to monitor and manage routers, switches, servers, and other network devices.

---

## LDAP (Port 389)

LDAP provides access to directory services, allowing organizations to manage users, groups, and authentication information.

---

## LDAPS (Port 636)

LDAPS secures LDAP communications by encrypting traffic between clients and directory servers.

---

## SMB (Port 445)

SMB enables file sharing, printer sharing, and resource sharing on Windows networks. Because it has been targeted by malware such as WannaCry, monitoring SMB traffic is important.

---

## Syslog (Port 514)

Syslog is used to send system and security logs from network devices and servers to a centralized logging server for monitoring and analysis.

---

## RDP (Port 3389)

RDP allows users to remotely access Windows computers through a graphical desktop interface. Exposed RDP services are common targets for brute-force attacks and unauthorized access attempts.

---

# Why Protocol and Port Knowledge is Essential for SOC Analysts

A SOC analyst investigates security events by understanding which protocols and ports are involved in network communications. Knowing how common protocols work and which ports they use helps analysts quickly identify suspicious activity and determine whether network traffic is legitimate.

Protocol and port knowledge enables SOC analysts to:

* Interpret alerts generated by SIEM platforms.
* Analyze network traffic using tools such as Wireshark.
* Identify unusual or unauthorized services running on a network.
* Detect malware communicating over common or uncommon ports.
* Investigate brute-force attacks targeting services like SSH and RDP.
* Recognize suspicious DNS, HTTP, HTTPS, or SMB activity.
* Configure firewall rules and intrusion detection systems (IDS/IPS).
* Respond more effectively to security incidents.

### Example

Suppose a SIEM generates an alert showing repeated connection attempts to **port 3389 (RDP)** from an unfamiliar external IP address. A SOC analyst immediately recognizes that the attacker may be attempting a brute-force attack against a Windows system. This knowledge allows the analyst to investigate quickly, verify whether the attempts were successful, and take actions such as blocking the source IP, disabling exposed RDP access, or escalating the incident.

---

# Key Takeaways

* A **network protocol** defines how devices communicate over a network.
* A **port** identifies the specific service or application receiving network traffic.
* Every protocol has a primary purpose and, in many cases, a well-known default port number.
* Understanding protocols and ports is essential for network troubleshooting, threat detection, and incident response.
* SOC analysts rely on protocol and port knowledge every day to analyze alerts, investigate suspicious activity, and protect organizational networks.
