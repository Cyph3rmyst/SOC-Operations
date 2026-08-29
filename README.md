# 🛡️ SOC Operations & Cyber Defense Portfolio

> **Core Mission:** Combining investigative curiosity with an attacker mindset to answer one fundamental question: *"Is this activity normal, or is this an attack?"*

---

## 🎯 Career Progression Roadmap

The objective of this repository is to systematically advance defensive security skills through progressive stages:

```text
📌 SOC L1 ➡️ 📌 SOC L2 ➡️ 📌 Malware Analysis & Reverse Engineering ➡️ 📌 Digital Forensics
```

### 📁 Repository Structure

Each project folder follows a standardized documentation and evidence structure:

```text
📁 project-name/
├── 📄 case-<date-of-analysis>.md
├── 🖼️ case-evidence.png
└── 🗂️ <case_artifact>  // e.g., .pcap, .log samples
```

*Note: Every project entry includes comprehensive reporting and in-depth research.*

---

## 📚 1. Structured Learning Platforms

Resources are intentionally curated to maximize skill acquisition with zero waste:

* **TryHackMe** — Foundational entry path covering core SOC L1 & SOC L2 competencies.
* **LetsDefend** — Dedicated SOC analyst training structured from core courses to hands-on challenges and live practice.
* **CyberDefenders** — Advanced digital forensics (network, memory, disk), malware analysis, and threat intelligence. *(Includes free Blueyard Labs access).*
* **Blue Team Labs Online (BTLO)** — Practical labs focusing on digital forensics, reverse engineering, threat hunting, and SOC operations.
* **KC7** — Gamified learning tracks for real-world SOC L1 & SOC L2 scenarios.
* **Boss of the SOC (BOTS)** — Jeopardy-style CTF simulations reflecting realistic incidents in enterprise environments.

---

## 📖 2. Recommended Reading & Mental Models

Books provide historical context, foundational patterns, and the critical mental models required for modern defense.

### 1. *Practical Malware Analysis*

**Author:** Michael Sikorski

**Focus Area:** Zero-to-advanced analysis, progressing into C-based reverse engineering.

### 2. *Automate the Boring Stuff with Python*

**Author:** Al Sweigart

**Focus Area:** Automating repetitive system administration and filesystem tasks.

### 3. *UNIX and Linux System Administration Handbook*

**Author:** Evi Nemeth et al.

**Focus Area:** Upgrading core Linux competence to advanced sysadmin levels.

### 4. *Blue Team Field Manual (BTFM)*

**Author:** Alan White et al.

**Focus Area:** Quick-reference command guide for incident response and defensive operations.

### 5. *Applied Network Security Monitoring*

**Author:** Chris Sanders

**Focus Area:** Essential network traffic analysis and monitoring principles.

### 6. *The C Programming Language (ANSI)*

**Author:** Dennis Ritchie

**Focus Area:** Advanced understanding required for malware analysis, reverse engineering, and exploit research.

---

## 🛠️ 3. Projects & Lab Architecture

Projects provide a structured framework where all practical work from learning platforms is applied and documented.

### Lab Environments

* **SIEM & Analysis Lab**

  * **Host OS:** Ubuntu Linux (Server security & orchestration)
  * **Victim/Target:** Windows 10
  * **Attacker Simulation:** Kali Linux

* **Malware Analysis Lab**

  * **REMnux:** Dedicated Linux distribution for malware analysis.
  * **FLARE VM:** Open-source Windows 10 distribution tailored for malware and reverse engineering.

---

### Project Modules

* 🏷️ **01. Home Lab Setup** — Configuration, architecture, and network topology.

* 🏷️ **02. SIEM Setup & Configurations** — Deployment, rule tuning, and log ingestion.

* 🏷️ **03. Traffic Analysis** — Deep-dive packet captures (`.pcap`) and network anomaly detection.

* 🏷️ **04. End-to-End Investigations** — Comprehensive workflows combining all lab disciplines:

  * Alert Triage & Reporting
  * Malware Analysis & Reverse Eng.
  * Alert Escalation
  * Digital Forensics (DFIR)
  * Phishing & Log Analysis
  * Threat Intelligence Integration
  * Threat Hunting

* 🏷️ **05. Log Analysis** — Windows Event Logs, Sysmon, and Linux authentication logs.

* 🏷️ **06. Vulnerability Analysis** — Identification, scanning, and remediation tracking.

* 🏷️ **07. Malware Analysis** — Dissecting real-world samples (e.g., Agent Tesla).

* 🏷️ **08. Threat Intelligence Reports** — Researching active threat groups (e.g., APT38).

* 🏷️ **09. Incident Response Playbooks** — Standardized response workflows for containment and eradication.

* 🏷️ **10. Phishing Analysis** — Email header inspection, URL detonation, and payload extraction.

* 🏷️ **11. Defensive CTFs** — Documented challenges from platforms like HackTheBox (e.g., Holmes CTF).
