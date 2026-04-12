## Risk Assessment Table

### Scope
This table presents identified security vulnerabilities, associated risks, compliance violations, and business impact based on technical scan results.

### Risk Classification Criteria
- High: Easily exploitable, leads to full system compromise
- Medium: Requires some skill, leads to data exposure
- Low: Limited impact, mainly information disclosure

---

### Risk Table

| Risk ID | Finding                     | Affected Service | CVE Reference     | Risk Level | Compliance Mapping       | Business Impact              |
|---------|----------------------------|------------------|-------------------|------------|--------------------------|------------------------------|
| R1      | FTP Backdoor               | FTP              | CVE-2011-2523     | High       | CIS 7.1                  | Full system compromise       |
| R2      | Unencrypted Telnet Service | Telnet           | N/A               | High       | NIST CSF PR.DS-2         | Credential theft             |
| R3      | Weak Authentication        | SSH, FTP         | N/A               | High       | CIS 5.2                  | Unauthorized access          |
| R4      | Default Database Credentials | PostgreSQL     | N/A               | High       | NIST SP 800-53 AC-2      | Sensitive data exposure      |

---

### Key Observations

- The majority of identified risks are related to weak authentication and poor access control.
- Legacy and insecure services (FTP, Telnet) significantly increase the attack surface.
- Lack of encryption mechanisms violates established data protection standards.
- All identified risks fall within the “High” category, indicating a critical security posture.

---

### Strategic Interpretation

The system demonstrates fundamental security weaknesses rather than isolated vulnerabilities. The primary risk drivers include:

- Absence of secure configuration baselines
- Use of outdated and unsupported services
- Failure to enforce identity and access management controls

This reflects a governance and compliance failure, not just a technical issue.
