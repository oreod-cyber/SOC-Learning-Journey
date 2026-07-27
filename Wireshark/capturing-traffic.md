# Packet Capture Fundamentals

## Definition of Packet Capture

**Packet Capture (PCAP)** is the process of intercepting, collecting, and recording network packets as they travel across a network. It allows cybersecurity professionals, network administrators, and SOC analysts to inspect network communications in detail.

Every activity performed on a network—such as opening a website, sending an email, downloading a file, or logging into an application—generates packets. Packet capture records these packets so they can be analyzed either in real time or later using tools such as **Wireshark**.

Packet capture is one of the most important techniques used in network troubleshooting, digital forensics, malware analysis, and incident response.

---

# Why Packet Capture is Important

Packet capture provides visibility into network communications that cannot always be obtained from logs alone.

By capturing packets, analysts can determine:

* Who initiated a network connection.
* Which devices communicated.
* Which protocols were used.
* What data was exchanged (if it is not encrypted).
* Whether malicious activity occurred.
* How an attacker moved through the network.

Packet captures often serve as valuable evidence during cybersecurity investigations.

---

# Steps to Capture Packets

Capturing packets is straightforward, but selecting the correct settings is essential to collect useful data.

## Step 1: Open a Packet Capture Tool

Launch a packet capture tool such as **Wireshark**.

Wireshark displays all available network interfaces on the computer.

---

## Step 2: Choose the Correct Network Interface

Select the interface through which the desired traffic is flowing.

Common interfaces include:

* Ethernet
* Wi-Fi (Wireless LAN)
* VPN Adapter
* Virtual Machine Network Adapter
* Loopback Interface

Choosing the wrong interface may result in capturing little or no useful traffic.

---

## Step 3: (Optional) Apply a Capture Filter

Before starting the capture, you can apply a **capture filter** to limit which packets are recorded.

This reduces unnecessary traffic and keeps the capture focused on the investigation.

---

## Step 4: Start the Capture

Click **Start** to begin capturing packets.

As network traffic flows, packets appear in real time.

---

## Step 5: Generate or Observe Network Activity

Perform the activity you want to analyze, such as:

* Browsing a website.
* Sending an email.
* Running a DNS lookup.
* Pinging another device.
* Connecting to a remote server.

The corresponding packets will appear in the capture window.

---

## Step 6: Stop the Capture

Once enough data has been collected, stop the capture.

Stopping the capture prevents unnecessary packets from being recorded and makes analysis easier.

---

## Step 7: Analyze or Save the Capture

Review the captured packets using Wireshark's analysis tools.

If needed, save the capture as a **PCAP** file so it can be shared with other analysts or examined later.

---

# Choosing the Correct Interface

Selecting the correct network interface is one of the most important steps in packet capture.

Different interfaces capture different types of traffic.

| Interface               | Typical Use                                                           |
| ----------------------- | --------------------------------------------------------------------- |
| Ethernet                | Captures traffic on a wired network connection.                       |
| Wi-Fi                   | Captures wireless network traffic.                                    |
| VPN Adapter             | Captures encrypted VPN traffic entering or leaving the device.        |
| Loopback                | Captures traffic sent from the computer to itself (127.0.0.1 or ::1). |
| Virtual Machine Adapter | Captures traffic between virtual machines and the host system.        |

### Example

If you are connected to the Internet through Wi-Fi but accidentally capture packets from the Ethernet interface, you may not capture any useful traffic because your network communication is occurring over the wireless adapter.

---

# Capture Filters vs. Display Filters

Wireshark supports **capture filters** and **display filters**, but they serve different purposes.

## Capture Filters

Capture filters determine **which packets are recorded** during the capture process.

Packets that do not match the filter are **never captured**.

Capture filters improve performance by reducing the amount of collected traffic.

### Examples

```text id="cf1"
host 192.168.1.100
```

Captures only traffic to or from **192.168.1.100**.

```text id="cf2"
port 80
```

Captures only traffic using **port 80**.

```text id="cf3"
tcp
```

Captures only TCP traffic.

---

## Display Filters

Display filters are applied **after** packets have already been captured.

They do not remove packets from the capture—they simply hide packets that do not match the filter.

This allows analysts to focus on specific traffic without losing any captured data.

### Examples

```text id="df1"
http
```

Displays only HTTP packets.

```text id="df2"
dns
```

Displays only DNS packets.

```text id="df3"
ip.addr == 192.168.1.100
```

Displays packets involving the specified IP address.

---

# Capture Filters vs Display Filters Comparison

| Feature     | Capture Filter                           | Display Filter                                            |
| ----------- | ---------------------------------------- | --------------------------------------------------------- |
| Applied     | Before packet capture                    | After packet capture                                      |
| Purpose     | Controls which packets are recorded      | Controls which captured packets are displayed             |
| Performance | Reduces captured traffic                 | Does not reduce captured traffic                          |
| Data Loss   | Packets not captured cannot be recovered | No data is lost because all packets remain in the capture |
| Common Use  | Focused packet collection                | Packet analysis and investigation                         |

---

# Why SOC Analysts Capture Network Traffic

Packet captures provide evidence that cannot always be found in system logs or security alerts.

SOC analysts capture network traffic to:

* Investigate suspicious network activity.
* Analyze malware communications.
* Detect Command-and-Control (C2) traffic.
* Investigate phishing attacks.
* Troubleshoot network problems.
* Validate firewall, IDS, and IPS alerts.
* Examine DNS queries.
* Identify data exfiltration attempts.
* Support digital forensics.
* Collect evidence during incident response.

### Example

Suppose a SIEM generates an alert indicating that an employee's computer communicated with an unfamiliar external IP address.

A SOC analyst captures the device's network traffic and discovers:

* Repeated DNS queries to suspicious domains.
* HTTPS connections to an unknown server.
* Large outbound data transfers.

By analyzing the packet capture, the analyst can determine whether the device is infected with malware, identify the communication pattern, and begin containment procedures.

---

# Best Practices for Packet Capture

To capture useful and reliable network traffic, follow these best practices:

* Capture traffic only on networks you are authorized to monitor.
* Choose the correct network interface before starting.
* Use capture filters to reduce unnecessary traffic when appropriate.
* Use display filters to simplify analysis after the capture.
* Record the purpose, time, and location of each capture.
* Keep packet captures as short as practical to reduce file size.
* Save important captures as PCAP files for future investigation.
* Protect PCAP files because they may contain sensitive information such as IP addresses, usernames, or unencrypted data.
* Correlate packet captures with SIEM, firewall, DNS, VPN, and endpoint logs for a more complete investigation.

---

# Common Challenges During Packet Capture

SOC analysts may encounter several challenges when capturing network traffic, including:

* Selecting the wrong network interface.
* Capturing excessive background traffic.
* Encrypted traffic that cannot be easily inspected.
* Large PCAP files that are difficult to analyze.
* Missing packets due to high network speeds or hardware limitations.

Understanding these challenges helps analysts plan more effective packet captures.

---

# Key Takeaways

* **Packet capture** is the process of recording network packets for analysis.
* Tools such as **Wireshark** allow analysts to capture and inspect network traffic.
* Choosing the correct network interface is essential for collecting relevant packets.
* **Capture filters** determine which packets are recorded, while **display filters** determine which captured packets are shown.
* SOC analysts use packet captures to investigate cyberattacks, analyze malware, troubleshoot networks, and support digital forensic investigations.
* Following best practices—such as using the correct interface, applying appropriate filters, and protecting PCAP files—helps ensure successful and secure packet analysis.
