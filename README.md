# Enterprise Wazuh SOC Portfolio

Hands-on Security Operations portfolio demonstrating SIEM deployment, Windows endpoint monitoring, threat detection, detection engineering, vulnerability management, threat intelligence, and incident investigation using Wazuh.

The lab environment was built around a Wazuh SIEM server and a monitored Windows 11 endpoint with Sysmon and Microsoft Defender telemetry. The projects progress from infrastructure deployment and log collection to custom detection engineering and end-to-end SOC investigation.

---

## Lab Architecture

```text
Windows 11 VM
├── Wazuh Agent
├── Sysmon
├── Microsoft Defender
└── Windows Security Logs
        │
        │ Security Telemetry
        ▼
Ubuntu Wazuh Server
├── Wazuh Manager
├── Wazuh Indexer
└── Wazuh Dashboard
        │
        ▼
Detection & Investigation
├── Authentication Monitoring
├── File Integrity Monitoring
├── Malware Detection
├── Vulnerability Detection
├── Custom Detection Rules
├── Network Monitoring
├── IOC Hunting
└── Incident Investigation
```

---

## Projects

### 01 – Wazuh Infrastructure & Agent Deployment

Deployed the Wazuh SIEM environment and connected a Windows 11 endpoint for centralized security monitoring.

**Key skills:** Wazuh deployment, SIEM architecture, agent management, endpoint onboarding, Linux administration

---

### 02 – Windows & Sysmon Endpoint Monitoring

Integrated Windows Sysmon telemetry with Wazuh and investigated process creation and command-line activity.

**Key telemetry:** Sysmon Event ID 1

**Key skills:** Sysmon, Windows telemetry, process analysis, command-line investigation, endpoint monitoring

---

### 03 – Authentication Attack Detection

Generated controlled failed-login activity and investigated authentication events through Wazuh.

**Detection evidence:**

- Windows Event ID 4625 – Failed Logon
- Wazuh Rule 60204 – Multiple Login Failures
- 9 correlated failed-login events observed during testing

**Key skills:** Authentication monitoring, brute-force detection, event correlation, alert triage

---

### 04 – File Integrity Monitoring

Configured Wazuh File Integrity Monitoring and validated detection of file creation, modification, and deletion.

**Detection evidence:**

- Rule 554 – File added
- Rule 550 – File integrity checksum changed
- Rule 553 – File deleted

**Key skills:** FIM, integrity monitoring, endpoint change detection, security-event investigation

---

### 05 – Malware Detection & Incident Investigation

Integrated Microsoft Defender telemetry with Wazuh and generated a controlled EICAR anti-malware detection.

**Detection evidence:**

- Microsoft Defender Event ID 1116
- Wazuh Rule 62123
- EICAR anti-malware test artifact

The alert was investigated through both endpoint and centralized SIEM telemetry.

**Key skills:** Malware triage, Microsoft Defender, SIEM correlation, endpoint investigation

---

### 06 – Vulnerability Detection & Remediation Assessment

Used Wazuh Vulnerability Detection to identify and validate vulnerabilities affecting VMware Tools on the Windows 11 VM.

**High-severity findings investigated:**

- CVE-2025-22230
- CVE-2025-41239
- CVE-2025-41246

The affected VMware Tools version `12.4.5` was independently verified and remediation requirements were documented.

**Key skills:** CVE investigation, CVSS analysis, vulnerability validation, risk prioritization, remediation assessment

---

### 07 – Custom Detection Rules

Developed custom Wazuh detection rules using Sysmon process telemetry.

**Custom detections:**

| Rule | Level | Detection |
|---|---:|---|
| 100100 | 8 | Controlled PowerShell activity |
| 100101 | 10 | Encoded PowerShell execution |

The encoded PowerShell detection was mapped to:

**MITRE ATT&CK T1059.001 – PowerShell**

**Key skills:** Detection engineering, custom Wazuh rules, regex matching, Sysmon, PowerShell monitoring, MITRE ATT&CK

---

### 08 – Network Threat Detection

Enabled Sysmon network telemetry and integrated network connection events with Wazuh.

A custom Wazuh rule was created to alert on Sysmon Event ID 3 telemetry.

**Detection evidence:**

- Sysmon Event ID 3 – Network Connection
- Wazuh Rule 100102
- Controlled Nmap reconnaissance performed within the lab

Network events were investigated using source/destination IPs, ports, protocols, and process context.

**Key skills:** Network monitoring, Sysmon network telemetry, Nmap, Wazuh threat hunting, network-event analysis

---

### 09 – Threat Intelligence & IOC Investigation

Performed threat-intelligence enrichment and IOC hunting using VirusTotal and Wazuh.

Two IOC types were investigated:

**Domain IOC**

```text
testsafebrowsing.appspot.com
```

VirusTotal: 2 vendor detections  
Wazuh: 0 internal matches

