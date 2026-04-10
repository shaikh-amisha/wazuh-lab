# Wazuh-based File and System Monitoring Lab

# 📌 Overview
This lab demonstrates a demonstration of file monitoring sysytem using Wazuh SIEM for real-time monitoring, threat detection, and log analysis.
This system integrates a Wazuh Manager, Indexer, Dashboard, and Agents to collect logs, detect anomalies, ans visualizes security events in a centralized interface.

# 🎯 Key Takeaways
Problem:
* Lack of centralized monitoring makes it difficult to detect unauthorized changes and suspicious activity.
Solution:
* Built a Wazuh lab that:
* Collects logs from endpoints
* Monitors file changes in real time
* Detects suspicious activity
Outcome:
* A working SIEM system capable of detecting security events and file modifications.

# 🎯 Objectives
* Monitor endpoints using Wazuh agents
* Detect unauthorized file changes
* Visualize alerts in real time
* Understand SIEM workflow

# Components Required
* Ubuntu Vm ( Wazuh Manager)
* Windows Host (Wazuh Agent)
* Wazuh Dashboard
* Wazuh Indexer

# ⚙️ Step-by-Step Workflow
1️⃣ Prerequisites
* Ubuntu VM (VirtualBox/VMware)
* Windows host machine
* Internet connectivity
* Admin access
* Bridged/NAT networking required for communication

2️⃣ Install Wazuh Manager (Ubuntu)
* curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh
* sudo bash wazuh-install.sh -a -i
* Installs:
Manager
Indexer
Dashboard

3️⃣ Access Dashboard
ip a
Open: https://<ubuntu-vm-ip>
Accept SSL warning
Login using credentials from installation

4️⃣ Install Wazuh Agent (Windows)
Download Wazuh agent MSI
Install using default settings

5️⃣ Register Agent with Manager
🔹 On Ubuntu:
sudo /var/ossec/bin/manage_agents
Press A → Add agent
Enter name (e.g., WindowsHost)
Leave IP blank
Press E → Extract key
🔹 On Windows:
Open Wazuh Agent Manager
Paste authentication key
Enter Manager IP
Save and restart agent

6️⃣ File Integrity Monitoring
Edit:
C:\Program Files (x86)\ossec-agent\ossec.conf

Add:
<directories realtime="yes">C:\Users\YourUser\Test</directories>

7️⃣ Restart Agent
Apply changes by restarting agent service.

8️⃣ Verification
Open Wazuh Dashboard
Go to Agents → status should be Active
Go to Integrity Monitoring
Create/modify/delete files
Check alerts

