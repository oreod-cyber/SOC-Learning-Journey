# Domain Name System (DNS)

## Definition of DNS

The **Domain Name System (DNS)** is a distributed naming system that translates **human-readable domain names** into **IP addresses** that computers use to communicate over a network.

Humans find it easier to remember names such as **google.com** or **github.com**, while computers communicate using IP addresses such as **142.250.190.14** or **140.82.114.4**. DNS acts as the "phonebook of the Internet" by matching domain names with their corresponding IP addresses.

Without DNS, users would have to remember and enter IP addresses every time they wanted to visit a website.

---

# How DNS Works

Whenever you type a website address into your browser, a DNS lookup occurs before the website can be loaded.

The process generally works as follows:

1. **User Request**

   * You enter a domain name (for example, `www.example.com`) into your web browser.

2. **DNS Resolver**

   * Your computer sends the request to a **DNS resolver**, usually provided by your Internet Service Provider (ISP) or a public DNS service.

3. **Root DNS Server**

   * If the resolver does not already know the answer, it contacts a **Root DNS Server**, which directs it to the correct Top-Level Domain (TLD) server.

4. **Top-Level Domain (TLD) Server**

   * The TLD server (such as `.com`, `.org`, or `.net`) directs the resolver to the domain's authoritative name server.

5. **Authoritative DNS Server**

   * The authoritative server returns the IP address associated with the requested domain.

6. **Connection Established**

   * The resolver sends the IP address back to your computer, allowing your browser to connect to the correct web server.

This entire process usually takes only a few milliseconds.

---

# DNS Record Types

DNS stores different types of information using **DNS records**. Each record has a specific purpose.

| Record Type | Purpose                                                                                                          |
| ----------- | ---------------------------------------------------------------------------------------------------------------- |
| **A**       | Maps a domain name to an IPv4 address.                                                                           |
| **AAAA**    | Maps a domain name to an IPv6 address.                                                                           |
| **CNAME**   | Creates an alias that points one domain name to another.                                                         |
| **MX**      | Specifies the mail server responsible for receiving email for a domain.                                          |
| **NS**      | Identifies the authoritative name servers for a domain.                                                          |
| **TXT**     | Stores text information such as SPF, DKIM, domain verification, and other metadata.                              |
| **PTR**     | Performs reverse DNS lookups by mapping an IP address to a domain name.                                          |
| **SRV**     | Specifies the location of specific network services, including their host and port.                              |
| **SOA**     | Contains administrative information about the DNS zone, including the primary name server and timing parameters. |

---

# Common DNS Record Types Explained

## A Record

Maps a domain name to an IPv4 address.

**Example**

```
example.com → 93.184.216.34
```

---

## AAAA Record

Maps a domain name to an IPv6 address.

---

## CNAME Record

Creates an alias for another domain name.

**Example**

```
www.example.com → example.com
```

---

## MX Record

Specifies which mail servers receive email for a domain.

---

## NS Record

Identifies the authoritative DNS servers responsible for answering queries about a domain.

---

## TXT Record

Stores text-based information commonly used for:

* SPF (Sender Policy Framework)
* DKIM (DomainKeys Identified Mail)
* Domain ownership verification
* Other security and configuration settings

---

## PTR Record

Maps an IP address back to a domain name. This is commonly used in reverse DNS lookups and email security checks.

---

## SRV Record

Provides information about the location of specific services, including the hostname and port number.

---

## SOA Record

Contains essential information about a DNS zone, including:

* Primary authoritative name server
* Domain administrator
* Zone serial number
* Refresh and retry intervals

---

# DNS Port Number

DNS primarily uses **Port 53**.

| Protocol  | Port |
| --------- | ---- |
| DNS (UDP) | 53   |
| DNS (TCP) | 53   |

Although both UDP and TCP use port **53**, they are used for different purposes.

---

# UDP vs TCP Usage in DNS

## DNS over UDP

