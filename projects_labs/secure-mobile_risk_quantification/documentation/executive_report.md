# Phase 3: Executive Reporting

## 1. Objective

In this phase, I translated the analysis into an executive-level decision report.

---

## 2. Top Risks

| Rank | Vulnerability | ALE |
|------|--------------|-----|
| 1 | Database Injection | $31,250,000 |
| 2 | Session Hijacking | $3,000,000 |
| 3 | API Authentication Bypass | $750,000 |

---

## 3. Recommended Controls

| Priority | Control | Cost |
|---------|--------|------|
| 1 | WAF | $150,000 |
| 2 | MFA | $200,000 |
| 3 | API Gateway | $350,000 |

---

## 4. Risk Reduction

| Control | Risk Reduction |
|--------|---------------|
| WAF | $24,000,000 |
| MFA | $2,850,000 |
| API Gateway | $675,000 |

---

## 5. ROI Summary

| Control | ROI |
|--------|-----|
| WAF | 159 |
| MFA | 13.25 |
| API Gateway | 0.93 |

---

## 6. Visualizations
 
Please refer to the techanical_evidence folder for the below charts

 Risk Exposure Before vs After (double_bar.png)  
 Control Investment Breakdown (stacked.png)  
 ROI Comparison (roi_horizontal.png)  

---

## 7. Implementation Plan

### Immediate (0–30 Days)
- Deploy MFA  
- Apply temporary WAF rules  

### Short-Term (30–90 Days)
- Full WAF deployment  
- Testing and tuning  

### Long-Term (3–12 Months)
- API Gateway implementation  
- Continuous monitoring  

---

## 8. Conclusion

The Web Application Firewall provides the highest financial impact and should be implemented first. Multi-Factor Authentication follows as an effective quick-win control, while the API Gateway should be implemented as a long-term improvement.
