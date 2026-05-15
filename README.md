# Cross-Platform Security Monitoring Lab (Wazuh SIEM)

## 📌 Overview
This project highlights the deployment of an enterprise-grade **SIEM/XDR** solution using **Wazuh**[cite: 1]. The primary objective was to architect a "Single Pane of Glass" for centralized security monitoring across a hybrid lab environment[cite: 1]. I successfully integrated **Windows 10** and **Ubuntu Linux** endpoints with a **Wazuh OVA Manager**, establishing a robust pipeline for real-time telemetry and log ingestion[cite: 1].

---

## 🛠️ Technical Stack
*   **SIEM Manager:** Wazuh 4.x (OVA Deployment)
*   **Endpoints:** Windows 10 (Workstation) | Ubuntu 22.04 
*   **Virtualization:** Oracle VirtualBox
*   **Administration:** PowerShell (Windows) | Bash/CLI (Linux)
*   **Networking:** Bridged Adapter configuration for cross-segment communication

---

## 🏗️ Lab Architecture
The environment was engineered to simulate a centralized Security Operations Center (SOC) monitoring diverse enterprise assets:
1.  **Wazuh Manager:** Centralized engine responsible for log analysis, alert correlation, and visualization.
2.  **Windows Agent:** Installed on Windows 10 to monitor Event Logs, system integrity, and user activity.
3.  **Ubuntu Agent:** Installed on Linux to monitor authentication logs and system service status.

---

## 🚀 Implementation Steps

### 1. SIEM Infrastructure Deployment
*   Provisioned the **Wazuh OVA** within VirtualBox, ensuring network interfaces were configured for bi-directional communication.
*   Validated the initialization of the Wazuh Indexer and Server components.
*   Verified accessibility of the web dashboard for centralized management.

<img width="1027" height="762" alt="Wazuh Manager Initialization" src="https://github.com/user-attachments/assets/17eb9861-4f85-45e1-b577-0f56b30b13c4" />

---

### 2. Manual Agent Provisioning (Windows)
*   Utilized an elevated **PowerShell** session to deploy the Wazuh agent MSI.
*   Manually defined the Manager's IP address and registration parameters to ensure secure enrollment.
*   Verified the `Wazuh` service status to confirm the successful handshake with the manager.

<img width="1027" height="762" alt="Windows Agent Registration" src="https://github.com/user-attachments/assets/64dfe16b-5a79-47ba-ae26-fb14df073e58" />
<img width="908" height="274" alt="PowerShell Verification" src="https://github.com/user-attachments/assets/f101d753-f122-49d8-8313-3fee56190f7a" />

---

### 3. Manual Agent Provisioning (Ubuntu)
*   Integrated the official Wazuh repository via the **Linux Terminal**.
*   Configured the `ossec.conf` communication settings to link the endpoint with the manager.
*   Initialized the `wazuh-agent` service and monitored local logs to confirm successful registration.

<img width="1021" height="765" alt="Ubuntu Agent CLI Installation" src="https://github.com/user-attachments/assets/9ed05d6e-89d4-406c-ba81-4592a5935dad" />

---

### 4. Visibility & Telemetry Validation
*   Performed an audit of the **Agents Dashboard** to verify "Active" status across all platforms.
*   Validated system telemetry, including OS metadata, network interfaces, and package inventory.
*   Confirmed real-time log flow by monitoring security events ingested from both Windows and Linux environments.

<img width="1011" height="716" alt="Final Dashboard Connectivity Overview" src="https://github.com/user-attachments/assets/06e3c07b-5f62-42f8-98b4-1ed9aabeb12f" />

---

## 📊 Key Takeaways
*   **Cross-Platform Competency:** Gained hands-on experience in managing security telemetry for both Windows and Linux environments using native administration tools.
*   **SIEM Engineering:** Developed a practical understanding of the Manager-Agent communication model and the log collection lifecycle.
*   **Network Hardening:** Configured and validated virtual network adapters to ensure a stable and secure telemetry pipeline.

---

