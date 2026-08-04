# Windows File System Fundamentals

## Definition of a File System

A **file system** is the method an operating system uses to organize, store, retrieve, and manage files and folders on a storage device such as a hard drive, solid-state drive (SSD), or USB flash drive.

Without a file system, a computer would not know where files are stored or how to locate them efficiently.

A file system is responsible for:

* Organizing files and folders.
* Managing file names and locations.
* Controlling file permissions.
* Tracking available storage space.
* Protecting file integrity.
* Storing file metadata, such as creation and modification dates.

Different operating systems use different file systems. For example:

* **Windows** – NTFS, FAT32, exFAT
* **Linux** – ext4, XFS, Btrfs
* **macOS** – APFS

---

# What is NTFS?

**NTFS (New Technology File System)** is the default file system used by modern versions of Microsoft Windows. It was designed to provide better security, reliability, and performance than older file systems such as FAT32.

NTFS supports advanced features that make it suitable for personal computers, enterprise environments, and servers.

### Key Features of NTFS

* File and folder permissions (Access Control Lists - ACLs).
* Support for very large files and partitions.
* File compression.
* File encryption using Encrypting File System (EFS).
* Disk quotas.
* Journaling to help recover from system crashes.
* Detailed file metadata.

Because of these features, NTFS is widely used in digital forensics and cybersecurity investigations.

---

# Important Windows Directories

Windows stores operating system files, applications, and user data in specific directories. Knowing these locations helps SOC analysts identify normal and suspicious activity.

| Directory                       | Purpose                                                                  |
| ------------------------------- | ------------------------------------------------------------------------ |
| `C:\Windows`                    | Contains core Windows operating system files.                            |
| `C:\Windows\System32`           | Stores essential system files, DLLs, drivers, and utilities.             |
| `C:\Program Files`              | Default installation location for 64-bit applications.                   |
| `C:\Program Files (x86)`        | Default installation location for 32-bit applications on 64-bit Windows. |
| `C:\Users`                      | Contains user profiles and personal data.                                |
| `C:\Users\<Username>\Desktop`   | Stores files located on a user's desktop.                                |
| `C:\Users\<Username>\Downloads` | Default folder for downloaded files.                                     |
| `C:\Users\<Username>\Documents` | Stores personal documents.                                               |
| `C:\Users\<Username>\AppData`   | Stores application settings, temporary files, and user-specific data.    |
| `C:\Temp` or `%TEMP%`           | Stores temporary files created by Windows and applications.              |

---

# Important Directories Explained

## C:\Windows

This directory contains the files required for Windows to operate. Unauthorized changes to files in this directory may indicate malware or system compromise.

---

## C:\Windows\System32

One of the most important folders in Windows.

It contains:

* Windows system files.
* Dynamic Link Libraries (DLLs).
* Device drivers.
* Administrative tools.
* Command-line utilities.

Attackers often attempt to disguise malware by placing files in this directory or by using names similar to legitimate Windows files.

---

## C:\Program Files

Most legitimate 64-bit applications install here.

SOC analysts may compare installed applications with authorized software to identify potentially unwanted or malicious programs.

---

## C:\Program Files (x86)

On 64-bit Windows systems, this directory stores 32-bit applications.

---

## C:\Users

Each user account has a separate folder inside this directory containing personal files and settings.

Common subfolders include:

* Desktop
* Documents
* Downloads
* Pictures
* Music
* Videos
* AppData

Many phishing downloads and malware infections begin in the **Downloads** folder.

---

## AppData

The **AppData** folder contains application configuration files and user-specific data.

It includes three subfolders:

* **Roaming**
* **Local**
* **LocalLow**

Because AppData is hidden by default and frequently used by applications, attackers often store malware here to avoid detection.

---

## Temp Folder

Temporary folders store files created during software installation and application execution.

Malware frequently writes files to temporary directories before executing them.

SOC analysts often examine these folders during investigations.

---

# Common File Extensions

A **file extension** identifies the type of file and often indicates which application can open it.

Some file extensions are commonly encountered during cybersecurity investigations.

