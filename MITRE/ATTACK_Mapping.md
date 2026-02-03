# MITRE ATT&CK Mapping

This document maps the simulated attacks in this project to the **MITRE ATT&CK Framework**, showing how real-world adversary techniques were observed, detected, and mitigated.

---

## 🔴 RDP Brute Force Attack Mapping

### 🧭 Attack Flow Summary
An external attacker scanned exposed services, performed brute force against RDP, and successfully authenticated using weak credentials.

---

### 🟡 MITRE Technique Mapping

| Tactic | Technique | Sub-Technique | ID |
|------|---------|--------------|----|
| Reconnaissance | Network Service Scanning | N/A | T1046 |
| Credential Access | Brute Force | Password Guessing | T1110.001 |
| Initial Access | Remote Services | RDP | T1021.001 |
| Lateral Movement | Remote Services | RDP | T1021.001 |

---

### 🔍 Phase-wise Breakdown

#### 1️⃣ Reconnaissance – Network Scanning
- **Technique ID:** T1046
- **Description:** Attacker used Nmap to identify exposed RDP services.
- **Tool Used:** Nmap
- **Evidence:**
  - Azure Firewall logs
  - Network flow logs showing multiple port probes
- **Detection Source:** Azure Firewall / Sentinel

---

#### 2️⃣ Credential Access – Brute Force
- **Technique ID:** T1110.001
- **Description:** Multiple authentication attempts against RDP service.
- **Tool Used:** Hydra
- **Evidence:**
  - Windows Security Event ID **4625**
  - High-frequency failed login attempts
- **Detection Source:** Windows Security Logs → Sentinel

---

#### 3️⃣ Initial Access – Remote Services
- **Technique ID:** T1021.001
- **Description:** Successful RDP login using compromised credentials.
- **Evidence:**
  - Windows Security Event ID **4624**
  - LogonType **10 (RemoteInteractive)**
- **Detection Source:** VM Security Logs → Sentinel

---

#### 4️⃣ Lateral Movement (Potential)
- **Technique ID:** T1021.001
- **Description:** Attacker could use RDP access to move laterally inside the network.
- **Evidence (Simulated):**
  - RDP logins to internal hosts
- **Detection Source:** Sentinel Correlation Rules

---

## 🟢 Defensive Controls Mapped

| Control | Mitigated Technique |
|------|------------------|
| Account Lockout Policy | T1110 |
| MFA Enforcement | T1021 |
| Firewall IP Blocking | T1046 |
| Sentinel Analytics Rules | T1110, T1021 |

---

## 🎯 Why This Mapping Matters
- Aligns detections with **industry-standard framework**
- Helps SOC teams prioritize alerts
- Demonstrates real **threat-hunting maturity**
- Interviewers instantly know you understand **attacker behavior**

---

## 📌 References
- MITRE ATT&CK: Enterprise Matrix

