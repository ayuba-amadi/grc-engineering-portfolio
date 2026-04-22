# Input Dataset Description

## Scenario Overview

This project is based on a simulated financial system:

SecureMobile – a mobile banking platform with:

- 500,000 active users  
- 50,000 daily transactions  
- Average transaction value of $2,500  

---

## Vulnerabilities Assessed

### 1. API Authentication Bypass
- Exploit Probability: 15%  
- Impact: Unauthorized transactions  
- Maximum Loss: $5,000,000  

---

### 2. Database Injection
- Exploit Probability: 25%  
- Impact: Data breach (PII + financial data)  
- Records at Risk: 500,000  
- Cost per Record: $250  

---

### 3. Session Hijacking
- Exploit Probability: 40%  
- Impact: Account takeover  
- Accounts at Risk: 5,000  
- Loss per Account: $1,500  

---

## Control Options

- Web Application Firewall (WAF)  
- Multi-Factor Authentication (MFA)  
- API Security Gateway  

---

## Purpose of Dataset

This dataset enables:

- Quantitative risk analysis  
- Financial impact modeling  
- Control effectiveness evaluation  