| Extension | File Type                         | Common Use                                                  |
| --------- | --------------------------------- | ----------------------------------------------------------- |
| `.exe`    | Executable                        | Windows applications and programs.                          |
| `.dll`    | Dynamic Link Library              | Shared program code used by Windows and applications.       |
| `.bat`    | Batch File                        | Executes a series of Windows commands.                      |
| `.cmd`    | Command Script                    | Similar to batch files, used for scripting.                 |
| `.ps1`    | PowerShell Script                 | Automates Windows administration tasks.                     |
| `.vbs`    | VBScript                          | Script used for automation and, sometimes, malware.         |
| `.js`     | JavaScript File                   | May be used by web applications or malicious downloaders.   |
| `.msi`    | Windows Installer Package         | Installs software.                                          |
| `.zip`    | Compressed Archive                | Stores one or more compressed files.                        |
| `.rar`    | Compressed Archive                | Another common compressed file format.                      |
| `.7z`     | Compressed Archive                | High-compression archive format.                            |
| `.pdf`    | Portable Document Format          | Documents commonly used in phishing campaigns.              |
| `.docx`   | Microsoft Word Document           | Office document format.                                     |
| `.xlsx`   | Microsoft Excel Spreadsheet       | Spreadsheet file format.                                    |
| `.pptx`   | Microsoft PowerPoint Presentation | Presentation file format.                                   |
| `.lnk`    | Windows Shortcut                  | Shortcut files that attackers may abuse to execute malware. |

---

# Why File Paths Matter to SOC Analysts

A **file path** specifies the exact location of a file or folder within the file system.

Example:

```text
C:\Users\John\Downloads\invoice.exe
```

File paths provide valuable context during an investigation.

SOC analysts examine file paths to determine:

* Where a suspicious file originated.
* Whether the location is expected or unusual.
* If malware is attempting to hide in system folders.
* Which user downloaded or executed the file.
* Whether persistence mechanisms are involved.

### Example

Consider these two executable files:

```text
C:\Program Files\Microsoft Office\WINWORD.EXE
```

This is a legitimate location for Microsoft Word.

```text
C:\Users\John\AppData\Roaming\WINWORD.EXE
```

Although the filename looks legitimate, the location is unusual and may indicate malware impersonating Microsoft Word.

This demonstrates why analysts always evaluate both the **filename** and the **file path** before reaching a conclusion.

---

# Best Practices When Investigating Suspicious Files

SOC analysts should follow a structured investigation process before determining whether a file is malicious.

Recommended best practices include:

* Verify the file's full path and filename.
* Check the file extension.
* Confirm whether the file is digitally signed.
* Determine when the file was created, modified, or accessed.
* Identify which user downloaded or executed the file.
* Calculate and review the file hash (such as SHA-256).
* Check whether antivirus or endpoint protection has detected the file.
* Review process creation logs and Windows Event Logs.
* Examine any related network connections.
* Analyze the file in a secure sandbox if necessary.
* Never execute a suspicious file on a production system.
* Correlate findings with SIEM, endpoint, DNS, and firewall logs.

---

# Why Understanding the Windows File System is Important in Cybersecurity

Many cyberattacks involve creating, modifying, or executing files on Windows systems.

SOC analysts rely on knowledge of the Windows file system to:

* Investigate malware infections.
* Detect suspicious executables.
* Identify persistence mechanisms.
* Trace phishing downloads.
* Analyze ransomware activity.
* Locate malicious scripts.
* Support digital forensic investigations.
* Correlate file activity with security logs.

### Example

A SIEM generates an alert indicating that a new executable has been launched.

During the investigation, the SOC analyst discovers:

* The file is located in:

```text
C:\Users\Alice\AppData\Local\Temp\update.exe
```

* The file has no valid digital signature.
* It was downloaded from the Internet only a few minutes earlier.
* It immediately contacted an unknown external IP address.

These findings strongly suggest suspicious activity. The analyst can then isolate the affected system, collect additional evidence, and begin the incident response process.

---

# Key Takeaways

* A **file system** organizes and manages files on a storage device.
* **NTFS** is the default Windows file system and provides security, reliability, permissions, and detailed metadata.
* Important Windows directories include **C:\Windows**, **System32**, **Program Files**, **Users**, **AppData**, and **Temp**.
* Understanding common file extensions helps SOC analysts identify executables, scripts, archives, and document files.
* File paths provide critical context during investigations and can reveal whether a file is in a legitimate or suspicious location.
* Following structured investigation practices helps analysts accurately assess suspicious files while preserving evidence and reducing the risk of false conclusions.
