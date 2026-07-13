# The OSI Model

## Definition of the OSI Model

The **Open Systems Interconnection (OSI) Model** is a conceptual framework developed by the **International Organization for Standardization (ISO)** to explain how data is transmitted between devices on a network. It divides the communication process into **seven layers**, each with a specific responsibility.

The OSI Model helps network engineers, cybersecurity professionals, and software developers understand how different networking technologies work together. Although modern networks primarily use the TCP/IP model, the OSI Model remains an essential learning tool and is widely used for troubleshooting and security analysis.

---

# The Seven Layers of the OSI Model

## Layer 7 – Application Layer

The **Application Layer** is the layer closest to the user. It provides network services directly to applications, allowing users to access web pages, send emails, transfer files, and communicate over the internet.

### Functions

* Provides network services to applications.
* Supports web browsing, email, file transfer, and remote access.
* Acts as the interface between users and the network.

### Common Protocols

* HTTP
* HTTPS
* FTP
* SMTP
* POP3
* IMAP
* DNS

### Devices

* Web Servers
* Email Servers
* Proxy Servers
* Client Applications (Web Browsers)

---

## Layer 6 – Presentation Layer

The **Presentation Layer** ensures that data is presented in a format both the sender and receiver can understand.

### Functions

* Data translation
* Data encryption and decryption
* Data compression

### Common Protocols and Standards

* SSL/TLS
* JPEG
* PNG
* GIF
* ASCII
* Unicode

### Devices

This layer is primarily implemented in software rather than dedicated hardware.

---

## Layer 5 – Session Layer

The **Session Layer** establishes, manages, and terminates communication sessions between devices.

### Functions

* Creates communication sessions
* Maintains active sessions
* Ends sessions after communication is complete
* Synchronizes data exchange

### Common Protocols

* NetBIOS
* RPC (Remote Procedure Call)
* SMB Session Services

### Devices

This layer is also mainly handled by software running on client and server systems.

---

## Layer 4 – Transport Layer

The **Transport Layer** ensures reliable or fast delivery of data between devices.

### Functions

* Segments data into smaller pieces
* Error detection
* Flow control
* End-to-end communication
* Data reassembly

### Common Protocols

* TCP
* UDP

### Devices

* Firewalls
* Load Balancers

---

## Layer 3 – Network Layer

The **Network Layer** determines the best path for data to travel between networks using logical addressing.

### Functions

* Routing
* Logical addressing (IP addresses)
* Packet forwarding
* Path selection

### Common Protocols

* IPv4
* IPv6
* ICMP
* IPsec
* OSPF
* RIP

### Devices

* Routers
* Layer 3 Switches

---

## Layer 2 – Data Link Layer

The **Data Link Layer** is responsible for communication between devices on the same local network.

### Functions

* Uses MAC addresses
* Error detection
* Frame creation
* Media access control

### Common Protocols

* Ethernet (IEEE 802.3)
* Wi-Fi (IEEE 802.11)
* PPP
* ARP

### Devices

* Switches
* Bridges
* Wireless Access Points

---

## Layer 1 – Physical Layer

The **Physical Layer** transmits raw bits across physical media.

### Functions

* Electrical and optical signal transmission
* Cable specifications
* Physical connectors
* Data transmission over wired and wireless media

### Standards

* Ethernet Cabling
* Fiber Optic
* USB
* Bluetooth
* Radio Signals

### Devices

* Network Cables
* Hubs
* Repeaters
* Connectors

---

# Summary Table of the OSI Model

| Layer | Name         | Main Function                                  | Common Protocols                   | Common Devices             |
| ----- | ------------ | ---------------------------------------------- | ---------------------------------- | -------------------------- |
| 7     | Application  | Provides services to user applications         | HTTP, HTTPS, FTP, SMTP, DNS        | Web Servers, Email Servers |
| 6     | Presentation | Translation, encryption, compression           | SSL/TLS, JPEG, PNG                 | Software                   |
| 5     | Session      | Establishes and manages communication sessions | NetBIOS, RPC                       | Software                   |
| 4     | Transport    | Reliable data delivery                         | TCP, UDP                           | Firewalls, Load Balancers  |
| 3     | Network      | Routing and logical addressing                 | IP, ICMP, OSPF, RIP                | Routers, Layer 3 Switches  |
| 2     | Data Link    | MAC addressing and framing                     | Ethernet, Wi-Fi, PPP, ARP          | Switches, Bridges          |
| 1     | Physical     | Transmits bits over media                      | Ethernet Cabling, Fiber, Bluetooth | Cables, Hubs, Repeaters    |

---

# Why the OSI Model Matters in Cybersecurity

The OSI Model is one of the most important concepts in cybersecurity because it helps security professionals understand where attacks occur and how to defend against them.

A Security Operations Center (SOC) analyst uses the OSI Model to:

* Troubleshoot network communication problems.
* Analyze network traffic captured with tools like Wireshark.
* Understand how different cyberattacks target specific layers.
* Investigate firewall, router, and switch logs.
* Detect suspicious or malicious network activity.
* Configure security devices correctly.
* Improve incident response by identifying where communication failures or attacks occur.

### Examples of Security Threats by Layer

| Layer        | Example Threat                                      |
| ------------ | --------------------------------------------------- |
| Application  | SQL Injection, Cross-Site Scripting (XSS), Phishing |
| Presentation | Weak or broken encryption                           |
| Session      | Session Hijacking                                   |
| Transport    | TCP SYN Flood, Port Scanning                        |
| Network      | IP Spoofing, DDoS, Routing Attacks                  |
| Data Link    | ARP Spoofing, MAC Flooding                          |
| Physical     | Cable Tampering, Device Theft                       |

---

# Key Takeaways

* The OSI Model divides network communication into **seven layers**.
* Each layer has a specific role and works together to ensure reliable communication.
* Understanding the OSI Model makes troubleshooting easier.
* Many networking protocols operate at specific OSI layers.
* Cybersecurity professionals use the OSI Model to identify where attacks occur and apply appropriate defenses.
* A strong understanding of the OSI Model is a fundamental skill for every SOC analyst.
