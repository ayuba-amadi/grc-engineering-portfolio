# Phase 1: Risk Exposure Calculation

## 1. Introduction

In this phase, I quantified the financial exposure associated with the key vulnerabilities identified in the SecureMobile banking platform assessment. The purpose of this phase was to determine the annual financial impact of each vulnerability using quantitative risk analysis.

---

## 2. Method Used

I applied the standard quantitative risk analysis approach using:

- Single Loss Expectancy (SLE)
- Annual Rate of Occurrence (ARO)
- Annualized Loss Expectancy (ALE)

ALE = SLE × ARO

---

## 3. Risk Calculations

### API Authentication Bypass
SLE = $5,000,000  
ARO = 0.15  
ALE = $750,000  

### Database Injection
SLE = 500,000 × $250 = $125,000,000  
ARO = 0.25  
ALE = $31,250,000  

### Session Hijacking
SLE = 5,000 × $1,500 = $7,500,000  
ARO = 0.40  
ALE = $3,000,000  

---

## 4. Risk Summary

| Vulnerability | SLE | ARO | ALE |
|--------------|-----|-----|-----|
| API Authentication Bypass | $5,000,000 | 0.15 | $750,000 |
| Database Injection | $125,000,000 | 0.25 | $31,250,000 |
| Session Hijacking | $7,500,000 | 0.40 | $3,000,000 |

---

## 5. Risk Prioritization

| Vulnerability | ALE | Priority |
|--------------|-----|----------|
| Database Injection | $31,250,000 | High |
| Session Hijacking | $3,000,000 | Medium |
| API Authentication Bypass | $750,000 | Low |

---

## 6. Visualizations

The following visualizations support this analysis:

- ALE Comparison Bar Chart  
- Risk Distribution Pie Chart  
- Risk Heat Map  

Refer to the technical_evidence folder for charts.