**SHA-256 IOC**

```text
275a021bbfb6489e54d471899f7db9d1663fc695ec2fe2a2c4538aabf651fd0f
```

VirusTotal: 65 vendor detections  
Wazuh: 0 internal matches

The investigation concluded that external reputation signals existed but no evidence of internal exposure was identified in the searched Wazuh telemetry.

**Key skills:** Threat intelligence, IOC enrichment, hash analysis, domain reputation, SIEM hunting, analyst disposition

---

### 10 – Incident Investigation & SOC Reporting

Conducted an end-to-end SOC investigation after custom Rule 100101 detected encoded PowerShell execution.

**Investigation workflow:**

```text
Encoded PowerShell
        ↓
Sysmon Event ID 1
        ↓
Wazuh Rule 100101
        ↓
Alert Triage
        ↓
Process & User Investigation
        ↓
Network Hunt
        ↓
MITRE ATT&CK Mapping
        ↓
Incident Assessment
        ↓
Closure
```

**Initial severity:** High  
**MITRE ATT&CK:** T1059.001 – PowerShell  
**Network follow-on:** None identified  
**Evidence of compromise:** None identified  
**Detection:** True Positive  
**Activity:** Authorized / Benign Lab Test  
**Final disposition:** Closed

**Key skills:** Alert triage, incident investigation, timeline development, severity assessment, MITRE ATT&CK, SOC reporting

---

## Detection Coverage

| Security Activity | Telemetry / Detection |
|---|---|
| Process Creation | Sysmon Event ID 1 |
| Failed Authentication | Windows Event ID 4625 |
| Multiple Login Failures | Wazuh Rule 60204 |
| File Creation | Wazuh Rule 554 |
| File Modification | Wazuh Rule 550 |
| File Deletion | Wazuh Rule 553 |
| Defender Malware Detection | Event ID 1116 / Rule 62123 |
| Vulnerable Software | Wazuh Vulnerability Detection |
| Custom PowerShell Detection | Rule 100100 |
| Encoded PowerShell | Rule 100101 |
| Network Connections | Sysmon Event ID 3 / Rule 100102 |
| IOC Investigation | VirusTotal + Wazuh Threat Hunting |

---

## MITRE ATT&CK Coverage

| Technique | ID | Lab |
|---|---|---|
| PowerShell | T1059.001 | Custom Detection / Incident Investigation |

MITRE ATT&CK mappings are included only where validated against the activity demonstrated in the lab.

---

## Technologies

### SIEM & Security

- Wazuh
- Microsoft Defender
- Sysmon
- Windows Security Event Logs
- VirusTotal
- MITRE ATT&CK

### Operating Systems

- Windows 11
- Ubuntu Linux

### Networking & Investigation

- Nmap
- TCP/IP
- DNS
- Windows network telemetry

### Administration & Scripting

- PowerShell
- Bash
- Git
- GitHub

---

## SOC Skills Demonstrated

- SIEM deployment and administration
- Endpoint security monitoring
- Windows event-log analysis
- Sysmon telemetry analysis
- Alert triage
- Authentication attack detection
- File Integrity Monitoring
- Malware investigation
- Vulnerability management
- CVE/CVSS analysis
- Detection engineering
- Custom SIEM rule development
- Network security monitoring
- Threat intelligence enrichment
- IOC hunting
- MITRE ATT&CK mapping
- Incident investigation
- Incident timeline development
- Security-event correlation
- SOC documentation and reporting

---

## Repository Structure

```text
enterprise-wazuh-soc-portfolio/
│
├── README.md
│
├── 01-Wazuh-Infrastructure-and-Agent-Deployment/
├── 02-Windows-and-Sysmon-Endpoint-Monitoring/
├── 03-Authentication-Attack-Detection/
├── 04-File-Integrity-Monitoring/
├── 05-Malware-Detection-and-Incident-Investigation/
├── 06-Vulnerability-Detection-and-Remediation/
├── 07-Custom-Detection-Rules/
├── 08-Network-Threat-Detection/
├── 09-Threat-Intelligence-and-IOC-Investigation/
└── 10-Incident-Investigation-and-SOC-Reporting/
```

Each project contains supporting screenshots and, where applicable, investigation notes, configuration files, custom detection rules, timelines, and SOC-style reports.

---

## Portfolio Outcome

This portfolio demonstrates a progression from deploying a SIEM and collecting endpoint telemetry to developing custom detections and conducting complete SOC investigations.

```text
SIEM Deployment
      ↓
Endpoint Monitoring
      ↓
Threat Detection
      ↓
Alert Triage
      ↓
Vulnerability Assessment
      ↓
Detection Engineering
      ↓
Network Monitoring
      ↓
Threat Intelligence
      ↓
Incident Investigation
      ↓
SOC Reporting
```

All attack simulations and security tests were performed in an isolated lab environment using controlled or safe test activity.
