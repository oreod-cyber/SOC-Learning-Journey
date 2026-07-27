# Windows Fundamentals for SOC Analysts

## Why Windows is Important for SOC Analysts

Microsoft Windows is the most widely used desktop operating system in businesses, government organizations, educational institutions, and enterprise environments. Because of its widespread adoption, it is also one of the primary targets for cyberattacks.

Most security incidents investigated by Security Operations Center (SOC) analysts involve Windows systems. Whether it is a phishing attack, malware infection, ransomware outbreak, privilege escalation, or unauthorized access, analysts often rely on Windows logs and system artifacts to understand what happened.

A strong understanding of Windows enables SOC analysts to:

* Investigate security incidents.
* Analyze Windows Event Logs.
* Detect malware infections.
* Identify suspicious processes and services.
* Investigate user activity.
* Understand Windows authentication.
* Examine file system activity.
* Perform digital forensic investigations.

For anyone pursuing a SOC analyst career, Windows knowledge is a fundamental skill.

---

# Definition of an Operating System

An **Operating System (OS)** is system software that manages a computer's hardware and software resources while providing services for applications and users.

The operating system acts as the bridge between computer hardware and the programs people use every day.

Its responsibilities include:

* Managing memory.
* Managing files and storage.
* Running applications.
* Managing hardware devices.
* Providing user interfaces.
* Enforcing security and permissions.
* Handling network communication.

Examples of operating systems include:

* Microsoft Windows
* Linux
* macOS
* Android
* iOS

---

# Windows Architecture

Windows uses a layered architecture designed to provide stability, security, and efficient resource management.

At a high level, Windows consists of two main operating modes:

* **User Mode**
* **Kernel Mode**

Applications generally run in User Mode, while the Windows kernel and core operating system components run in Kernel Mode.

```
+------------------------------------+
|           User Applications        |
| Chrome | Word | Outlook | Teams    |
+------------------------------------+
|              User Mode             |
+------------------------------------+
|             Kernel Mode            |
| Windows Kernel | Drivers | Memory  |
+------------------------------------+
|             Hardware               |
| CPU | RAM | Disk | Network Card    |
+------------------------------------+
```

This separation helps prevent application failures from crashing the entire operating system.

---

# User Mode vs. Kernel Mode

## User Mode

**User Mode** is the restricted operating mode where most applications execute.

Applications running in User Mode cannot directly access hardware or critical system memory. Instead, they must request services from the operating system.

### Characteristics

* Limited privileges.
* Isolated from the Windows kernel.
* Cannot directly access hardware.
* Failures usually affect only the application.
* Safer and more secure.

### Examples

* Microsoft Word
* Google Chrome
* Microsoft Outlook
* Notepad
* Microsoft Teams

---

## Kernel Mode

**Kernel Mode** is the privileged operating mode where the Windows kernel, hardware drivers, and core system components execute.

Programs running in Kernel Mode have unrestricted access to system memory and hardware resources.

### Characteristics

* Full system privileges.
* Direct access to hardware.
* Manages memory and processes.
* Controls device drivers.
* Failures can cause system crashes, such as the Blue Screen of Death (BSOD).

### Examples

* Windows Kernel
* Device Drivers
* Memory Manager
* Process Scheduler
* File System Driver

---

# User Mode vs. Kernel Mode Comparison

| Feature                 | User Mode                       | Kernel Mode                           |
| ----------------------- | ------------------------------- | ------------------------------------- |
| Privilege Level         | Limited                         | Full                                  |
| Hardware Access         | Indirect                        | Direct                                |
| Access to System Memory | Restricted                      | Full                                  |
| Typical Programs        | Applications                    | Kernel and Drivers                    |
| Crash Impact            | Usually affects one application | May crash the entire operating system |
| Security Risk           | Lower                           | Higher if compromised                 |

---

# Windows Registry

## Definition

The **Windows Registry** is a hierarchical database that stores configuration settings for the Windows operating system, installed applications, hardware devices, and user preferences.

Almost every Windows component relies on the Registry to store and retrieve configuration information.

Common information stored in the Registry includes:

* Installed software settings.
* User account preferences.
* Startup programs.
* Device configurations.
* File associations.
* Security settings.
* Network configuration.

### Registry Structure

The Registry is organized into major sections called **Registry Hives**.

Some important hives include:

| Registry Hive                  | Purpose                                            |
| ------------------------------ | -------------------------------------------------- |
| **HKEY_LOCAL_MACHINE (HKLM)**  | Stores system-wide settings.                       |
| **HKEY_CURRENT_USER (HKCU)**   | Stores settings for the currently logged-in user.  |
| **HKEY_CLASSES_ROOT (HKCR)**   | Stores file associations and COM information.      |
| **HKEY_USERS (HKU)**           | Stores settings for all user profiles.             |
| **HKEY_CURRENT_CONFIG (HKCC)** | Stores current hardware configuration information. |

### Why It Matters

Attackers frequently modify Registry keys to:

