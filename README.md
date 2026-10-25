# Enterprise NetDevOps Automation & Secure Triage Framework

An advanced, multi-vendor (Cisco/Aruba) network automation pipeline built with Python, Netmiko, and SNMPv3. It features intelligent alert mitigation, automated layer-2 threat quarantine, configuration drift management, and end-to-end encrypted mobile incident response.

## 🚀 Core Architecture

### 1. Intelligent Alerting & Port Diagnostics
* **Targeted Monitoring:** Scans critical uplinks and designated ports for CRC and Input errors at highly flexible, user-defined intervals (ranging from seconds to hours).
* **Flood Mitigation:** Implements an alert throttling architecture. Critical port failures trigger instant encrypted alerts, while secondary port telemetry is quietly piped to a local home directory log file to eliminate notification fatigue.

### 2. Automated Layer-2 Duplicate IP Quarantine
* **Real-time Traps:** Leverages secure SNMPv3 traps and direct Netmiko execution to immediately identify duplicate IP conflicts across the network infrastructure.
* **Failsafe Isolation:** Automatically reconfigures the rogue port into a isolated **Quarantine VLAN 999**.
* **Safety Overrides:** Built-in safeguards ensure critical infrastructure links and trunk ports are completely exempt from automated lockdown logic.

### 3. Multi-Vendor Configuration Drift & Compliance
* **Baseline Auditing:** Periodically fetches running configurations from Cisco and Aruba devices, running local diffs against a secure, master backup directory.
* **Audit Trail Generation:** Detects unauthorized modifications and outputs encrypted tamper alerts containing **precise code deltas, operator user details, and exact execution timestamps**.

### 4. End-to-End Encrypted Mobile Decryption (Termux Integration)
* **Secure Payloads:** All diagnostic and drift alerts are encrypted prior to being transmitted over Gmail and Telegram Bot APIs.
* **On-Device Triage:** Using an Android device running Termux and the `termux-api` package, administrators can securely copy an incoming alert. The local Python script auto-intercepts the clipboard data, performs localized decryption, and instantly formats the network logs inside the mobile terminal.

## 🛠️ Tech Stack
* **Languages & Automation:** Python, Netmiko, SNMPv3 (PySNMP)
* **Infrastructure Supported:** Cisco IOS/IOS-XE, ArubaOS/ArubaOS-CX
* **Security & Cryptography:** Python `cryptography` (AES-256)
* **Mobile Triage:** Termux, Termux-API
* **Notification Layer:** Telegram Bot API, SMTP
