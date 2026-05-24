# Incident Response Report - Operation Phantom Pursuit

---

## Phase 1 - SIEM Correlation: The Alert

- Source IP: 198.51.100.44

---

## Phase 2 - Live Triage & Chain of Custody

- Suspicious Process PID: 11
- Process: nc -lvnp 4444 (Netcat listener backdoor)

- SHA256 Hash of compromised drive:
aee693b7f906b7d366d036697ebec6eea7bbaeab86536df98296cb37736ef1c9

- Description:
A persistent malicious process was observed on port 4444. A root-level shell loop was spawning a netcat listener continuously to maintain persistence inside the container.

---

## Phase 3 - Disk Autopsy & Deleted File Recovery

- File Name: beacon.exe
- Inode: 582
- Status: Deleted (Not Allocated)
- Recovery Result: Not recoverable (Size = 0, orphaned directory entry only)

- Description:
The deleted file was identified in the filesystem metadata. However, no recoverable payload data was present in disk blocks or inode content, indicating the file was either wiped or never fully written to disk.

---

## Final Summary

The breach originated from external IP 198.51.100.44. The attacker deployed a netcat-based persistent listener on port 4444 inside a quarantined container, enabling potential command-and-control access. A deleted artifact (beacon.exe) was discovered in the disk image, confirming evidence of malware staging activity. No recoverable payload was extracted from the deleted file.

