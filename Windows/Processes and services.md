# Windows Processes and Services Fundamentals

## Definition of a Process

A **process** is a running instance of a program or application. Whenever you open an application, Windows creates one or more processes to execute the program's instructions.

Each process has its own resources, including:

* Process ID (PID).
* Memory allocation.
* CPU usage.
* Security context.
* Open files.
* Network connections.
* Threads.

A single application can create multiple processes, and multiple instances of the same application can run simultaneously.

For example, opening two separate instances of Notepad creates two different processes, each with its own Process ID (PID).

---

# Definition of a Windows Service

A **Windows Service** is a background process that performs system or application tasks without requiring direct user interaction.

Unlike most applications, services can start automatically when Windows boots and continue running even when no user is logged in.

Windows services support many essential functions, including:

* Network connectivity.
* Windows Update.
* Printing.
* Event logging.
* Antivirus protection.
* DHCP and DNS client services.
* Remote management.

Because services often run with elevated privileges, attackers frequently target them to achieve persistence or execute malicious code.

---

# Important Windows Processes and Their Roles

Understanding normal Windows processes helps SOC analysts identify suspicious or malicious activity.

---

## System Idle Process

**Purpose**

Represents unused CPU resources.

### Characteristics

* Always running.
* Uses Process ID (PID) **0**.
* High CPU usage usually means the processor is idle, not busy.

---

## System

**Purpose**

Represents the Windows kernel and core operating system components.

### Characteristics

* Starts during system boot.
* Runs in **Kernel Mode**.
* Essential for Windows operation.

---

## smss.exe (Session Manager Subsystem)

**Purpose**

One of the first user-mode processes started during boot.

### Responsibilities

* Starts system sessions.
* Launches critical Windows processes.
* Initializes the operating environment.

---

## csrss.exe (Client/Server Runtime Subsystem)

**Purpose**

Handles core Windows user-mode operations.

### Responsibilities

* Console windows.
* Thread management.
* Shutdown operations.

Because this is a critical system process, terminating it can cause Windows to become unstable or crash.

---

## wininit.exe (Windows Initialization Process)

**Purpose**

Starts important system services during boot.

### Responsibilities

* Starts the Service Control Manager (services.exe).
* Starts the Local Security Authority (lsass.exe).
* Starts the Local Session Manager (lsm.exe).

---

## services.exe (Service Control Manager)

**Purpose**

Manages Windows services.

### Responsibilities

* Starts services.
* Stops services.
* Monitors service status.
* Maintains service configurations.

SOC analysts often examine this process when investigating malicious services.

---

## lsass.exe (Local Security Authority Subsystem Service)

**Purpose**

Handles Windows authentication and security policies.

### Responsibilities

* User authentication.
* Password verification.
* Access token creation.
* Security policy enforcement.

Because LSASS stores authentication information, it is a common target for credential theft tools such as Mimikatz.

---

## svchost.exe (Service Host)

**Purpose**

Hosts one or more Windows services.

Instead of creating a separate process for every service, Windows groups compatible services inside svchost.exe processes.

### Characteristics

* Multiple instances normally run simultaneously.
* Usually located in:

```text id="9zv41p"
C:\Windows\System32\svchost.exe
```

Numerous svchost.exe processes are normal. However, analysts should verify that they are running from the legitimate directory.

---

## explorer.exe

**Purpose**

Provides the Windows graphical user interface (GUI).

### Responsibilities

* Desktop.
* Taskbar.
* Start Menu.
* File Explorer.

If Explorer.exe stops unexpectedly, the desktop and taskbar may disappear until it is restarted.

---

## winlogon.exe

**Purpose**

Manages user logon and logoff processes.

### Responsibilities

* Displays the Windows logon screen.
* Starts the user shell after authentication.
* Handles secure attention sequences such as **Ctrl + Alt + Delete**.

---

## taskhostw.exe

**Purpose**

Hosts Windows-based background tasks and scheduled operations.

It is commonly associated with Task Scheduler activities.

---

## RuntimeBroker.exe

**Purpose**

Manages permissions for Microsoft Store applications.

It ensures that applications access system resources according to their granted permissions.

---

# Summary of Important Windows Processes

| Process                 | Primary Role                                        |
| ----------------------- | --------------------------------------------------- |
| **System Idle Process** | Represents unused CPU resources.                    |
| **System**              | Windows kernel and core operating system functions. |
| **smss.exe**            | Starts user sessions during system boot.            |
| **csrss.exe**           | Manages console windows and user-mode operations.   |
| **wininit.exe**         | Starts critical Windows processes.                  |
| **services.exe**        | Manages Windows services.                           |
| **lsass.exe**           | Handles authentication and security policies.       |
| **svchost.exe**         | Hosts Windows services.                             |
| **explorer.exe**        | Provides the Windows graphical interface.           |
| **winlogon.exe**        | Manages user logon and logoff.                      |
| **taskhostw.exe**       | Hosts background Windows tasks.                     |
| **RuntimeBroker.exe**   | Manages Microsoft Store application permissions.    |

