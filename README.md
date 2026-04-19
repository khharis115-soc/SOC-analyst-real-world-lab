# SOC-analyst-real-world-lab
This repository documents my hands-on experience with Security Information and Event Management (SIEM) tools, intrusion detection, and incident response. It demonstrates my ability to monitor network traffic, analyze logs, and identify potential security threats.

## Introduction: SOC Analyst Lab - FTP Attack Detection

This lab focuses on the end-to-end cycle of a cyber attack: from execution to detection. By simulating a brute force attack using Hydra on a Kali Linux machine, we generate real-world malicious traffic against a Metasploitable 2 target.The core of the lab is the SOC Analyst's perspective on an Ubuntu-based Splunk SIEM. The goal is to ingest raw vsftpd.log files  and use Search Processing Language (SPL) to identify the attacker's IP, the targeted account, and the success or failure of the login attempts. This practical exercise demonstrates how centralized logging is critical for incident response and forensic analysis.

## Environment Architecture
Attacker: Kali Linux (10.0.2.6) Target (Victim): Metasploitable 2 (10.0.2.5) 
## SIEM Platform: Splunk Enterprise on Ubuntu (10.0.2.15) 
## Offensive Phase (Attack Simulation)
The attack was performed using Hydra to target the FTP service on the Metasploitable machine.Command Used:hydra -l msfadmin -p msfadmin ftp://10.0.2.5 Result: 1 valid password found (msfadmin/msfadmin).
##  Defensive Phase 
(SOC Analysis)Data IngestionConnected to the Metasploitable target from the Ubuntu machine via FTP.Navigated to /var/log/ and downloaded the vsftpd.log file.Uploaded the log file into the Splunk platform for indexing.Search and IdentificationUsed the following SPL query in Splunk to isolate the attack events:Splunk SPLsource="vsftpd.log" host="ubuntu-VirtualBox" sourcetype="vsftp log"
## Findings & EvidenceAttacker Identification:
Logs confirmed multiple connections from IP 10.0.2.6.Compromise Confirmation: The logs show an OK LOGIN for user msfadmin originating from the attacker's IP at 09:07:54 AM.Activity Trace: Post-login activity, including a directory download of vsftpd.log, was clearly visible in the audit trail.5. ConclusionThis lab successfully demonstrates how a SOC analyst can use Splunk to bridge the gap between a network event and a security incident. By analyzing vsftpd logs, we identified the exact source and timestamp of an unauthorized login.

<img width="1280" height="800" alt="VirtualBox_ubuntu _18_04_2026_19_10_59" src="https://github.com/user-attachments/assets/7b7a5609-5318-41b3-8402-a8fa759e80ac" />

<img width="1280" height="800" alt="VirtualBox_ubuntu _18_04_2026_19_11_17" src="https://github.com/user-attachments/assets/71ef4c9d-d2e0-4efd-8d16-6470461fe6b4" />

<img width="1280" height="800" alt="VirtualBox_ubuntu _18_04_2026_19_11_26" src="https://github.com/user-attachments/assets/16a75b86-eaa0-4ba8-a344-eda0928d1510" />

<img width="1280" height="800" alt="VirtualBox_ubuntu _18_04_2026_19_11_53" src="https://github.com/user-attachments/assets/1a5bac09-90ea-4cef-ab9e-f3f3b5e5aa9d" />

<img width="1366" height="643" alt="VirtualBox_kalilinux_18_04_2026_19_28_46" src="https://github.com/user-attachments/assets/b8a56cf7-9b58-4dbf-be5c-4686d1492ce1" />

<img width="1280" height="800" alt="VirtualBox_ubuntu _18_04_2026_19_13_13" src="https://github.com/user-attachments/assets/992834d2-dd29-47f9-a595-b371c729b1a9" />

<img width="1280" height="800" alt="VirtualBox_ubuntu _18_04_2026_19_29_15" src="https://github.com/user-attachments/assets/78894b25-0d7c-408c-affe-402b2d39451e" />
