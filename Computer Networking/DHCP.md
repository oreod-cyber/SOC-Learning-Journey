# Dynamic Host Configuration Protocol (DHCP)

## Definition of DHCP

**DHCP (Dynamic Host Configuration Protocol)** is a network management protocol that automatically assigns IP addresses and other network configuration settings to devices when they join a network.

Instead of manually configuring every computer, smartphone, printer, or server with an IP address, DHCP allows devices to obtain the required network settings automatically from a **DHCP server**.

A DHCP server typically provides:

* IP address
* Subnet mask
* Default gateway
* DNS server addresses
* Lease duration
* Other network configuration options

DHCP simplifies network administration and reduces configuration errors, making it an essential service in both home and enterprise networks.

---

# Why DHCP is Needed

Without DHCP, network administrators would have to manually configure every device with an IP address and other network settings. This process would be time-consuming, difficult to manage, and prone to errors.

DHCP provides several important benefits:

* Automatically assigns IP addresses.
* Prevents IP address conflicts.
* Reduces administrative workload.
* Allows devices to join networks quickly.
* Ensures devices receive the correct network configuration.
* Makes managing large networks much easier.

### Example

Imagine a company with **500 employees**.

Without DHCP:

* Every computer would need to be manually configured.
* Mistakes could lead to duplicate IP addresses or incorrect network settings.

With DHCP:

* Each computer automatically receives the correct network configuration as soon as it connects to the network.

---

# The DORA Process

When a device connects to a network, it communicates with the DHCP server using a four-step process known as **DORA**:

* **D** – Discover
* **O** – Offer
* **R** – Request
* **A** – Acknowledge

This process allows a device to obtain a valid IP address and network configuration automatically.

### Step 1: DHCP Discover

A new device does not yet have an IP address.

It broadcasts a **DHCP Discover** message across the local network to locate any available DHCP servers.

---

### Step 2: DHCP Offer

The DHCP server receives the Discover message and responds with a **DHCP Offer**.

The offer usually includes:

* Available IP address
* Subnet mask
* Default gateway
* DNS server
* Lease duration

---

### Step 3: DHCP Request

The client accepts one of the offered IP addresses and sends a **DHCP Request** message to the DHCP server.

This lets the server know which offered address the client wishes to use.

---

### Step 4: DHCP Acknowledge (ACK)

The DHCP server confirms the assignment by sending a **DHCP ACK** message.

The client can now use the assigned IP address to communicate on the network.

---

### Summary of the DORA Process

| Step | Message           | Purpose                                     |
| ---- | ----------------- | ------------------------------------------- |
| 1    | Discover          | Client searches for a DHCP server           |
| 2    | Offer             | Server offers an available IP address       |
| 3    | Request           | Client requests the offered IP address      |
| 4    | Acknowledge (ACK) | Server confirms the lease and configuration |

---

# DHCP Ports

DHCP uses **UDP** because it provides fast communication without the overhead of establishing a connection.

| Device      | Port   | Protocol                |
| ----------- | ------ | ----------------------- |
| DHCP Server | UDP 67 | Receives DHCP requests  |
| DHCP Client | UDP 68 | Receives DHCP responses |

### Why UDP?

DHCP clients often do not yet have an IP address when communication begins. UDP allows clients to broadcast messages efficiently without first establishing a connection, making it ideal for the initial IP assignment process.

---

# DHCP Lease

A **DHCP lease** is the amount of time that a client is allowed to use an assigned IP address.

The lease is temporary rather than permanent.

When the lease expires, the client contacts the DHCP server to renew it. If the renewal succeeds, the client keeps the same IP address (or receives a new one if necessary).

### Example

A network administrator configures a lease time of **24 hours**.

* Laptop joins the network at **9:00 AM**.
* DHCP assigns **192.168.1.25**.
* The lease expires at **9:00 AM the next day**.
* Before expiration, the laptop requests a lease renewal.

This process helps DHCP efficiently manage available IP addresses.

---

# Common DHCP Attacks

Although DHCP simplifies networking, attackers may exploit it if proper security controls are not in place.

