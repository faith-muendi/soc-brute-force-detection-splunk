# SOC Lab: Brute Force Attack Detection using Splunk SIEM

## Project Overview
This project demonstrates an end-to-end simulation and detection of a brute-force attack using Kali Linux and Splunk SIEM.

---

## Lab Setup
- Attacker: Kali Linux
- Target: Windows Server 2022
- SIEM: Splunk
- Protocol: SMB

---

## Attack Simulation
A brute-force attack was performed using CrackMapExec:

crackmapexec smb <target-ip> -u john -p wrongpassword

Multiple failed login attempts were generated followed by a successful login.

---

## Detection

### Failed Logins (4625)
index=* EventCode=4625
| stats count by Source_Network_Address

---

### Successful Login (4624)
index=* EventCode=4624
| table _time Account_Name Source_Network_Address

---

## Analysis
Multiple failed login attempts from a single IP followed by a successful login indicate a brute-force attack.

---

## Skills Demonstrated
- Splunk SIEM
- Log Analysis
- Threat Detection
- Incident Investigation