* Achieve persistence after a reboot.
* Disable security software.
* Change system configurations.
* Execute malware automatically at startup.

SOC analysts often examine Registry changes during incident response and forensic investigations.

---

# Explorer.exe

## Definition

**Explorer.exe** is the Windows process responsible for providing the graphical user interface (GUI).

It manages:

* The Desktop.
* The Taskbar.
* The Start Menu.
* File Explorer.
* Windows navigation.

Without Explorer.exe, Windows would still be running, but users would not have the familiar graphical interface.

### Why It Matters

Because Explorer.exe is always running during normal user sessions, attackers sometimes exploit or inject malicious code into it to hide their activities.

SOC analysts often examine Explorer.exe when investigating:

* Process injection.
* Malware execution.
* Suspicious child processes.
* Unauthorized file access.

---

# Windows Services

## Definition

A **Windows Service** is a background program that performs system or application tasks without requiring user interaction.

Services often start automatically when Windows boots and continue running in the background.

### Common Examples

* Windows Update
* Windows Defender
* Print Spooler
* DHCP Client
* DNS Client
* Event Log Service

### Why Services Matter

Attackers sometimes:

* Install malicious services.
* Modify existing services.
* Change service startup types.
* Disable security-related services.

SOC analysts monitor Windows services to identify persistence mechanisms and suspicious system changes.

---

# NTFS (New Technology File System)

## Definition

**NTFS (New Technology File System)** is the default file system used by modern versions of Microsoft Windows.

A file system determines how files are stored, organized, accessed, and protected on storage devices.

### Key Features

* File and folder permissions (ACLs).
* File compression.
* File encryption (EFS).
* Disk quotas.
* Journaling for improved reliability.
* Support for large files and partitions.

### Why NTFS Matters

NTFS stores important security information, including:

* File ownership.
* Access permissions.
* Audit settings.
* File timestamps.
* Metadata.

SOC analysts use NTFS metadata to:

* Investigate unauthorized file access.
* Analyze malware behavior.
* Reconstruct attack timelines.
* Perform forensic investigations.

---

# How These Components Work Together

Windows components work together to provide a secure and stable operating environment.

* The **Operating System** manages hardware and software resources.
* **User Mode** runs applications with limited privileges.
* **Kernel Mode** controls the core operating system and hardware.
* The **Windows Registry** stores system and application settings.
* **Explorer.exe** provides the graphical user interface.
* **Windows Services** perform background tasks and system functions.
* **NTFS** organizes files while enforcing permissions and maintaining file metadata.

Understanding how these components interact helps SOC analysts recognize normal system behavior and identify malicious activity.

---

# Why These Windows Components are Important in Cybersecurity

Windows components are frequently involved in cyberattacks. Malware authors often abuse legitimate Windows features to gain persistence, escalate privileges, evade detection, or execute malicious code.

SOC analysts use their knowledge of Windows internals to:

* Investigate malware infections.
* Analyze suspicious processes.
* Detect persistence mechanisms.
* Examine Registry modifications.
* Review service configurations.
* Analyze file system artifacts.
* Investigate user activity.
* Correlate Windows Event Logs with system behavior.
* Support digital forensic investigations.

### Example

A SIEM generates an alert indicating that a suspicious executable launched every time a user logs in.

During the investigation, a SOC analyst discovers:

* A new **Registry Run** key that automatically starts the malware.
* A malicious **Windows Service** configured to restart if stopped.
* The malware executing through **Explorer.exe**.
* Suspicious files stored on an **NTFS** volume with recently modified timestamps.

By examining these Windows components together, the analyst can determine how the malware achieved persistence, assess its impact, and remove it from the system.

---

# Best Practices for Windows Security

Organizations should adopt the following practices to improve Windows security:

* Keep Windows and installed software updated.
* Enable Windows Defender or another trusted endpoint protection solution.
* Monitor Windows Event Logs.
* Audit Registry and service changes.
* Apply the principle of least privilege.
* Use strong authentication, including multi-factor authentication (MFA).
* Restrict administrative access.
* Monitor startup programs and scheduled tasks.
* Regularly review file permissions on NTFS volumes.
* Integrate Windows logs with a SIEM platform for centralized monitoring.

---

# Key Takeaways

* **Windows** is the most widely used operating system in enterprise environments, making it a primary target for cyberattacks.
* An **Operating System** manages hardware, software, and system resources while providing services to applications.
* Windows architecture is divided into **User Mode** and **Kernel Mode**, providing stability and security through privilege separation.
* The **Windows Registry** stores system and application configuration settings and is commonly abused by attackers for persistence.
* **Explorer.exe** provides the Windows graphical user interface and is sometimes targeted by malware.
* **Windows Services** run background tasks and can be exploited or modified by attackers.
* **NTFS** is the default Windows file system and stores critical security metadata used during forensic investigations.
* Understanding these Windows components is essential for SOC analysts because they are central to incident response, malware analysis, threat hunting, and digital forensics.
