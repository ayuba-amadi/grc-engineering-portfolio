
# Risk Assessment Table

## Includes
- Affected services
- CVE references
- Risk ratings (Low, Medium, High)
- Compliance alignment
- Business impact description

## Overview
This table summarizes identified vulnerabilities, their associated risks, and business impact.

## Risk Table

-------------------------------------------------------------------------------------------------------------------------------------
| Risk ID | Finding                  | Service    | CVE            | Risk Level | Compliance Mapping        | Business Impact        |
|---------|--------------------------|------------|----------------|------------|---------------------------|------------------------|
| R1      | FTP Backdoor             | FTP        | CVE-2011-2523  | High       | CIS 7.1                   | Full system compromise |
| R2      | Telnet Unencrypted       | Telnet     | N/A            | High       | NIST PR.DS-2              | Credential theft       |
| R3      | Weak Credentials         | SSH/FTP    | N/A            | High       | CIS 5.2                   | Unauthorized access    |
| R4      | Default DB Credentials   | PostgreSQL | N/A            | Critical   | NIST AC-2                 | Data exposure          |
-------------------------------------------------------------------------------------------------------------------------------------

## Key Observations

- Most risks are authentication-related failures
- Legacy services significantly increase exposure
- Lack of encryption violates basic compliance requirements

  
