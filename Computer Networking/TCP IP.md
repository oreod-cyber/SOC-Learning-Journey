# The TCP/IP Model

## Definition of the TCP/IP Model

The **Transmission Control Protocol/Internet Protocol (TCP/IP) Model** is the standard networking model used for communication over the Internet and most modern computer networks. It defines how data is packaged, transmitted, routed, and received between devices.

Unlike the OSI Model, which is primarily a conceptual framework, the TCP/IP Model is a practical model used in real-world networking. It consists of **four layers**, each responsible for a specific part of the communication process.

Every time you browse a website, send an email, stream a video, or use a messaging app, your device relies on the TCP/IP Model to communicate with other devices across the network.

---

# The Four Layers of the TCP/IP Model

## 1. Application Layer

The **Application Layer** is the top layer of the TCP/IP Model. It provides network services directly to user applications and combines the functions of the **Application, Presentation, and Session** layers of the OSI Model.

### Responsibilities

* Provides services to applications.
* Enables web browsing, email, file sharing, and remote access.
* Handles data formatting, encryption, and session management.

### Common Protocols

* HTTP
* HTTPS
* DNS
* FTP
* SMTP
* POP3
* IMAP
* SSH
* Telnet
* DHCP

### Examples

* Opening a website in a web browser.
* Sending an email.
* Downloading a file from the internet.

---

## 2. Transport Layer

The **Transport Layer** is responsible for end-to-end communication between devices. It ensures that data is delivered correctly, in the right order (when required), and without unnecessary loss.

### Responsibilities

* Segments data into smaller pieces.
* Provides reliable or fast data delivery.
* Performs error checking.
* Controls data flow.
* Reassembles data at the destination.

### Common Protocols

* TCP (Transmission Control Protocol)
* UDP (User Datagram Protocol)

### Examples

* Downloading files using TCP.
* Voice and video calls using UDP.

---

## 3. Internet Layer

The **Internet Layer** is responsible for logical addressing and routing. It determines the best path for data to travel across different networks.

### Responsibilities

* Assigns IP addresses.
* Routes packets between networks.
* Determines the best communication path.
* Handles packet forwarding.

### Common Protocols

* IPv4
* IPv6
* ICMP
* IPsec
* ARP*

> **Note:** ARP is often associated with the Link/Network Access layer in many modern references, but it is commonly discussed alongside the Internet layer because it supports IP communication by resolving IP addresses to MAC addresses.

### Devices

* Routers
* Layer 3 Switches

---

## 4. Network Access Layer

Also called the **Link Layer**, this layer is responsible for transmitting data over the physical network.

### Responsibilities

* Physical transmission of data.
* Uses MAC addresses for local communication.
* Frames data.
* Detects transmission errors.
* Controls access to the transmission medium.

### Common Protocols and Technologies

* Ethernet
* Wi-Fi (IEEE 802.11)
* PPP
* Bluetooth

### Devices

* Switches
* Network Interface Cards (NICs)
* Wireless Access Points
* Hubs
* Bridges

---

# Summary Table of the TCP/IP Model

| Layer          | Main Responsibility                            | Common Protocols                 |
| -------------- | ---------------------------------------------- | -------------------------------- |
| Application    | Provides network services to applications      | HTTP, HTTPS, DNS, FTP, SMTP, SSH |
| Transport      | End-to-end communication and reliable delivery | TCP, UDP                         |
| Internet       | Logical addressing and routing                 | IPv4, IPv6, ICMP, IPsec          |
| Network Access | Physical transmission and local communication  | Ethernet, Wi-Fi, PPP             |

---

# Comparison Between the TCP/IP and OSI Models

Although both models describe how devices communicate over a network, they have different purposes.

| OSI Model                                               | TCP/IP Model                                      |
| ------------------------------------------------------- | ------------------------------------------------- |
| Seven layers                                            | Four layers                                       |
| Developed by ISO                                        | Developed by the U.S. Department of Defense (DoD) |
| Primarily a conceptual model                            | Practical model used in real-world networking     |
| Used for learning and troubleshooting                   | Used to implement modern networks                 |
| Separates Application, Presentation, and Session layers | Combines these into one Application layer         |

