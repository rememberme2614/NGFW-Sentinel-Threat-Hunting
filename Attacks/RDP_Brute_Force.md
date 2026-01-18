# RDP Brute Force Attack – Threat Hunt

## 🎯 Objective
Detect repeated unauthorized RDP authentication attempts against a public Windows VM.

---

## 🖥️ Target
- Windows Server VM
- Port: TCP/3389
- Internet-facing via NAT

---

## ⚔️ Attack Simulation
Multiple RDP login attempts were generated from an external source to simulate a brute-force attack.

---

## 🔍 Detection Sources
- FortiGate Firewall Logs
- FortiGate IPS Logs
- Microsoft Sentinel Alerts

---

## 🛡️ IPS Detection
A custom IPS signature was deployed to detect abnormal RDP connection behavior.

---

## 📊 Observed Indicators
- High frequency of RDP connection attempts
- Same source IP targeting port 3389
- IPS signature triggered

---

## 🚨 Sentinel Alert
Microsoft Sentinel generated an alert correlating:
- Source IP
- Destination VM
- Repeated failed access attempts

---

## 🧠 Analyst Decision
Attack confirmed as **malicious brute-force attempt**.

---

## 🛑 Response Action
- Source IP blocked at FortiGate firewall
- Incident closed after validation

---

## 🧬 MITRE ATT&CK Mapping
| Technique | Description |
|--------|-------------|
| T1110 | Brute Force |
| T1078 | Valid Accounts |