## DHCP Starvation Attack

In a **DHCP Starvation** attack, an attacker floods the DHCP server with numerous fake DHCP requests using different spoofed MAC addresses.

The goal is to exhaust the DHCP server's available IP address pool so that legitimate users cannot obtain an IP address.

### Impact

* Legitimate users cannot join the network.
* Network services become unavailable.
* Can be used as a precursor to a Rogue DHCP attack.

---

## Rogue DHCP Server

A **Rogue DHCP Server** is an unauthorized DHCP server connected to a network.

Instead of receiving configuration from the legitimate DHCP server, clients may receive malicious network settings from the rogue server.

An attacker can provide:

* A malicious default gateway.
* Malicious DNS servers.
* Incorrect subnet information.

This allows the attacker to intercept, monitor, redirect, or manipulate network traffic.

---

## DHCP Spoofing

DHCP spoofing occurs when an attacker impersonates a legitimate DHCP server and provides false network configuration to clients.

Victims may unknowingly send their traffic through systems controlled by the attacker.

---

## Man-in-the-Middle (MITM) Attacks

A rogue DHCP server can redirect network traffic through an attacker's device.

This enables the attacker to:

* Capture sensitive information.
* Monitor user activity.
* Modify network traffic.
* Launch additional attacks against victims.

---

# Protecting DHCP Services

Organizations can reduce DHCP-related risks by implementing the following security measures:

* Enable **DHCP Snooping** on managed switches.
* Allow DHCP responses only from trusted switch ports.
* Use **Port Security** to limit unauthorized devices.
* Monitor for rogue DHCP servers.
* Regularly review DHCP logs.
* Use network access control (NAC) where appropriate.
* Keep networking devices updated with security patches.

---

# Why DHCP is Important in Cybersecurity

Although DHCP primarily manages IP address assignment, it also plays an important role in cybersecurity.

SOC analysts frequently analyze DHCP logs to understand which device was assigned a particular IP address at a specific time.

DHCP information helps analysts:

* Identify devices involved in security incidents.
* Correlate IP addresses with physical devices.
* Investigate unauthorized devices joining the network.
* Detect rogue DHCP servers.
* Investigate DHCP starvation attacks.
* Correlate DHCP logs with DNS, firewall, VPN, proxy, endpoint, and SIEM logs.
* Trace attacker activity during incident response.

### Example

Suppose a SIEM generates an alert indicating suspicious activity from **192.168.10.55**.

A SOC analyst reviews the DHCP logs and discovers:

* The IP address was assigned to a laptop.
* The device connected at **8:12 AM**.
* The device belongs to the Finance department.
* The lease duration is 24 hours.

Using this information, the analyst can identify the affected device, correlate other security logs, determine the scope of the incident, and begin containment and remediation.

---

# Best Practices for DHCP Security

To secure DHCP services, organizations should:

* Enable DHCP Snooping on managed switches.
* Block unauthorized DHCP servers.
* Monitor DHCP logs continuously.
* Use strong network segmentation.
* Maintain an accurate inventory of leased IP addresses.
* Regularly audit DHCP server configurations.
* Integrate DHCP logs into SIEM platforms for centralized monitoring.

---

# Key Takeaways

* **DHCP (Dynamic Host Configuration Protocol)** automatically assigns IP addresses and network settings to devices.
* DHCP eliminates the need for manual IP address configuration.
* The **DORA** process consists of **Discover, Offer, Request, and Acknowledge (ACK)**.
* DHCP uses **UDP Port 67** (server) and **UDP Port 68** (client).
* A **DHCP lease** defines how long a client may use an assigned IP address.
* Common DHCP attacks include **DHCP Starvation**, **Rogue DHCP Servers**, **DHCP Spoofing**, and **Man-in-the-Middle (MITM)** attacks.
* DHCP logs are valuable during incident response because they help SOC analysts identify which device was using a particular IP address at a specific time.
* Understanding DHCP is essential for SOC analysts because it supports network visibility, device identification, threat detection, and forensic investigations.