UDP is the default transport protocol for most DNS queries because it is fast and has low overhead.

### Advantages

* Faster communication.
* Lower network overhead.
* Ideal for simple DNS lookups.
* Used for the vast majority of client queries.

---

## DNS over TCP

TCP is used when reliability is more important than speed.

Common situations include:

* DNS zone transfers between DNS servers.
* Responses that are too large for UDP.
* Some DNSSEC-related communications.

### Advantages

* Reliable data delivery.
* Supports larger message sizes.
* Ensures complete transmission of critical DNS data.

---

# DNS Attack Types

Because DNS is essential to Internet communication, attackers often target it to disrupt services, steal information, or redirect users.

## DNS Spoofing (DNS Cache Poisoning)

An attacker inserts false DNS information into a DNS resolver's cache, causing users to be redirected to malicious websites even when they enter legitimate domain names.

---

## DNS Tunneling

Attackers use DNS queries and responses to secretly transfer data or communicate with malware, bypassing traditional network security controls.

---

## DNS Amplification Attack

A type of **Distributed Denial-of-Service (DDoS)** attack in which attackers send small DNS requests with a spoofed source IP address. DNS servers respond with much larger replies, overwhelming the victim's network.

---

## DNS Hijacking

An attacker changes DNS settings on a user's device, router, or DNS server so that requests are redirected to malicious destinations.

---

## Fast Flux

Attackers rapidly change the IP addresses associated with a malicious domain name, making it difficult for defenders to block malicious infrastructure.

---

## Domain Generation Algorithm (DGA)

Some malware generates hundreds or thousands of random domain names every day. Attackers only need to register a few of these domains to regain communication with infected systems, making detection and blocking more difficult.

---

# Why DNS is Important in Cybersecurity

DNS is involved in almost every network connection. Before a device communicates with a website or many Internet services, it usually performs a DNS lookup. Because of this, DNS data is extremely valuable during security investigations.

SOC analysts use DNS to:

* Investigate suspicious domains.
* Detect malware communicating with command-and-control (C2) servers.
* Identify phishing websites.
* Monitor unusual DNS traffic.
* Detect DNS tunneling attempts.
* Correlate DNS logs with firewall, proxy, endpoint, and SIEM logs.
* Investigate data exfiltration attempts.
* Block malicious domains through DNS filtering and security controls.

### Example

Suppose a workstation repeatedly sends DNS requests for randomly generated domain names such as:

```
aj82jd91x.com
kq8za21.net
zpxv71.org
```

A SOC analyst may recognize this pattern as a **Domain Generation Algorithm (DGA)** used by malware. By reviewing DNS logs, endpoint activity, and network traffic, the analyst can determine whether the device is infected and take appropriate response actions.

---

# Best Practices for DNS Security

Organizations should adopt the following practices to strengthen DNS security:

* Use trusted and secure DNS resolvers.
* Enable **DNSSEC (Domain Name System Security Extensions)** where supported to help protect against DNS spoofing.
* Monitor DNS logs for unusual activity.
* Block known malicious domains.
* Detect and investigate DNS tunneling attempts.
* Restrict unauthorized changes to DNS records.
* Keep DNS servers updated with the latest security patches.

---

# Key Takeaways

* **DNS (Domain Name System)** translates domain names into IP addresses.
* DNS primarily uses **Port 53** over both **UDP** and **TCP**.
* **UDP** is used for most DNS queries because it is fast, while **TCP** is used for zone transfers and larger or more reliable communications.
* Common DNS record types include **A, AAAA, CNAME, MX, NS, TXT, PTR, SRV,** and **SOA**.
* DNS is a frequent target of cyberattacks, including DNS spoofing, DNS tunneling, DNS amplification, DNS hijacking, Fast Flux, and DGA-based attacks.
* Understanding DNS is essential for SOC analysts because DNS logs provide valuable evidence during threat hunting, incident response, malware investigations, and network monitoring.
