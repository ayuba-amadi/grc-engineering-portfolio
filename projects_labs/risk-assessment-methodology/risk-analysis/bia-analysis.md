## Business Impact Analysis (BIA)

### Objective
This analysis evaluates the operational and financial impact of identified security risks on critical business processes. It supports prioritization of recovery efforts and alignment with business continuity requirements.

---

### BIA Table

| Risk ID | Threat Description                | Affected Business Process     | RTO     | RPO     | Financial Impact (Estimated) | Non-Financial Impact |
|---------|----------------------------------|-------------------------------|---------|---------|------------------------------|----------------------|
| R1      | FTP Backdoor (CVE-2011-2523)     | Customer Data Management      | 24 hours| 6 hours | $900,000/year                | Data loss, regulatory penalties |
| R2      | Weak Credentials                 | User Authentication System    | 12 hours| 2 hours | $1,250,000/year              | Unauthorized access, reputational damage |
| R3      | Telnet (Plaintext Exposure)      | Internal Communications       | 8 hours | 1 hour  | $900,000/year                | Data interception, loss of trust |
| R4      | PHP Vulnerability (CVE-2012-1823)| Web Application Services      | 16 hours| 4 hours | $700,000/year                | Website compromise, service disruption |
| R5      | Database Default Credentials     | Financial Transactions        | 24 hours| 2 hours | $1,344,000/year              | Data breach, legal consequences, customer loss |

---

### Key Impact Insights

- **Highest Financial Impact:** R5 (Database System) – $1,344,000/year  
- **Most Time-Sensitive Risk:** R3 (Telnet Exposure) – lowest RTO (8 hours)  
- **Most Critical Business Function:** Authentication system (R2), affecting all user access  

---

### Business Continuity Implications

- Short RTO values indicate limited tolerance for downtime, requiring rapid incident response capabilities  
- Low RPO values highlight the need for frequent backups and strong data protection mechanisms  
- Critical systems (authentication, financial transactions) require priority in disaster recovery planning  

---

### Strategic Interpretation

The organization’s highest risks are concentrated around:

- Identity and access management failures  
- Exposure of sensitive financial and customer data  
- Lack of secure communication protocols  

This indicates that operational disruption is most likely to occur due to **basic control failures**, not advanced threats.

---

### Recommendation Summary

- Prioritize protection of authentication and database systems  
- Eliminate insecure protocols such as Telnet  
- Strengthen backup, recovery, and monitoring capabilities  
