# IP Addressing Fundamentals

## Definition of an IP Address

An **IP (Internet Protocol) address** is a unique logical address assigned to a device on a network. It allows devices to identify and communicate with one another by specifying where data should be sent and received.

Just as a postal address helps deliver mail to the correct house, an IP address helps deliver data packets to the correct device on a network.

Every device connected to a network—such as a computer, smartphone, server, router, or printer—requires an IP address to communicate using the Internet Protocol (IP).

---

# Types of IP Addresses

There are two major versions of IP addresses in use today:

* **IPv4 (Internet Protocol Version 4)**
* **IPv6 (Internet Protocol Version 6)**

IPv6 was introduced to solve the shortage of available IPv4 addresses while providing improved efficiency and security features.

---

# IPv4 vs IPv6

## IPv4 (Internet Protocol Version 4)

IPv4 is the most widely used version of the Internet Protocol. It uses **32-bit addresses**, allowing for approximately **4.3 billion unique addresses**.

### Example

```text
192.168.1.100
```

### Characteristics

* 32-bit addressing.
* Four decimal numbers (octets) separated by periods.
* Approximately 4.3 billion unique addresses.
* Still the most commonly used version today.
* Supported by virtually all networking devices.

---

## IPv6 (Internet Protocol Version 6)

IPv6 is the latest version of the Internet Protocol. It uses **128-bit addresses**, providing an almost unlimited number of unique IP addresses.

### Example

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

Compressed form:

```text
2001:db8:85a3::8a2e:370:7334
```

### Characteristics

* 128-bit addressing.
* Written in hexadecimal.
* Groups separated by colons (`:`).
* Supports an extremely large address space.
* Improves routing efficiency.
* Designed for the future growth of the Internet.

---

# IPv4 vs IPv6 Comparison

| Feature        | IPv4           | IPv6                                                                                |
| -------------- | -------------- | ----------------------------------------------------------------------------------- |
| Address Length | 32 bits        | 128 bits                                                                            |
| Address Format | Decimal        | Hexadecimal                                                                         |
| Example        | 192.168.1.100  | 2001:db8::1                                                                         |
| Address Space  | ~4.3 billion   | Approximately 340 undecillion (3.4 × 10³⁸)                                          |
| NAT Required   | Commonly used  | Usually not required                                                                |
| Header Size    | Variable       | Simplified and fixed                                                                |
| Security       | IPsec optional | IPsec support is built into the protocol specification (though its use is optional) |

---

# Public vs Private IP Addresses

## Public IP Address

A **public IP address** is globally unique and routable over the Internet. It is assigned by an Internet Service Provider (ISP) and allows a device or network to communicate with systems on the Internet.

### Example

```text
8.8.8.8
```

### Characteristics

* Globally unique.
* Accessible over the Internet.
* Assigned by an ISP or cloud provider.
* Used by websites, cloud servers, and Internet-connected services.

---

## Private IP Address

A **private IP address** is used only within a local network (LAN). These addresses are **not routable on the public Internet** and can be reused by different private networks.

Private addresses are commonly assigned automatically by a DHCP server on a home or office router.

### Example

```text
192.168.1.25
```

### Characteristics

* Used inside private networks.
* Not directly accessible from the Internet.
* Reused by millions of different organizations and homes.
* Conserves public IPv4 addresses.

---

# The Three Private IPv4 Address Ranges

The Internet Assigned Numbers Authority (IANA) reserves three IPv4 ranges for private networks.

| Address Range                     | CIDR Notation  | Typical Use                      |
| --------------------------------- | -------------- | -------------------------------- |
| **10.0.0.0 – 10.255.255.255**     | 10.0.0.0/8     | Large enterprise networks        |
| **172.16.0.0 – 172.31.255.255**   | 172.16.0.0/12  | Medium-sized organizations       |
| **192.168.0.0 – 192.168.255.255** | 192.168.0.0/16 | Home and small business networks |

These ranges are reserved exclusively for private networking and cannot be routed across the public Internet.

---

# Loopback Address

A **loopback address** is a special IP address used by a device to communicate with itself. It is commonly used for testing, troubleshooting, and verifying that the TCP/IP networking stack is functioning correctly.

## IPv4 Loopback

```text
127.0.0.1
```

The entire **127.0.0.0/8** range is reserved for loopback, but **127.0.0.1** is the address most commonly used.

## IPv6 Loopback

```text
::1
```

### Common Uses

* Testing network applications.
* Verifying TCP/IP functionality.
* Running local web servers.
* Software development and debugging.

---

# Network Address Translation (NAT)

**Network Address Translation (NAT)** is a networking technique that allows multiple devices using private IP addresses to share a single public IP address when accessing the Internet.

A router performing NAT replaces a device's private source IP address with its public IP address before forwarding traffic to the Internet. When responses return, the router translates the destination back to the correct private IP address.

### Benefits of NAT

* Conserves public IPv4 addresses.
* Hides internal network addresses from the Internet.
* Allows many devices to share one public IP address.
* Adds a layer of privacy by masking internal IP addresses (although it should not be considered a security mechanism by itself).

### Example

Without NAT:

* PC 1 → Needs a public IP.
* PC 2 → Needs a public IP.
* PC 3 → Needs a public IP.

With NAT:

* PC 1 → 192.168.1.10
* PC 2 → 192.168.1.11
* PC 3 → 192.168.1.12

Router:

* Public IP → 203.0.113.5

All three devices access the Internet through the router's single public IP address.

---

# Why IP Addressing is Important in Cybersecurity

IP addresses play a central role in cybersecurity because they identify the source and destination of network communications. Nearly every security investigation involves analyzing IP addresses to understand who communicated, when they communicated, and where the traffic originated.

SOC analysts rely on IP addressing to:

* Investigate suspicious network connections.
* Identify the source of cyberattacks.
* Detect unauthorized access attempts.
* Monitor inbound and outbound network traffic.
* Trace malware communication.
* Analyze firewall, IDS/IPS, and SIEM logs.
* Block malicious IP addresses using firewalls or security appliances.
* Identify internal devices involved in security incidents.

### Example

Suppose a SIEM generates an alert showing repeated failed login attempts from the public IP address **198.51.100.25** to a company's VPN server. A SOC analyst can investigate whether the IP address is associated with a brute-force attack, review authentication logs, and take actions such as blocking the IP address, enforcing multi-factor authentication (MFA), or escalating the incident for further investigation.

---

# Best Practices for Managing IP Addresses

To improve network security and simplify investigations, organizations should:

* Maintain an accurate inventory of IP address assignments.
* Use private IP addresses for internal devices whenever appropriate.
* Restrict unnecessary public-facing services.
* Monitor network traffic for unusual IP activity.
* Block known malicious IP addresses.
* Keep firewall and router rules up to date.
* Regularly review DHCP and DNS logs during security investigations.

---

# Key Takeaways

* An **IP address** uniquely identifies a device on a network.
* **IPv4** uses 32-bit addresses, while **IPv6** uses 128-bit addresses.
* **Public IP addresses** are Internet-routable, whereas **private IP addresses** are used only within local networks.
* The three private IPv4 ranges are **10.0.0.0/8**, **172.16.0.0/12**, and **192.168.0.0/16**.
* The IPv4 loopback address is **127.0.0.1**, while the IPv6 loopback address is **::1**.
* **NAT** enables multiple private devices to share a single public IP address.
* Understanding IP addressing is essential for SOC analysts because it forms the basis of network communication, traffic analysis, threat detection, and incident response.
