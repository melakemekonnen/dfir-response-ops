# INCIDENT RESPONSE REPORT: PHANTOM PURSUIT
**Operator:** melakee

## PHASE 1: SIEM CORRELATION
* **Initial Alert Source IP:** 198.51.100.44
* **Event Type:** Critical Alert — Unauthorized Access Detected on Web-01
* **Timestamp:** 2026-04-30 10:15:00 UTC

## PHASE 2: LIVE TRIAGE & CHAIN OF CUSTODY
* **Suspicious Process ID (PID):** 10
* **Process Name / Port:** nc (Netcat) listening on 0.0.0.0:4444 — bind shell backdoor
* **Evidence SHA256 Hash:** 9b1cdddf670e312eeadada65605084190e233c8e861798ba1c7d505935c92db1

## PHASE 3: DISK FORENSICS
* **Deleted File Inode Number:** 582
* **Recovered Filename:** beacon.exe (FAT deletion tombstone confirmed as _EACON.EXE — first byte overwritten with 0xE5 deletion marker)
* **Infection Timestamp (from inode metadata):** 2026-05-21 00:18:35 EDT
* **Extracted Payload Data:** Inode 582 metadata recovered via istat; data clusters were zeroed (size 0, sector 108 empty), consistent with secure deletion by the attacker. Filename, deletion marker, and infection timestamp recovered from the FAT directory entry. Active beacon component identified during live triage as nc (PID 10) listening on port 4444.
