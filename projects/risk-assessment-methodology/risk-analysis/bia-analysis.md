# Business Impact Analysis (BIA)

## Includes
- Affected business processes
- Recovery Time Objective (RTO)
- Recovery Point Objective (RPO)
- Financial impact
- Non-financial impact

| Risk ID | Threat Description               | Affected Business Process     | RTO     | RPO     | Financial Impact (Estimated) | Non-Financial Impact                           |
|---------|----------------------------------|-------------------------------|---------|---------|------------------------------|------------------------------------------------|
| R1      | FTP Backdoor (CVE-2011-2523)     | Customer Data Management      | 24 hours| 6 hours | $900,000/year                | Data loss, regulatory penalties                |
| R2      | Weak Credentials                 | User Authentication System    | 12 hours| 2 hours | $1,250,000/year              | Unauthorized access, reputational damage       |
| R3      | Telnet (Plaintext Exposure)      | Internal Communications       | 8 hours | 1 hour  | $900,000/year                | Data interception, loss of trust               |
| R4      | PHP Vulnerability (CVE-2012-1823)| Web Application Services      | 16 hours| 4 hours | $700,000/year                | Website compromise, service disruption         |
| R5      | Database Default Credentials     | Financial Transactions        | 24 hours| 2 hours | $1,344,000/year              | Data breach, legal consequences, customer los  |

## Purpose
To understand how technical failures affect business continuity and operations.
