# 🔍 Digital Forensics Lab — Semester 6
### B.Tech in Computer Science Engineering (Cybersecurity)

---

![Digital Forensics](https://img.shields.io/badge/Domain-Digital%20Forensics-blue?style=for-the-badge&logo=shield)
![Semester](https://img.shields.io/badge/Semester-6th-orange?style=for-the-badge)
![Experiments](https://img.shields.io/badge/Experiments-10-green?style=for-the-badge)
![Language](https://img.shields.io/badge/Tools-Kali%20Linux%20%7C%20Windows-purple?style=for-the-badge&logo=linux)

---

## 📋 Overview

This repository contains the lab outputs, reports, and documentation for the **Digital Forensics** course undertaken in **Semester 6** of B.Tech CSE (Cybersecurity). The experiments cover the complete forensics lifecycle — from evidence acquisition and memory analysis to mobile forensics and incident reconstruction — using industry-standard tools.

> **Course:** Digital Forensics Lab (COM-6xx)
> **Program:** B.Tech CSE — Cybersecurity Specialization
> **Semester:** 6th Semester

---

## 📁 Repository Structure

```
digital-forensics-lab/
│
├── Experiment-01_Disk-Imaging/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-02_File-Recovery/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-03_RAM-Analysis/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-04_System-Timeline/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-05_Metadata-Extraction/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-06_Email-Forensics/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-07_Browser-Forensics/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-08_Android-Forensics/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-09_Hash-Integrity/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-10_Incident-Reconstruction/
│   ├── output/
│   ├── screenshots/
│   └── report.md
│
└── README.md
```

---

## 🧪 List of Experiments

---

### Experiment 1 — Forensic Disk Imaging & Integrity Verification

**Tools:** FTK Imager / Guymager · sha256sum

**Objective:**
Acquire a forensically sound image of a storage device using imaging tools and verify the integrity of the captured image using SHA-256 hashing.

**Key Concepts:**
- Forensic disk imaging (bit-for-bit copy)
- Write-blocking to preserve evidence integrity
- SHA-256 hash generation and comparison between source and image
- Chain of custody in digital evidence handling

**Outcome:**
Successfully created a forensic disk image and confirmed data integrity by comparing SHA-256 hash values of the original storage device and its image copy.

---

### Experiment 2 — Deleted File Recovery & Metadata Analysis

**Tools:** Autopsy · Sleuth Kit (TSK)

**Objective:**
Recover deleted files from a disk image and analyze file metadata to extract digital evidence.

**Key Concepts:**
- File system internals and inode analysis
- Deleted file carving and recovery
- Metadata examination — timestamps (MAC: Modified, Accessed, Created), file ownership, and access patterns
- Evidence correlation using Autopsy's GUI pipeline

**Outcome:**
Successfully recovered deleted files and extracted forensically relevant metadata to reconstruct user activity on the disk image.

---

### Experiment 3 — RAM Capture & Volatile Memory Analysis

**Tools:** DumpIt · Volatility Framework

**Objective:**
Capture volatile memory from a live system and analyze the memory image to extract process, network, and malicious activity data.

**Key Concepts:**
- Volatile memory acquisition without altering system state
- Process enumeration from RAM (`pslist`, `pstree`, `cmdline`)
- Active network connections from memory (`netscan`, `netstat`)
- Detection of hidden or injected malicious processes
- Memory artifacts: registry hives, browser sessions, credentials

**Outcome:**
Captured a RAM dump from a live Windows system and used Volatility plugins to enumerate running processes, open network connections, and identify anomalous hidden activities.

---

### Experiment 4 — System Timeline Generation

**Tools:** Plaso (log2timeline) · Autopsy · Timeline Explorer

**Objective:**
Generate a comprehensive system event timeline from file system metadata to reconstruct user and system behavior.

**Key Concepts:**
- Super-timeline creation from multiple forensic artifacts
- MACB (Modified, Accessed, Changed, Born) timestamps
- Identification of anomalous or suspicious event sequences
- Correlation of file system, registry, and log events

**Outcome:**
Produced a detailed chronological timeline of system activity that allowed identification of anomalous user behavior patterns and potential indicators of compromise.

---

### Experiment 5 — Metadata Extraction from Media & Documents

**Tools:** ExifTool · PDFinfo · Strings

**Objective:**
Extract and analyze hidden metadata embedded within image files and PDF documents to support digital investigations.

**Key Concepts:**
- EXIF metadata: camera model, GPS coordinates, timestamps, author
- Document metadata: PDF creator, modification history, software used
- Geolocation extraction from media files
- Anti-forensic awareness: metadata stripping techniques

**Outcome:**
Extracted rich metadata from sample media files and documents, including GPS location data, original authorship information, and document creation timestamps that could serve as digital evidence.

---

### Experiment 6 — Email Header & PGP Message Investigation

**Tools:** Thunderbird · Gpg4win · MX Toolbox

**Objective:**
Investigate email headers to trace sender origin and verify authenticity and integrity of PGP-signed and encrypted messages.

**Key Concepts:**
- Email header anatomy: `Received`, `X-Originating-IP`, `Message-ID`, `DKIM`, `SPF`
- IP tracing and relay server identification
- PGP/GPG digital signatures — verification of message authenticity
- Detecting email spoofing and header forgery

**Outcome:**
Successfully traced email origin through relay server hops, identified originating IP addresses, and verified PGP-signed message integrity using GPG key verification.

---

### Experiment 7 — Browser Artifact & History Analysis

**Tools:** Browser History Examiner · Nirsoft BrowsingHistoryView · SQLite Browser

**Objective:**
Recover and analyze web browsing artifacts — visited URLs, cached content, and cookies — to understand user online behavior and potential compromise vectors.

**Key Concepts:**
- Browser artifact locations (Chrome, Firefox, Edge SQLite databases)
- URL visit history reconstruction with timestamps
- Cookie analysis for session tokens and tracking data
- Cache analysis for previously accessed web content
- Identifying insider threat and exfiltration indicators

**Outcome:**
Extracted and analyzed browser history, cookies, and cached data from a forensic image to reconstruct the user's online activity and identify suspicious browsing patterns.

---

### Experiment 8 — Android Device Forensics

**Tools:** Andriller · Autopsy · ADB (Android Debug Bridge)

**Objective:**
Forensically analyze an Android device image to extract call logs, SMS messages, application data, and stored credentials.

**Key Concepts:**
- Android file system structure (`/data/data/`, `/sdcard/`)
- APK and SQLite database parsing per application
- SMS, MMS, and call log extraction
- App data artifacts: WhatsApp, Instagram, browser history
- Credential extraction from stored application databases

**Outcome:**
Successfully parsed an Android device image to recover SMS messages, call logs, application-specific user data, and stored credentials relevant to a mobile forensics investigation scenario.

---

### Experiment 9 — Hash-Based File Integrity Verification

**Tools:** sha256sum · md5deep / hashdeep · md5sum

**Objective:**
Generate and compare cryptographic hashes of files to verify data integrity and identify tampered or unauthorized file modifications.

**Key Concepts:**
- MD5, SHA-256, SHA-512 hash generation and comparison
- Recursive directory hashing with `hashdeep`
- Known-good hash baseline creation
- Tamper detection through hash mismatch identification
- Application in malware detection and evidence validation

**Outcome:**
Built a hash baseline of a file set, introduced controlled modifications, and successfully detected all tampered files through hash comparison — demonstrating cryptographic integrity verification in a forensic context.

---

### Experiment 10 — Log Correlation & Incident Reconstruction

**Tools:** Timesketch · Elastic Stack (optional) · Plaso

**Objective:**
Aggregate and correlate system and network logs from multiple sources to simulate incident reconstruction and produce a structured investigative report.

**Key Concepts:**
- Multi-source log ingestion (syslog, Windows Event Logs, network logs)
- Timesketch timeline creation and collaborative analysis
- Attack pattern identification through log correlation
- Building a chronological incident narrative
- Investigative report writing with evidence documentation

**Outcome:**
Correlated logs from system and network sources within Timesketch to reconstruct a simulated security incident timeline, identifying attacker actions from initial access to exfiltration and documenting findings in a formal report.

---

## 🛠️ Tools & Technologies Summary

| Category | Tools Used |
|---|---|
| **Disk Imaging** | FTK Imager, Guymager |
| **File Recovery** | Autopsy, Sleuth Kit (TSK) |
| **Memory Forensics** | DumpIt, Volatility Framework |
| **Timeline Analysis** | Plaso (log2timeline), Autopsy, Timeline Explorer |
| **Metadata Extraction** | ExifTool, PDFinfo |
| **Email Forensics** | Thunderbird, Gpg4win, MX Toolbox |
| **Browser Forensics** | Browser History Examiner, Nirsoft Tools, SQLite Browser |
| **Mobile Forensics** | Andriller, Autopsy, ADB |
| **Integrity Verification** | sha256sum, md5deep, hashdeep |
| **Incident Reconstruction** | Timesketch, Plaso, Elastic Stack |

---

## 💻 Environment

| Component | Details |
|---|---|
| **OS (Primary)** | Kali Linux / Ubuntu |
| **OS (Secondary)** | Windows 10/11 (for FTK, Thunderbird, Browser tools) |
| **Virtualization** | VMware Workstation / VirtualBox |
| **Architecture** | x86-64 |

---

## 📌 Key Takeaways

- Developed hands-on proficiency with industry-standard forensic tools used in real investigations.
- Understood the **forensic evidence lifecycle** — acquisition → preservation → analysis → reporting.
- Applied **chain-of-custody** principles and integrity verification across all experiments.
- Gained practical exposure to **disk, memory, network, email, browser, and mobile forensics** domains.
- Built skills directly applicable to **DFIR (Digital Forensics & Incident Response)** roles.

---

## 👤 Author

**Aneesh Sangran**
B.Tech CSE (Cybersecurity) — 6th Semester

[![GitHub](https://img.shields.io/badge/GitHub-aneeshsangran84-black?style=flat-square&logo=github)](https://github.com/aneeshsangran84)
[![YouTube](https://img.shields.io/badge/YouTube-CWE%20%7C%20Cyber%20White%20Elephant-red?style=flat-square&logo=youtube)](https://youtube.com/@CyberWhiteElephant)

---

> ⚠️ **Disclaimer:** All experiments were performed in controlled lab environments on legally owned or provided forensic images and devices. This repository is intended strictly for educational purposes.
