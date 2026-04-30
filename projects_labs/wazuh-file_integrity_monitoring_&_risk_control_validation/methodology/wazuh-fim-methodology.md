# Wazuh FIM Control Validation Methodology

## 1. Control Type

Detective Control

---

## 2. Monitoring Configuration

Path monitored:

C:\SensitiveFiles

Mode:

Realtime monitoring enabled

---

## 3. Events Simulated

| Event Type | Description |
|----------|-------------|
| Creation | New file introduced |
| Modification | File content changed |
| Deletion | File removed |

---

## 4. Detection Logic

Wazuh syscheck module detects:

- File presence changes
- Hash changes (MD5, SHA1, SHA256)
- File size changes
- Metadata changes

---

## 5. Alert Generation

Each event generates:

- Rule ID
- Rule level
- Timestamp
- File path
- Event type

---

## 6. Compliance Mapping

Events are automatically mapped to:

- PCI DSS 11.5
- HIPAA 164.312
- NIST SI-7
- GDPR integrity controls
- MITRE ATT&CK techniques

---

## 7. Effectiveness Indicators

The control is effective if:

- Events are detected in real time
- Alerts contain integrity data
- Evidence is retrievable

---

## 8. Limitation

This control does not prevent attacks.

It only detects and reports them.

Preventive controls must be added separately.