### Layer Mapping

| OSI Layer    | TCP/IP Layer   |
| ------------ | -------------- |
| Application  | Application    |
| Presentation | Application    |
| Session      | Application    |
| Transport    | Transport      |
| Network      | Internet       |
| Data Link    | Network Access |
| Physical     | Network Access |

---

# TCP vs UDP

The two main protocols at the Transport Layer are **TCP** and **UDP**.

## TCP (Transmission Control Protocol)

TCP is a **connection-oriented** protocol that ensures reliable communication.

### Characteristics

* Reliable data delivery.
* Error checking.
* Acknowledges received packets.
* Retransmits lost packets.
* Delivers data in the correct order.

### Common Uses

* Web browsing (HTTP/HTTPS)
* Email
* File transfers
* Online banking

---

## UDP (User Datagram Protocol)

UDP is a **connectionless** protocol designed for speed rather than reliability.

### Characteristics

* Faster than TCP.
* No acknowledgments.
* No retransmission of lost packets.
* Lower overhead.
* Suitable for real-time communication.

### Common Uses

* Video streaming
* Voice over IP (VoIP)
* Online gaming
* DNS queries

---

## TCP vs UDP Comparison

| Feature         | TCP                       | UDP                          |
| --------------- | ------------------------- | ---------------------------- |
| Connection      | Connection-oriented       | Connectionless               |
| Reliability     | Reliable                  | Best effort                  |
| Speed           | Slower                    | Faster                       |
| Error Recovery  | Yes                       | No                           |
| Packet Ordering | Guaranteed                | Not guaranteed               |
| Typical Use     | Web, Email, File Transfer | Streaming, Gaming, VoIP, DNS |

---

# Common TCP/IP Protocols

Below are some of the most common protocols used in TCP/IP networking.

| Protocol  | Purpose                                 |
| --------- | --------------------------------------- |
| HTTP      | Transfers web pages                     |
| HTTPS     | Secure web communication                |
| FTP       | File transfer                           |
| DNS       | Resolves domain names into IP addresses |
| DHCP      | Automatically assigns IP addresses      |
| SMTP      | Sends email                             |
| POP3      | Retrieves email                         |
| IMAP      | Synchronizes email across devices       |
| SSH       | Secure remote administration            |
| Telnet    | Remote administration (insecure)        |
| TCP       | Reliable transport                      |
| UDP       | Fast transport                          |
| IPv4/IPv6 | Logical addressing                      |
| ICMP      | Network diagnostics (e.g., ping)        |
| IPsec     | Secures IP communications               |

---

# Why the TCP/IP Model is Important in Cybersecurity

The TCP/IP Model forms the foundation of modern computer networking. Nearly every cyberattack involves one or more TCP/IP protocols, making this model essential for cybersecurity professionals.

A SOC analyst uses the TCP/IP Model to:

* Understand how data travels across networks.
* Analyze network traffic using tools like Wireshark.
* Investigate suspicious IP addresses and network connections.
* Detect malware communication and Command-and-Control (C2) traffic.
* Monitor network activity using SIEM platforms.
* Identify unusual protocol behavior that may indicate an attack.
* Investigate incidents involving DNS, HTTP, HTTPS, SSH, FTP, or other protocols.
* Troubleshoot communication problems during incident response.

Understanding which TCP/IP layer a problem or attack affects helps analysts investigate incidents more efficiently.

---

# Key Takeaways

* The TCP/IP Model is the networking model used by the Internet and most modern networks.
* It consists of **four layers**: Application, Transport, Internet, and Network Access.
* The model explains how data is transmitted from one device to another.
* TCP provides reliable communication, while UDP prioritizes speed.
* Common protocols such as HTTP, HTTPS, DNS, TCP, UDP, and IP all operate within the TCP/IP Model.
* Every SOC analyst should understand the TCP/IP Model because it is fundamental to network traffic analysis, threat detection, and incident response.
