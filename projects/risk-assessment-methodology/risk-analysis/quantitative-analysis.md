
# Quantitative Risk Analysis

## Metrics Used
- Asset Value (AV)
- Exposure Factor (EF)
- Single Loss Expectancy (SLE)
- Annualized Rate of Occurrence (ARO)
- Annualized Loss Expectancy (ALE)

| Risk ID | Asset Name            | Threat Description                | AV ($)   | EF  | SLE ($)   | ARO | ALE ($)   |
|---------|----------------------|----------------------------------|----------|-----|-----------|-----|-----------|
| R1      | Customer Data System | FTP Backdoor (CVE-2011-2523)     | 3,000,000| 0.6 | 1,800,000 | 0.5 | 900,000   |
| R2      | Authentication System| Weak Credentials (FTP, DB, VNC)  | 2,500,000| 0.5 | 1,250,000 | 1.0 | 1,250,000 |
| R3      | Network Communication| Telnet (Plaintext Exposure)      | 1,500,000| 0.4 | 600,000   | 1.5 | 900,000   |
| R4      | Web Application      | PHP Vulnerability (CVE-2012-1823) | 2,000,000| 0.5 | 1,000,000 | 0.7 | 700,000   |
| R5      | Database System      | PostgreSQL Default Credentials   | 2,800,000| 0.6 | 1,680,000 | 0.8 | 1,344,000 |

## Purpose
To estimate financial impact and support risk prioritization decisions.