---

# Common Attacker Tricks

Attackers often disguise malware by imitating legitimate Windows processes or placing malicious files in unusual locations.

## Fake Process Names

A common technique is to create a process name that closely resembles a legitimate Windows process.

Examples include:

| Legitimate Process | Malicious Look-Alike                                 |
| ------------------ | ---------------------------------------------------- |
| `svchost.exe`      | `scvhost.exe`                                        |
| `explorer.exe`     | `expl0rer.exe`                                       |
| `lsass.exe`        | `Isass.exe` (uppercase "I" instead of lowercase "l") |
| `services.exe`     | `service.exe`                                        |
| `winlogon.exe`     | `winlogin.exe`                                       |

At first glance, these names appear legitimate, but careful inspection reveals subtle differences.

---

## Unusual File Locations

Even if the process name is correct, the file location may reveal malicious activity.

### Legitimate Location

```text id="gq7ka2"
C:\Windows\System32\svchost.exe
```

### Suspicious Location

```text id="4j2m1h"
C:\Users\John\AppData\Roaming\svchost.exe
```

Legitimate Windows system processes are expected to reside in trusted system directories. Finding them in user profile folders, temporary directories, or the Downloads folder is highly suspicious.

---

## Process Injection

Some malware injects malicious code into legitimate Windows processes, allowing attackers to hide their activity while using trusted processes such as:

* explorer.exe
* svchost.exe
* lsass.exe

Process injection can make malware more difficult to detect because the malicious code runs inside a legitimate process.

---

## Parent-Child Process Abuse

SOC analysts also examine **parent-child process relationships**.

For example:

Normal behavior:

```text id="gqgwxz"
explorer.exe
    └── notepad.exe
```

Suspicious behavior:

```text id="4d25fk"
winword.exe
    └── powershell.exe
        └── cmd.exe
```

A Microsoft Word document launching PowerShell and Command Prompt may indicate a malicious Office macro or other malware.

---

# Best Practices for Investigating Suspicious Processes

When investigating a suspicious process, SOC analysts should follow a structured approach rather than immediately assuming it is malicious.

Recommended best practices include:

* Verify the process name for spelling variations.
* Check the full file path.
* Confirm whether the executable is digitally signed.
* Review the Process ID (PID) and parent process.
* Identify which user started the process.
* Check the process creation time.
* Examine CPU, memory, and network activity.
* Look for unusual child processes.
* Review command-line arguments.
* Calculate and verify the file hash (such as SHA-256).
* Search for known indicators of compromise (IOCs).
* Correlate process activity with Windows Event Logs, endpoint telemetry, firewall logs, DNS logs, and SIEM alerts.
* If necessary, analyze the executable in an isolated sandbox.
* Avoid terminating critical system processes without understanding their role and the potential impact.

---

# Why Understanding Windows Processes and Services is Important in Cybersecurity

Processes and services provide valuable evidence during security investigations.

SOC analysts monitor them to:

* Detect malware execution.
* Identify persistence mechanisms.
* Investigate ransomware activity.
* Detect credential theft attempts.
* Identify unauthorized remote access tools.
* Monitor suspicious PowerShell or command-line activity.
* Investigate process injection.
* Correlate endpoint activity with SIEM alerts.
* Support incident response and digital forensic investigations.

### Example

A SIEM generates an alert indicating that **powershell.exe** established a connection to an unfamiliar external IP address.

During the investigation, the SOC analyst discovers:

* The parent process is **winword.exe**.
* The PowerShell command is heavily obfuscated.
* The executable was launched immediately after a user opened an email attachment.
* The process downloaded an additional executable into the **AppData** directory.

These findings strongly suggest a phishing attack that executed malicious PowerShell commands. The analyst can isolate the endpoint, collect evidence, and begin containment and remediation.

---

# Key Takeaways

* A **process** is a running instance of a program or application.
* A **Windows Service** is a background process that performs system tasks without user interaction.
* Important Windows processes such as **lsass.exe**, **services.exe**, **svchost.exe**, **explorer.exe**, and **winlogon.exe** are essential to the operating system and are frequently referenced during security investigations.
* Attackers often disguise malware using fake process names, unusual file locations, process injection, and suspicious parent-child process relationships.
* Investigating a process requires examining its name, file path, digital signature, parent process, command-line arguments, network activity, and related security logs.
* Understanding Windows processes and services is essential for SOC analysts because they provide critical evidence for malware analysis, threat hunting, incident response, and digital forensics.
