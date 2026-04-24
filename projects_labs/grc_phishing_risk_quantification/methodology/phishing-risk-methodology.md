# Phishing Risk Quantification Methodology

## 1. Overview

This document describes the methodology used to analyze phishing simulation data and quantify organizational risk.

The approach follows a structured progression:

1. Behavioral Analysis  
2. Risk Projection  
3. Financial Impact Modeling  
4. Control Evaluation  
5. Statistical Validation  

Each stage builds on the previous one to ensure logical consistency and traceability.

---

## 2. Behavioral Metric Calculations

### 2.1 Fundamental Rates

The following metrics are used to measure user behavior:

- Email Open Rate  
- Click-Through Rate  
- Credential Submission Rate  
- Data Entry Rate  

### Formula

Rate = (Number of Events / Number of Emails Sent) × 100

---

### 2.2 Conversion Metrics

These measure how users progress through the phishing attack stages.

#### Open to Click Conversion

Open → Click Rate = (Clicks / Opens) × 100

#### Click to Credential Conversion

Click → Credential Rate = (Credentials Submitted / Clicks) × 100

---

## 3. Risk Projection Method

The phishing simulation results are scaled to the full organization.

### Formula

Compromised Users = Total Employees × Credential Rate

---

### Breach Estimation

Expected Breaches = Compromised Users × Breach Probability

---

## 4. Financial Risk Modeling

### 4.1 Single Loss Expectancy (SLE)

SLE represents the financial impact of one breach.

In this project:

SLE = $4,350,000

---

### 4.2 Annual Rate of Occurrence (ARO)

ARO represents the expected number of breaches per year.

ARO = Expected Breaches

---

### 4.3 Annualized Loss Expectancy (ALE)

ALE = SLE × ARO

This provides the total expected financial loss.

---

## 5. Control Effectiveness Evaluation

Controls are evaluated based on their ability to reduce risk.

### 5.1 Risk Reduction

Risk Reduction = Current ALE − New ALE

---

### 5.2 Return on Investment (ROI)

ROI = (Risk Reduction − Control Cost) / Control Cost

---

### 5.3 Adjusted Risk Calculation

New Credential Rate = Original Rate × (1 − Control Effectiveness)

---

## 6. Statistical Analysis

### 6.1 Confidence Interval

Confidence intervals are used to estimate the reliability of observed rates.

### Formula

Confidence Interval = p ± 1.96 × √[p(1 − p) / n]

Where:

- p = observed rate  
- n = sample size  

---

## 7. Risk Assessment Framework

Risk levels are determined using:

- Financial exposure  
- Credential compromise rate  
- Organizational impact  

Categories:

- Critical  
- High  
- Medium-High  

---

## 8. Assumptions

The following assumptions were applied:

- Phishing behavior is consistent across the organization  
- Breach probability is fixed at 25%  
- Cost per breach is constant at $4.35M  
- Control effectiveness is applied uniformly  

---

## 9. Limitations

- Simulation results may not fully reflect real-world behavior  
- External factors such as attacker sophistication are not modeled  
- Financial estimates are based on industry averages  

---

## 10. Conclusion

This methodology provides a structured approach for transforming phishing simulation data into measurable financial risk.

It enables organizations to:

- Quantify human-related security risks  
- Evaluate control effectiveness  
- Support data-driven security decisions  

The approach can be adapted for other cybersecurity risk scenarios beyond phishing.
