# Computer Networking Fundamentals for SOC Analysts

## Definition of a Computer Network

A **computer network** is a collection of two or more computers, servers, or other devices connected together to communicate and share resources such as files, applications, printers, and internet access. Devices on a network exchange data using standardized communication protocols like TCP/IP.

**Example:**
When your laptop connects to your home Wi-Fi to browse the internet or share files with another computer, it is part of a computer network.

---

# Types of Networks

## 1. Local Area Network (LAN)

A **LAN** connects devices within a small geographical area such as a home, office, school, or campus. It is typically fast, secure, and privately managed.

**Example:** Office computers connected through a switch.

---

## 2. Wide Area Network (WAN)

A **WAN** connects multiple LANs over large geographical distances using public or private communication links.

**Example:** The Internet is the world's largest WAN.

---

## 3. Metropolitan Area Network (MAN)

A **MAN** covers a city or metropolitan area and is larger than a LAN but smaller than a WAN.

**Example:** A university connecting multiple campuses within the same city.

---

## 4. Personal Area Network (PAN)

A **PAN** is a small network that connects personal devices over a short distance.

**Example:** A smartphone connected to wireless earbuds through Bluetooth.

---

## 5. Wireless Local Area Network (WLAN)

A **WLAN** is a LAN that uses wireless technologies (Wi-Fi) instead of cables.

**Example:** Home Wi-Fi networks.

---

# Network Devices

## Router

A router connects different networks and forwards data between them. It also provides internet access to devices on a local network.

**Example:** Your home Wi-Fi router.

---

## Switch

A switch connects multiple devices within the same LAN and forwards data only to the intended destination device using MAC addresses.

---

## Hub

A hub connects devices but broadcasts incoming data to every connected device. Unlike a switch, it does not identify the correct destination, making it inefficient and less secure.

---

## Firewall

A firewall monitors and filters incoming and outgoing network traffic based on security rules. It helps prevent unauthorized access.

---

## Modem

A modem converts signals between your Internet Service Provider (ISP) and your local network, allowing internet connectivity.

---

## Wireless Access Point (AP)

An access point allows wireless devices to connect to a wired network using Wi-Fi.

---

# IP Address

An **IP (Internet Protocol) address** is a unique logical address assigned to a device on a network. It identifies where data should be sent and received.

There are two versions:

* **IPv4:** 192.168.1.10
* **IPv6:** 2001:db8::1

Public IP addresses are used on the internet, while private IP addresses are used within local networks.

---

# MAC Address

A **MAC (Media Access Control) address** is a unique physical address assigned to a network interface card (NIC) by the manufacturer.

Example:

```
00:1A:2B:3C:4D:5E
```

Unlike IP addresses, MAC addresses normally remain the same and are mainly used for communication within a local network.

---

# Packet

A **packet** is a small unit of data transmitted across a network. Large files are broken into packets before transmission and reassembled when they reach the destination.

Each packet typically contains:

* Source address
* Destination address
* Payload (actual data)
* Control information

SOC analysts often inspect packets to detect suspicious or malicious network activity.

---

# Client vs Server

## Client

A client is a device or application that requests services or resources from another computer.

**Examples:**

* Web browser
* Email application
* Mobile app

---

## Server

A server is a computer or software that provides services, applications, or data to clients over a network.

**Examples:**

* Web server
* File server
* Database server
* Email server

### Difference

| Client                  | Server                          |
| ----------------------- | ------------------------------- |
| Requests resources      | Provides resources              |
| Initiates communication | Responds to requests            |
| Used by end users       | Hosts services and applications |

---

# Why Networking is Important in a Security Operations Center (SOC)

Networking is one of the most important skills for a SOC analyst because cyberattacks occur across networks. Understanding networking helps analysts detect, investigate, and respond to security incidents effectively.

A SOC analyst uses networking knowledge to:

* Monitor network traffic for suspicious activity.
* Analyze logs from firewalls, routers, and servers.
* Investigate malicious IP addresses and network connections.
* Detect malware communication and command-and-control (C2) traffic.
* Understand how attackers move through a network (lateral movement).
* Identify unauthorized devices and unusual network behavior.
* Respond to incidents more quickly and accurately.
* Use tools such as Wireshark, SIEM platforms, IDS/IPS, and network monitoring solutions.

## Summary

Networking forms the foundation of cybersecurity. Before analyzing threats, detecting attacks, or responding to incidents, a SOC analyst must understand how devices communicate, how data travels through networks, and how attackers exploit network vulnerabilities. Strong networking knowledge makes it easier to recognize abnormal behavior and protect organizational systems.
