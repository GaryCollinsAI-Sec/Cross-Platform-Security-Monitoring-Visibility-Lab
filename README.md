# Cross-Platform Security Monitoring & Visibility Lab (Wazuh SIEM/XDR)

## 📌 Overview
This lab demonstrates the deployment and configuration of a centralized security monitoring solution using **Wazuh (SIEM/XDR)**. The project focuses on establishing comprehensive visibility across a hybrid environment consisting of **Windows 10** and **Ubuntu Linux** endpoints. By integrating these systems, I created a unified telemetry pipeline capable of real-time threat detection, file integrity monitoring, and vulnerability assessment.

---

## 🛠️ Technical Stack
*   **SIEM/XDR Manager:** Wazuh 4.x (OVA Deployment)
*   **Endpoints:** Windows 10 Enterprise, Ubuntu 22.04 LTS
*   **Virtualization:** Oracle VirtualBox
*   **Automation/Scripting:** PowerShell, Bash
*   **Network:** Bridged Adapter configuration for cross-host communication

---

## 🏗️ Architecture
The environment was architected to simulate a small enterprise network:
1.  **Wazuh Manager:** Serves as the central brain for log collection, analysis, and alerting.
2.  **Windows Agent:** Monitored via a PowerShell-provisioned agent to capture Event Logs, Sysmon data, and registry changes.
3.  **Ubuntu Agent:** Monitored via a CLI-provisioned agent to track authentication logs (`auth.log`), system changes, and rootkit activity.

---

## 🚀 Implementation Highlights

### 1. Endpoint Provisioning
To ensure a secure and efficient rollout, agents were deployed using platform-specific automation:

*   **Windows 10:** Utilized an elevated **PowerShell** script to download the MSI package, assign the manager IP, and initiate the registration service.
*   **Ubuntu:** Deployed via **Bash** using the official Wazuh repository, ensuring the agent was correctly linked to the manager's registration server.

### 2. Log Analysis & Threat Detection
Configured the manager to ingest and parse logs for specific security events, including:
*   Failed authentication attempts (Brute-force detection).
*   Account creations and privilege escalations.
*   System service modifications.

### 3. File Integrity Monitoring (FIM)
I tuned the `ossec.conf` file on both endpoints to monitor sensitive directories:
*   **Windows:** Monitored `C:\Windows\System32\drivers\etc\hosts` for unauthorized redirection attempts.
*   **Linux:** Monitored `/etc/shadow` and `/etc/passwd` to detect unauthorized user modifications.

### 4. Vulnerability Management & Compliance
Enabled the **Security Configuration Assessment (SCA)** module to:
*   Identify unpatched software and high-severity CVEs.
*   Audit systems against CIS (Center for Internet Security) benchmarks.
*   Map findings to the **MITRE ATT&CK** framework for better context during incident response.

---

## 📊 Key Results
*   **Unified Visibility:** Successfully consolidated disparate logs from Linux and Windows into a single "Pane of Glass."
*   **Active Alerting:** Validated that the manager triggers high-severity alerts within seconds of a detected threat (e.g., unauthorized file change).
*   **Hardening Baseline:** Used SCA reports to identify and remediate three critical misconfigurations on the Ubuntu server.

---

## 📂 Repository Structure
*   `/configs`: Contains snippets of customized `ossec.conf` settings.
*   `/scripts`: Includes the PowerShell and Bash commands used for agent deployment.
*   `/docs`: Screenshots of the Wazuh Dashboard and sample alerts.

---

## 🔗 Connect with Me
**Gary Collins**  
[LinkedIn](https://linkedin.com/in/garyjosephcollins) | IT Support & Security Specialist
