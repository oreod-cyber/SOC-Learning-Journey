# Wireshark Fundamentals

## Definition of Wireshark

**Wireshark** is a free and open-source **network protocol analyzer** (also known as a packet analyzer) used to capture, inspect, and analyze network traffic in real time or from previously captured network data.

Wireshark allows network administrators, cybersecurity professionals, and SOC analysts to see exactly what is happening on a network by examining the individual packets exchanged between devices.

It supports hundreds of networking protocols and runs on Windows, Linux, and macOS, making it one of the most widely used tools in networking and cybersecurity.

---

# Why SOC Analysts Use Wireshark

SOC analysts use Wireshark to investigate network activity and identify signs of malicious behavior. It provides visibility into network communications, allowing analysts to understand how devices interact and detect suspicious traffic.

Wireshark helps SOC analysts to:

* Capture live network traffic.
* Analyze suspicious network connections.
* Investigate malware communication.
* Detect Command-and-Control (C2) traffic.
* Troubleshoot network issues.
* Examine protocol behavior.
* Verify firewall and IDS/IPS alerts.
* Investigate phishing and ransomware incidents.
* Support digital forensics and incident response.

For many investigations, Wireshark provides the detailed packet-level evidence needed to understand exactly what happened during an attack.

---

# What is a Packet?

A **packet** is the smallest unit of data transmitted across a network.

When a device sends information—such as loading a website, sending an email, or downloading a file—the data is divided into smaller pieces called packets. These packets travel independently across the network and are reassembled when they reach their destination.

Each packet contains important information, including:

* Source IP address.
* Destination IP address.
* Source port.
* Destination port.
* Protocol (such as TCP, UDP, or ICMP).
* Header information.
* Payload (the actual data being transmitted).

By examining packets, SOC analysts can determine who communicated, what protocol was used, and whether the communication appears legitimate or malicious.

---

# What is a PCAP File?

A **PCAP (Packet Capture)** file is a file that stores captured network packets.

Instead of analyzing live traffic, analysts can save network captures into a PCAP file and examine them later using Wireshark or other packet analysis tools.

PCAP files are widely used for:

* Incident response.
* Digital forensics.
* Malware analysis.
* Network troubleshooting.
* Security investigations.
* Cybersecurity training.

Think of a PCAP file as a recording of network activity that can be replayed and analyzed whenever needed.

---

# The Wireshark Interface

When you open a packet capture in Wireshark, the interface is divided into **three main panes**.

## 1. Packet List Pane

The **Packet List Pane** is the top section of the interface.

It displays every captured packet in chronological order.

For each packet, Wireshark displays information such as:

* Packet number.
* Capture time.
* Source IP address.
* Destination IP address.
* Protocol.
* Packet length.
* Brief description (Info column).

This pane provides a quick overview of all captured network traffic.

---

## 2. Packet Details Pane

The **Packet Details Pane** is the middle section.

It displays a hierarchical breakdown of the selected packet.

Information commonly shown includes:

* Ethernet Header.
* IP Header.
* TCP or UDP Header.
* DNS Information.
* HTTP Requests.
* TLS Information.
* Application Layer Data.

Analysts use this pane to understand exactly how a packet is structured.

---

## 3. Packet Bytes Pane

The **Packet Bytes Pane** is located at the bottom.

It displays the raw contents of the selected packet in both hexadecimal and ASCII formats.

This view allows analysts to inspect the exact bytes transmitted across the network.

---

# Summary of the Three Panes

| Pane                    | Purpose                                                                       |
| ----------------------- | ----------------------------------------------------------------------------- |
| **Packet List Pane**    | Displays all captured packets with basic information.                         |
| **Packet Details Pane** | Displays the decoded protocol information for the selected packet.            |
| **Packet Bytes Pane**   | Displays the raw hexadecimal and ASCII representation of the selected packet. |

---

# Common Wireshark Display Filters

Display filters allow analysts to quickly locate specific packets within a capture.

Below are some of the most commonly used filters.

| Display Filter            | Purpose                                                  |
| ------------------------- | -------------------------------------------------------- |
| `ip.addr == 192.168.1.10` | Shows traffic involving a specific IP address.           |
| `tcp`                     | Displays only TCP packets.                               |
| `udp`                     | Displays only UDP packets.                               |
| `icmp`                    | Displays ICMP traffic (such as ping).                    |
| `dns`                     | Displays DNS traffic.                                    |
| `http`                    | Displays HTTP traffic.                                   |
| `tls`                     | Displays encrypted TLS traffic.                          |
| `arp`                     | Displays ARP packets.                                    |
| `ftp`                     | Displays FTP traffic.                                    |
| `smtp`                    | Displays SMTP traffic.                                   |
| `tcp.port == 80`          | Shows traffic using TCP port 80.                         |
| `tcp.port == 443`         | Shows traffic using HTTPS (TCP port 443).                |
| `dns.flags.response == 0` | Displays DNS queries only.                               |
| `ip.src == 10.0.0.5`      | Shows packets from a specific source IP address.         |
| `ip.dst == 8.8.8.8`       | Shows packets sent to a specific destination IP address. |

Display filters make investigations faster by reducing large packet captures to only the traffic relevant to the investigation.

---

# Practical Example

Suppose a SIEM generates an alert indicating that a workstation communicated with a suspicious external IP address.

A SOC analyst opens the associated PCAP file in Wireshark and applies filters such as:

```text
ip.addr == 203.0.113.50
```

or

```text
dns
```

The analyst discovers that the workstation repeatedly contacted a suspicious domain before connecting to an unknown external server over HTTPS.

By examining the packets, the analyst can determine:

* Which device initiated the connection.
* When the communication occurred.
* Which protocols were used.
* Whether files were downloaded.
* Whether the communication resembles malware or Command-and-Control (C2) traffic.

This information helps guide the incident response process.

---

# Why Wireshark is Important in Cybersecurity

Wireshark is one of the most valuable tools in cybersecurity because it provides complete visibility into network communications.

SOC analysts rely on Wireshark to:

* Investigate suspicious network activity.
* Analyze malware communications.
* Identify Command-and-Control (C2) traffic.
* Detect network scanning.
* Investigate DNS anomalies.
* Examine HTTP and HTTPS traffic.
* Troubleshoot network problems.
* Validate firewall and IDS/IPS alerts.
* Support digital forensics.
* Collect evidence during incident response.

Because every network communication is transmitted as packets, understanding packet analysis is a critical skill for every cybersecurity professional.

---

# Best Practices for Using Wireshark

To use Wireshark effectively and responsibly:

* Capture traffic only on networks you are authorized to monitor.
* Apply display filters to focus on relevant traffic.
* Save important captures as PCAP files for future analysis.
* Correlate Wireshark findings with SIEM, firewall, DNS, and endpoint logs.
* Learn common protocols such as TCP, UDP, HTTP, DNS, DHCP, ICMP, and TLS.
* Protect PCAP files, as they may contain sensitive information.

---

# Key Takeaways

* **Wireshark** is a free and open-source packet analyzer used to capture and analyze network traffic.
* SOC analysts use Wireshark to investigate suspicious activity, troubleshoot network issues, and support incident response.
* A **packet** is the smallest unit of data transmitted across a network.
* A **PCAP file** stores captured network packets for later analysis.
* The Wireshark interface consists of three panes: the **Packet List Pane**, **Packet Details Pane**, and **Packet Bytes Pane**.
* Display filters help analysts quickly locate specific traffic within a packet capture.
* Wireshark is an essential cybersecurity tool because it enables deep packet inspection, helping analysts detect, investigate, and respond to network-based threats.
