# Wazuh File Integrity Monitoring (FIM) – Risk Monitoring & Control Validation Lab

## 1. Overview

This project demonstrates the implementation and validation of a **File Integrity Monitoring (FIM)** control using Wazuh.

The lab simulates a real-world risk scenario involving:

- Unauthorized file creation
- Unauthorized file modification
- Unauthorized file deletion

The objective is to verify that the control:

- Detects file integrity violations
- Logs events with sufficient detail
- Provides audit-ready compliance evidence

---

## 2. Lab Objective

To validate that Wazuh FIM operates effectively as a **detective control** for monitoring sensitive files.

---

## 3. Environment

| Component        | Description                         |
|-----------------|-------------------------------------|
| Wazuh Manager   | Ubuntu Server (10.10.10.227)        |
| Endpoint        | Windows 10 VM (10.10.10.70)         |
| Agent           | Wazuh Agent installed on Windows    |
| Monitoring Path | `C:\SensitiveFiles`                 |

---

## 4. Risk Scenario

**Risk:** Unauthorized modification of financial documents

**Asset:**  
`C:\SensitiveFiles\Q4_Financial_Forecast.docx`

**Threats Simulated:**
- Insider misuse
- Unauthorized access
- Data manipulation

---

## 5. Control Implemented

**Control Type:** Detective Control  
**Control Name:** File Integrity Monitoring (FIM)

**Capability:**
- Detect file creation
- Detect file modification (via checksum)
- Detect file deletion

---

## 6. Test Activities

| Activity        | Command Used |
|----------------|-------------|
| File Creation  | `echo ... > file` |
| File Modification | `echo ... >> file` |
| File Deletion  | `del file` |

---

## 7. Key Results

| Event       | Detection Status |
|------------|-----------------|
| File Created | Detected |
| File Modified | Detected |
| File Deleted | Detected |

Wazuh successfully generated alerts for all events.

---

## 8. Evidence

All supporting materials are stored in:

- `/evidence/screenshots/`
- `/evidence/reports/`

---

## 9. Compliance Coverage

Wazuh automatically mapped events to:

- PCI DSS (11.5)
- HIPAA (164.312.c.1 / c.2)
- NIST 800-53 (SI-7)
- GDPR (II_5.1.f)
- MITRE ATT&CK
- Trust Services Criteria (TSC)

---

## 10. Conclusion

The FIM control is:

- Operational
- Reliable
- Audit-ready

This lab demonstrates how technical controls support **risk monitoring, governance, and compliance**.

---

## 11. Author

Ayuba Amadi
