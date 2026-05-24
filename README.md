# Operation Phantom Pursuit
## Digital Forensics & Incident Response (DFIR) Project

---

## Project Overview
This project simulates a real-world cybersecurity incident response investigation involving log analysis, live system triage, and disk forensics.

The goal was to identify attacker activity, trace persistence mechanisms, and recover deleted forensic artifacts from a compromised system.

---

## Scenario
A containerized enterprise environment was compromised. The attacker established a reverse shell, maintained persistence, and attempted to hide malware artifacts on disk.

---

## Tools Used
- Docker
- Linux CLI (Ubuntu / Alpine)
- Kibana (SIEM)
- Netcat (nc)
- Sleuth Kit (fls, icat, istat)
- SHA256 hashing
- Git / GitHub

---

## Investigation Phases

### Phase 1 - SIEM Analysis
- Source IP identified from critical alert logs:
  - 198.51.100.44

---

### Phase 2 - Live Triage
- Accessed quarantined Docker container
- Identified persistent listener on port 4444
- Process ID (PID): 11
- SHA256 of disk image:
  - aee693b7f906b7d366d036697ebec6eea7bbaeab86536df98296cb37736ef1c9

---

### Phase 3 - Disk Forensics
- Deleted file found: beacon.exe
- Inode: 582
- Status: Not allocated (deleted)
- No recoverable payload data found (size 0)

---

## Conclusion
The investigation confirmed malicious activity including:
- External intrusion
- Reverse shell persistence
- Deleted malware staging artifact

All evidence was documented and validated using forensic tools.

---

## Author
John - DFIR Training Project
