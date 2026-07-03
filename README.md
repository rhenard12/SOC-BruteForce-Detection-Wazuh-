# 🛡️ Windows Server 2022 + Wazuh SIEM: Failed Logon Detection Lab

## 📌 Project Overview

This project demonstrates how to detect and investigate failed Windows authentication attempts using **Wazuh SIEM** in a home lab environment.

The lab integrates a Windows Server 2022 Domain Controller with a Wazuh Manager running on Ubuntu and uses Kali Linux to validate connectivity. Failed logon attempts are generated and analyzed through Wazuh Threat Hunting.

---

## 🏗️ Lab Environment

| Component | Technology |
|-----------|------------|
| SIEM | Wazuh 4.14.3 |
| Operating System | Windows Server 2025 Standard Evaluation |
| Linux | Ubuntu Server |
| Attacker/Test Machine | Kali Linux 2025.4 |
| Virtualization | Oracle VirtualBox |
| Directory Service | Active Directory Domain Services |

---

## 🎯 Objectives

- Deploy Windows Server 2022
- Configure Active Directory
- Create a test user
- Verify network connectivity
- Enable Remote Desktop
- Generate failed Windows logon events
- Detect authentication failures using Wazuh
- Investigate security events using Threat Hunting

---

## 🔧 Lab Configuration

### Windows Server

- Hostname: WIN-39RFRQKG3AT
- IP Address: 10.0.0.4
- Wazuh Agent Version: 4.14.3
- Agent ID: 002

### Test User

Username:

```
labuser
```

Password:

```
Password
```

---

## 📝 Steps Performed

### 1. Created Active Directory Test User

Created the account:

```
labuser
```

using **Active Directory Users and Computers**.

---

### 2. Enabled Remote Desktop

Configured Windows Server to allow Remote Desktop connections.

---

### 3. Verified Network Connectivity

From Kali Linux:

```bash
ping 10.0.0.4
```

Result:

- Successful replies
- 0% packet loss

---

### 4. Verified RDP Port

```bash
nmap -Pn -p 3389 10.0.0.4
```

Result:

```
3389/tcp open ms-wbt-server
```

---

### 5. Generated Failed Logons

Multiple failed login attempts were intentionally performed using:

```
labuser
```

to generate Windows Security Event ID **4625**.

---

### 6. Investigated in Wazuh

Opened:

```
Threat Hunting
```

Search query:

```
4625
```

Detected:

- Failed Authentication Events
- Rule ID 60122
- Rule Level 5

---

## 🔍 Findings

Detected Events:

- Authentication Failure
- Failed Windows Logon
- Target User: labuser
- Windows Security Event 4625

Wazuh successfully detected and indexed all failed authentication attempts.

---

## 🛡️ MITRE ATT&CK Mapping

| Technique | MITRE ID |
|-----------|----------|
| Valid Accounts | T1078 |
| Brute Force | T1110 |
| Initial Access | TA0001 |
| Credential Access | TA0006 |

---

## 📷 Evidence

Included screenshots:

- Active Directory User
- Ping Test
- Nmap RDP Scan
- Wazuh Dashboard
- Threat Hunting Results
- Endpoint Summary
- Event JSON
- Alert Details
- Rule Information

---

## 📁 Repository Structure

```
SOC-BruteForce-Detection-Wazuh/
│
├── README.md
├── Incident_Report.md
├── MITRE_ATT&CK.md
├── Detection_Logic.md
├── Lessons_Learned.md
├── screenshots/
└── architecture/
```

---

## 📚 Skills Demonstrated

- Windows Server Administration
- Active Directory
- Wazuh SIEM
- Security Monitoring
- Threat Hunting
- Windows Event Logs
- Authentication Analysis
- Network Troubleshooting
- Nmap
- Kali Linux
- Incident Investigation

---

## 🎓 Lessons Learned

This project demonstrated how authentication failures are collected from Windows Event Logs, forwarded through the Wazuh Agent, analyzed by the Wazuh Manager, and investigated using Threat Hunting. It also reinforced Active Directory administration, Windows security logging, SIEM analysis, and network troubleshooting within a virtualized home lab environment.

---

## 👨‍💻 Author

**John Leonard Sta Rita**

Cybersecurity Home Lab Project

Windows Server • Active Directory • Wazuh SIEM • Kali Linux • Ubuntu
