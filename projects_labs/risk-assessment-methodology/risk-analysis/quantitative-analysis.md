## Quantitative Risk Analysis

### Objective
This analysis quantifies the financial impact of identified security risks using industry-standard risk calculation models (SLE and ALE). The goal is to support risk prioritization and informed decision-making.

---

### Metrics Definition

- **Asset Value (AV):** Estimated monetary value of the affected asset
- **Exposure Factor (EF):** Percentage of asset loss if the risk occurs
- **Single Loss Expectancy (SLE):** AV × EF
- **Annualized Rate of Occurrence (ARO):** Estimated frequency per year
- **Annualized Loss Expectancy (ALE):** SLE × ARO

---

### Quantitative Risk Table

| Risk ID | Asset Name            | Threat Description                | AV ($)   | EF  | SLE ($)   | ARO | ALE ($)   |
|---------|----------------------|----------------------------------|----------|-----|-----------|-----|-----------|
| R1      | Customer Data System | FTP Backdoor (CVE-2011-2523)     | 3,000,000| 0.6 | 1,800,000 | 0.5 | 900,000   |
| R2      | Authentication System| Weak Credentials (FTP, DB, VNC)  | 2,500,000| 0.5 | 1,250,000 | 1.0 | 1,250,000 |
| R3      | Network Communication| Telnet (Plaintext Exposure)      | 1,500,000| 0.4 | 600,000   | 1.5 | 900,000   |
| R4      | Web Application      | PHP Vulnerability (CVE-2012-1823) | 2,000,000| 0.5 | 1,000,000 | 0.7 | 700,000   |
| R5      | Database System      | PostgreSQL Default Credentials   | 2,800,000| 0.6 | 1,680,000 | 0.8 | 1,344,000 |

---

### Key Insights

- **Highest Financial Risk:** R5 (Database System) with an ALE of $1,344,000  
- **Most Frequent Threat:** R3 (Telnet Exposure) with the highest ARO (1.5)  
- **Most Critical Control Failure:** R2 (Weak Credentials), impacting multiple systems  

---

### Risk Prioritization

Based on ALE values, risks should be prioritized as follows:

1. R5 – Database System Compromise  
2. R2 – Weak Authentication Controls  
3. R1 / R3 – Infrastructure-Level Risks  
4. R4 – Web Application Vulnerability  

---

### Strategic Interpretation

The analysis shows that the organization faces the highest financial exposure from:

- Weak access control mechanisms  
- Default and insecure configurations  
- Legacy protocols lacking encryption  

This indicates that risk is driven more by **poor security governance and control failures** than by advanced attack techniques.
