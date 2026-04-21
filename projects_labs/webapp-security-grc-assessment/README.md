# Web Application Security Assessment & GRC Risk Analysis

## Overview

This project presents a comprehensive web application security assessment conducted on a legacy environment using the OWASP Broken Web Applications (BWA) platform.

The assessment integrates:

* Technical vulnerability analysis
* OWASP Top 10 (2021) evaluation
* Governance, Risk, and Compliance (GRC) mapping

## Objectives

* Identify critical vulnerabilities
* Evaluate security posture
* Map findings to compliance frameworks:

  * OWASP Top 10
  * NIST Cybersecurity Framework
  * PCI DSS

## Scope

Target Environment:

* OWASP Broken Web Applications (BWA)

Applications Tested:

* WebGoat
* BodgeIt Store
* DVWA

## Methodology

1. Reconnaissance & Enumeration
2. Automated Scanning (Burp Suite)
3. Manual Testing (OWASP Top 10)
4. Risk & Compliance Mapping

## Key Findings

* Broken Access Control (Critical)
* Plaintext Credential Transmission (Critical)
* Weak Authentication Mechanisms
* Potential Injection Risks

## Repository Structure

* documentation/ → Full report and analysis
* technical-evidence/ → Raw scan outputs and logs
* screenshots/ → Visual proof of findings

## Tools Used

* Nmap
* Burp Suite Professional
* OWASP BWA

## Author

Ayuba Amadi
GRC Engineering – ICDFA

## Disclaimer

This project was conducted in a controlled lab environment for educational and research purposes only.
