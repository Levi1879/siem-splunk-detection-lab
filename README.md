# siem-splunk-detection-lab

This project simulates a real-world SOC environment by building a SIEM pipeline in Splunk and developing detection use-cases for common attack techniques such as brute-force attempts, credential dumping, and suspicious process execution.


🎯 Project Scope
Centralized log collection from Windows and Linux systems
Sysmon integration for advanced endpoint visibility
Real-time log monitoring
Detection use-case development
Dashboard-based threat visualization

⚙️ Technologies Used
Splunk (SIEM)
Sysmon
Windows Event Logs
Linux Syslogs
Nmap
FortiGate (log source simulation)

🧩 Architecture Overview
Splunk Server (Indexer + Search Head)
Windows Endpoint (Sysmon + Universal Forwarder)
Linux Endpoint (Syslog + Universal Forwarder)

All logs were forwarded via Splunk Universal Forwarder over port 9997.

📥 Log Ingestion
Installed Universal Forwarder on Windows & Linux
Configured log forwarding:
Windows Event Logs
Sysmon Logs
Linux /var/log/
Verified ingestion via Splunk Search

🔍 Sysmon Configuration
Custom XML configuration applied
Focused on detecting:
Process creation
Network connections
LSASS access attempts

Example monitored source:

WinEventLog:Microsoft-Windows-Sysmon/Operational

🚨 Detection Use-Cases

1. Brute Force Attack Detection
Event ID: 4625
Identified high-frequency failed login attempts
Grouped by source IP and user
2. PowerShell Activity Monitoring
Event ID: 4688
Detected suspicious PowerShell executions
Analyzed parent-child process relationships
3. Suspicious Tool Execution
Sysmon EventCode=1
Detected tools such as:
mimikatz
netcat
certutil
4. LSASS Access Detection
Sysmon Event ID: 10
Identified potential credential dumping attempts
Monitored process access to lsass.exe
5. Network Traffic Analysis (FortiGate Logs)
Parsed firewall logs
Identified top talkers and traffic patterns

📊 Dashboards

Created multiple dashboards including:

Failed login trends
Process execution tracking
Suspicious activity monitoring
Network traffic visualization

📈 Key Outcomes
Built an end-to-end SIEM pipeline
Developed practical detection use-cases
Gained hands-on experience in SPL queries
Improved understanding of attacker behavior and detection logic

⚠️ Limitations
No cloud log integration (AWS/Azure)
Limited lateral movement simulation
Partial SSL inspection deployment

🚀 Future Improvements
Integrate cloud log sources
Implement advanced attack simulations
Automate detection rules

