# Phase 1: Basic Metric Calculations

## 1. Introduction

In this phase, I analyzed employee responses to phishing simulation campaigns. The purpose is to measure how users behave at each stage of a phishing attack and identify where the organization is most vulnerable.

A phishing attack typically follows a sequence:

Email Sent → Opened → Link Clicked → Credentials Submitted → Sensitive Data Entered

Each stage represents a decision point where the user may either stop or continue the attack.

---

## 2. Understanding the Metrics

### Email Open Rate
Measures how many users opened the phishing email.

### Click-Through Rate
Measures how many users clicked the malicious link.

### Credential Submission Rate
Measures how many users entered their login credentials. This represents actual compromise.

### Data Entry Rate
Measures how many users provided additional sensitive information.

---

## 3. Step 1: Fundamental Rate Calculations

Formula:

Rate = (Number of Events / Number of Emails Sent) × 100

---

### Campaign A

Open Rate = (82 / 100) × 100 = 82%  
Click Rate = (47 / 100) × 100 = 47%  
Credential Rate = (18 / 100) × 100 = 18%  
Data Entry Rate = (5 / 100) × 100 = 5%  

---

### Campaign B

Open Rate = (200 / 250) × 100 = 80%  
Click Rate = (150 / 250) × 100 = 60%  
Credential Rate = (75 / 250) × 100 = 30%  
Data Entry Rate = (25 / 250) × 100 = 10%  

---

### Campaign C

Open Rate = (72 / 80) × 100 = 90%  
Click Rate = (60 / 80) × 100 = 75%  
Credential Rate = (12 / 80) × 100 = 15%  
Data Entry Rate = (8 / 80) × 100 = 10%  

---

## 4. Summary Table

| Campaign | Open Rate | Click Rate | Credential Rate | Data Entry Rate |
|----------|----------|------------|-----------------|-----------------|
| A | 82% | 47% | 18% | 5% |
| B | 80% | 60% | 30% | 10% |
| C | 90% | 75% | 15% | 10% |

---

## 5. Efficiency Metrics

### Open → Click Conversion

Campaign A = (47 / 82) × 100 = 57.3%  
Campaign B = (150 / 200) × 100 = 75%  
Campaign C = (60 / 72) × 100 = 83.3%  

---

### Click → Credential Conversion

Campaign A = (18 / 47) × 100 = 38.3%  
Campaign B = (75 / 150) × 100 = 50%  
Campaign C = (12 / 60) × 100 = 20%  

---

## 6. Efficiency Summary

| Campaign | Open → Click | Click → Credential |
|----------|--------------|--------------------|
| A | 57.3% | 38.3% |
| B | 75% | 50% |
| C | 83.3% | 20% |

---

## 7. Visualizations

Refer to the Technical Evidence folder for the full visual.
---

## 8. Key Findings

Campaign B has the highest credential compromise rate and is the most dangerous.

Campaign C has the highest engagement but lower credential compromise.

Human behavior is the primary vulnerability.
