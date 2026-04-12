### **Risk Assessment Report**

# **Risk Assessment Methodologies - Technical Scanning to GRC Analysis**

## Overview
This document presents a technical-to-GRC risk assessment performed on a vulnerable system using industry-standard tools.

## Scope
- Target: Metasploitable 2
- Environment: Controlled lab environment
- Tools Used: Nmap, Nikto, Nuclei

## Objectives
- Identify vulnerabilities
- Map to business risk
- Quantify financial impact
- Recommend treatment strategies

# **Executive Summary**

This lab demonstrated the full process of translating technical security
findings into business-focused risk management decisions. Using tools
such as Nmap, Nikto, and Nuclei, multiple critical vulnerabilities were
identified on the Metasploitable system, including outdated services,
weak authentication mechanisms, exposed databases, and known exploitable
backdoors.

The analysis revealed that several vulnerabilities pose a high financial
and operational risks, with estimated annual losses exceeding \$1
million for key systems such as databases and authentication services.
These risks directly impact critical business functions, including
customer data management, financial transactions, and system
availability.

By applying structured risk assessment methods, including risk triage,
quantitative analysis (SLE and ALE), and Business Impact Analysis (BIA),
The technical findings were translated into measurable business risks.
Appropriate risk treatment strategies were developed, with a strong
Focus on mitigation through patching, system hardening, and access
control improvements.

The findings were aligned with recognized industry standards, such as the
National Institute of Standards and Technology Cybersecurity Framework,
NIST SP 800-53, CIS Controls, and PCI DSS, ensuring that recommendations are followed
follow accepted best practices.

Overall, this lab highlights the importance of integrating technical
security assessments with governance, risk, and compliance (GRC)
processes to support informed decision-making at the management level.

# **Phase 1: Information Gathering and Service Discovery**

## **Objective**

The objective of this phase is to identify open ports, running services,
and system characteristics of the target system (Metasploitable 2). This
helps to understand the system's attack surface and provides the
foundation for vulnerability identification and risk analysis.

## **Work Performed**

A working directory was created to organize all outputs related to this
task. A comprehensive network scan was then executed using Nmap with
service detection, default scripts, operating system detection, and full
port scanning enabled.

### **Command Executed**

sudo nmap -sV -sC -O -p- -oA initial_scan 10.97.241.156

This command performs the following:

-   -sV: Detects service versions

-   -sC: Runs default scripts for additional information

-   -O: Identifies the operating system

-   -p-: Scans all 65535 ports

-   -oA: Saves output in three formats (.nmap, .xml, .gnmap)

### **HTML Report Generation**

The XML output was converted into a readable HTML report using:

xsltproc -o initial_scan_report.html /usr/share/nmap/nmap.xsl
initial_scan.xml

**Findings**

The scan revealed that the target system has many open ports and
outdated services. This indicates a high attack surface.

### **Key Observations**

1.  **Multiple Critical Services Exposed**

    a.  FTP (21) -- vsftpd 2.3.4

    b.  SSH (22) -- OpenSSH 4.7

    c.  Telnet (23) -- insecure remote access

    d.  HTTP (80) -- Apache 2.2.8

    e.  MySQL (3306)

    f.  PostgreSQL (5432)

2.  **Presence of Known Vulnerable Services**

    a.  vsftpd 2.3.4 (known backdoor vulnerability)

    b.  UnrealIRCd (historically vulnerable)

    c.  Old Apache and SSH versions

3.  **Insecure Configurations**

    a.  Anonymous FTP login allowed

    b.  Telnet transmitting data in plain text

    c.  SMB message signing disabled

4.  **Unnecessary Services Running**

    a.  IRC (6667)

    b.  VNC (5900)

    c.  Java RMI (1099, 42323)

    d.  Distccd (3632)

5.  **Operating System Information**

    a.  Linux Kernel 2.6.x (outdated)

## **Analysis (What This Means)**

The system is highly exposed due to:

-   Too many open ports

-   Outdated software versions

-   Weak or insecure configurations

This significantly increases the likelihood of:

-   Unauthorized access

-   Remote system compromise

-   Data leakage

# **Phase 2 -- Step 1: Nmap Output Analysis**

## **Objective**

The objective of this step is to analyse the Nmap scan results to
identify running services, their versions, and any security weaknesses.
This information is used to detect potential vulnerabilities and support
risk assessment activities.

## **Commands Executed**

## **nano initial_scan.nmap**


## **Findings**

### **1. Identified Services and Versions**

 | -------------------------------------------------------------------------------|
 | **Port** |  **Service** |  **Version**      |  **Security Concern**            |
 | ---------|---------------------------------------------------------------------|
 | 21       |  FTP         |  vsftpd 2.3.4     |  Known backdoor vulnerability    |
 ---------------------------------------------------------------------------------|
 | 22       |  SSH         |  OpenSSH 4.7      |  Outdated version                |
 ---------------------------------------------------------------------------------|
 | 23       |  Telnet      |  Linux telnetd    |  Unencrypted communication       |
 ---------------------------------------------------------------------------------|
 | 25       |  SMTP        |  Postfix          |  Weak encryption (SSLv2 enabled) |
 ---------------------------------------------------------------------------------|
 | 53       |  DNS         |  BIND 9.4.2       |  Outdated DNS server             |
 ---------------------------------------------------------------------------------|
 | 80       |  HTTP        |  Apache 2.2.8     |  Outdated web server             |
 ---------------------------------------------------------------------------------|
 | 139/445  |  SMB         |  Samba 3.0.20     |  Known vulnerabilities           |
 ---------------------------------------------------------------------------------|
 | 3306     |  MySQL       |  5.0.51           |  Weak database security          |
 ---------------------------------------------------------------------------------|
 | 5432     |  PostgreSQL  |  8.3.x            |  Outdated database               |
 ---------------------------------------------------------------------------------|
 | 8180     |  HTTP        | Apache Tomcat 5.5 |  Vulnerable application server   |
  --------------------------------------------------------------------------------|

### **2. Critical Security Misconfigurations**

The scan identified several serious configuration issues:

-   Anonymous FTP login enabled

-   FTP and Telnet transmit data in plain text

-   SSLv2 enabled (weak encryption)

-   SMB message signing disabled

-   Multiple unnecessary services exposed

### **3. High-Risk Services Identified**

The following services significantly increase the attack surface:

-   Telnet (insecure remote access)

-   FTP (anonymous access + known exploit)

-   RPC and NFS (exposed internal services)

-   IRC and Java RMI (often exploited services)

-   Bind shell on port 1524 (critical backdoor indicator)

## **Analysis (Security Interpretation)**

The system exposes many services, many of which are outdated and
insecure. This increases the likelihood of successful attacks such as:

-   Remote system compromise

-   Credential theft

-   Unauthorized access

-   Service exploitation

The presence of legacy protocols (Telnet, FTP) and outdated software
Versions show a lack of proper system hardening and patch management.

**Step 2: Web Application Assessment**

**Objective**

The objective of this step is to identify web application
vulnerabilities and weak configurations on the target system using Nikto
and manual browser inspection. Web applications are high-risk attack
vectors because they are directly exposed to users and attackers. The
OWASP Top 10 is a standard awareness document for the most critical web
application security risks, and PCI DSS Requirement 6 focuses on
developing and maintaining secure systems and applications.

### **Command Executed**

nikto -h <http://10.97.241.156> -o nikto_scan.txt

### **Key Findings**

The Nikto scan identified several important web application weaknesses:

1.  **Outdated Apache Web Server**
    
    The server is running Apache 2.2.8, which is outdated and no longer
    considered secure.

2.  **Outdated PHP Version**

    The server exposes PHP/5.2.4-2ubuntu5.10, which is very old and may
    contain known vulnerabilities.

3.  **Missing Security Headers**

    The anti-clickjacking X-Frame-Options header is not present. This
    weakens browser-side protection.
    
4.  **HTTP TRACE Method Enabled**

    The TRACE method is active, which may support Cross-Site Tracing (XST).

5.  **Sensitive Information Exposure**

    The file /phpinfo.php is accessible and reveals PHP configuration
    details.

6.  **Directory Indexing Enabled**

    Browsable directories such as /doc/, /test/, and /icons/ were
    identified.

7.  **phpMyAdmin Exposed**

    The /phpMyAdmin/ interface is publicly accessible and should be
    protected or restricted.

8.  **Cookie Security Weakness**

    The phpMyAdmin cookie was created without the HttpOnly flag.

### **Analysis**

These findings show weak web server hardening and poor application
security practices. Publicly exposed administration pages, directory
indexing, and verbose information disclosure increase the risk of
unauthorized access, reconnaissance, and targeted exploitation. This
directly relates to common web application risk categories identified by
OWASP, such as security misconfiguration, vulnerable or outdated
components.

## **Step 3: Focused Vulnerability Scanning**

### **Objective**

The objective of this step is to identify known vulnerabilities and
high-risk weaknesses using Nuclei based on the services discovered
during the Nmap scan. This provides stronger technical evidence,
including CVE references and severity ratings, for the later GRC
analysis.

### **Commands Executed**

nuclei -u <http://10.97.241.156> -o nuclei_web_scan.txt

nuclei -target 10.97.241.156 -o nuclei_full_scan.txt

The Nuclei scans produced several high-value findings:

#### **Web-Related Findings**

1.  **CVE-2012-1823** -- PHP CGI vulnerability

    This is a high-risk web vulnerability that may allow remote code
    execution through PHP CGI argument injection.

2.  **phpMyAdmin Panel Exposed**

    The phpMyAdmin interface is accessible from the web.

3.  **phpinfo.php Exposed**

    Sensitive PHP configuration information is publicly available.

4.  **HTTP TRACE Enabled**

    Confirms the web server allows TRACE requests.

5.  **Missing Security Headers**

    Several headers such as X-Frame-Options, X-Content-Type-Options, and
    Content-Security-Policy is missing.

#### **Network and Service Findings**

6.  **CVE-2011-2523** -- vsFTPd Backdoor

    This is a critical finding that indicates a known backdoor associated
    with vsFTPd 2.3.4.

7.  **FTP Anonymous Access and Weak Credentials**

    Anonymous FTP login is enabled, and weak/default credentials are
    accepted.

8.  **PostgreSQL Empty Password / Default Credentials**

    PostgreSQL accepts weak or empty credentials, which is a critical
    authentication weakness.

9.  **VNC Default Logins**

    The VNC service appears vulnerable to common default passwords such as
    password and password123.

10. **SMBv1 Supported**

    SMBv1 is detected, which is an outdated and insecure protocol.

11. **Outdated Software Exposure**

-   Apache HTTPD 2.2.8

-   PHP 5.2.4

-   Samba 3.0.20

-   PostgreSQL 8.3.1

### **Analysis**

The Nuclei results confirm that the target system contains a combination
of:

-   critical known vulnerabilities

-   weak authentication practices

-   insecure legacy protocols

-   exposed administrative services

-   poor hardening

These findings are highly valuable because they include CVE references
and severity ratings, which make them easier to map to risk levels and
treatment actions.

# **Phase 4: Advanced GRC Analysis -- Quantitative Risk & Treatment**

## **Objective**

The objective of this phase is to quantify the financial impact of
critical security risks and define appropriate treatment strategies
aligned with recognized frameworks such as the National Institute of
Standards and Technology SP 800-53 and industry risk management
practices.

**Step 1: Quantitative Risk Calculation (SLE & ALE)**

## **Method Used**

-   **SLE (Single Loss Expectancy) = AV × EF**

-   **ALE (Annualized Loss Expectancy) = SLE × ARO**

## **Quantitative Risk Table**

 | -------|------------------|-----------------------|-----------------|-------------|----------------|--------------|----------------|
 | **Risk |  **Asset Name**  |     **Threat          |    **AV (\$)**  |   **EF**    |   **SLE        |   **ARO**    |   **ALE        |
 | ID**   |                  |     Description**     |                 |    (\$)**   |                |    (\$)**    |                |
 | -------|------------------|-----------------------|-----------------|-------------|------ ---------|--------------|----------------|
 | R1     |  Customer Data   |      FTP Backdoor     |     3,000,000   |    0.6      |    1,800,000   |     0.5      |     900,000    |
 |        |  System          |     (CVE-2011-2523)   |                 |             |                |              |                |
 ---------|------------------|-----------------------|-----------------|-------------|----------------|--------------|----------------|
 | R2     |  Authentication  |     Weak Credentials  |    2,500,000    |    0.5      |    1,250,000   |      1.0     |     1,250,000  |
 |        |  System          |     (FTP, DB, VNC)    |                 |             |                |              |                |
 ---------|------------------|-----------------------|-----------------|-------------|----------------|--------------|----------------|
 | R3     |  Network         |     Telnet (Plaintext |    1,500,000    |    0.4      |    600,000     |      1.5     |      900,000   |
 |        |  Communication   |     Exposure)         |                 |             |                |              |                |
 ---------|------------------|-----------------------|-----------------|-------------|----------------|--------------|----------------|          
 | R4     |  Web Application |     PHP Vulnerability |    2,000,000    |    0.5      |    1,000,000   |       0.7    |      700,000   | 
 |        |                  |     (CVE-2012-1823)   |                 |             |                |              |                |
 ---------|------------------|-----------------------|-----------------|-------------|----------------|--------------|----------------|
 |  R5    | Database System  |    PostgreSQL         |   2,800,000     |   0.6       |   1,680,000    |       0.8    |      1,344,000 |
 |        |                  |     Default           |                 |             |                |              |                |
 |        |                  |     Credentials       |                 |             |                |              |                |
 | -------|------------------|-----------------------|-----------------|-------------|----------------|--------------|----------------|

# **Step 2: Risk Treatment Strategy**

## **Risk Treatment Table**

  -------------------------------------------------------------------------
  **Risk   **ALE       **Proposed      **Justification**
  ID**     (\$)**      Treatment**     
  -------- ----------- --------------- ------------------------------------
  R1       900,000     Mitigate        Patch vsFTPd, disable vulnerable FTP
                                       service

  R2       1,250,000   Mitigate        Enforce strong passwords and MFA

  R3       900,000     Avoid           Disable Telnet completely

  R4       700,000     Mitigate        Apply patches and secure PHP
                                       configuration

  R5       1,344,000   Mitigate        Remove default credentials and
                                       restrict DB access
  -------------------------------------------------------------------------

# **Step 3: Control Mapping (NIST SP 800-53)**

## **Control Mapping Table**

  ---------------------------------------------------------------------------
  **Risk   **Threat        **Proposed       **NIST     **Control
  ID**     Description**   Control**        Control    Description**
                                            ID**       
  -------- --------------- ---------------- ---------- ----------------------
  R1       FTP Backdoor    Patch Management SI-2       Flaw Remediation

  R1       FTP Backdoor    Service          CM-7       Least Functionality
                           Hardening                   

  R2       Weak            Multi-Factor     IA-2       Identification and
           Credentials     Authentication              Authentication

  R2       Weak            Password Policy  IA-5       Authenticator
           Credentials                                 Management

  R3       Telnet Exposure Disable Telnet   CM-7       Least Functionality

  R3       Telnet Exposure Encrypt          SC-13      Cryptographic
                           Communications              Protection

  R4       PHP             Input Validation SI-10      Information Input
           Vulnerability                               Validation

  R4       PHP             Web Filtering    SC-7       Boundary Protection
           Vulnerability                               

  R5       DB Default      Access Control   AC-6       Least Privilege
           Credentials                                 

  R5       DB Default      Account          AC-2       Account Management
           Credentials     Management                  
  ---------------------------------------------------------------------------

# **Phase 5: Business Impact Analysis (BIA) & Final Reporting**

## **Objective**

To clearly show how technical vulnerabilities affect business
operations, financial stability, and organizational reputation, in line
with best practices from the National Institute of Standards and
Technology and ISO risk management principles.

# **Step 1: Business Impact Analysis (BIA)**

## **BIA Table (Submission Ready)**

  ----------------------------------------------------------------------------------------------------
  **Risk   **Threat          **Affected       **RTO**   **RPO**   **Financial Impact **Non-Financial
  ID**     Description**     Business                             (Estimated)**      Impact**
                             Process**                                               
  -------- ----------------- ---------------- --------- --------- ------------------ -----------------
  R1       FTP Backdoor      Customer Data    24 hours  6 hours   \$900,000/year     Loss of sensitive
           (CVE-2011-2523)   Management                                              data, regulatory
                                                                                     penalties

  R2       Weak Credentials  User             12 hours  2 hours   \$1,250,000/year   Unauthorized
                             Authentication                                          access,
                             System                                                  reputational
                                                                                     damage

  R3       Telnet (Plaintext Internal         8 hours   1 hour    \$900,000/year     Data
           Exposure)         Communications                                          interception,
                                                                                     loss of trust

  R4       PHP Vulnerability Web Application  16 hours  4 hours   \$700,000/year     Website
           (CVE-2012-1823)   Services                                                compromise,
                                                                                     service
                                                                                     disruption

  R5       Database Default  Financial        24 hours  2 hours   \$1,344,000/year   Data breach,
           Credentials       Transactions                                            legal
                                                                                     consequences,
                                                                                     customer loss
  ----------------------------------------------------------------------------------------------------

## **Simple Explanation (What this table really means)**

-   **RTO (Recovery Time Objective)** → How long the business can
    survive downtime

-   **RPO (Recovery Point Objective)** → How much data loss is
    acceptable

Example:

-   R5 (Database risk):

    -   If the system is down for more than **24 hours → business fails**

    -   If more than **2 hours of data is lost → serious damage**

# **Step 2: Refined Executive Summary (Final Version)**

## **Executive Summary (Final Submission Version)**

**To:** IT Management\
**From:** GRC Audit Team\
**Date:** \[Insert Current Date\]\
**Subject:** Critical Risk Assessment Report -- Metasploitable
Development Server

### **1. Executive Summary**

A comprehensive security assessment identified multiple critical
vulnerabilities that expose the organization to significant financial
and operational risk. Several of these risks could result in annual
losses exceeding **\$1 million**, particularly those affecting database
systems and authentication controls. These weaknesses indicate
non-compliance with established security frameworks such as the NIST
Cybersecurity Framework and industry best practices.

### **2. Key Findings and Business Risks**

-   **Critical Risk -- Full System Compromise:**

The FTP service contains a known backdoor vulnerability (CVE-2011-2523),
allowing unauthorized remote access. This creates a direct path to total
system compromise.

-   **High Risk -- Database Exposure:**

Default credentials in the PostgreSQL database allow attackers to gain
full access to sensitive financial and operational data. This represents
the highest financial risk, with an estimated annual loss of **\$1.34
million**.

-   **High Risk -- Weak Authentication Controls:**

Multiple services allow weak or default credentials, significantly
increasing the risk of unauthorized access and data breaches.

-   **High Risk -- Unsecured Communication:**

The use of Telnet exposes credentials in plaintext, making interception
easy for attackers.

-   **High Risk -- Web Application Vulnerabilities:**

The web server is outdated and vulnerable to known exploits, increasing
the likelihood of web-based attacks.

### **3. Business Impact**

If exploited, these vulnerabilities could result in:

-   Major financial losses exceeding **\$1 million annually**

-   Disruption of critical business services

-   Loss of customer trust and reputation

-   Regulatory penalties due to data breaches

-   Long-term operational instability

### **4. Recommended Actions**

-   **Immediate Isolation:**\
    Remove the affected system from the production network until
    remediation is completed.

-   **Mitigation:**

    -   Apply patches to vulnerable services

    -   Remove default credentials and enforce strong authentication

    -   Disable insecure services such as Telnet

    -   Secure web applications through updates and configuration
        hardening

-   **Strategic Improvements:**

    -   Implement continuous vulnerability management

    -   Align systems with CIS Controls and NIST standards

    -   Conduct regular security audits and monitoring

### **5. Return on Security Investment (ROSI)**

Investing in proper security controls will significantly reduce the
annualized loss expectancy (ALE). For example:

-   Fixing database vulnerabilities alone can reduce potential losses by
    over **\$1.3 million annually**

-   Strengthening authentication controls reduces repeated breach risks

This demonstrates that security investment is not a cost, but a
**financial risk reduction strategy**

# **Conclusion**

This work successfully bridged the gap between technical vulnerability
assessment and enterprise risk management. It showed that security risks
are not just technical problems but business issues that can lead to
significant financial loss, operational disruption, and reputational
damage.

The identification of critical vulnerabilities such as default
credentials, outdated software, and insecure communication protocols
demonstrates the importance of proper system configuration and
continuous monitoring. When these weaknesses are left unaddressed, they
significantly increase the organization's attack surface and exposure to
threats.

Through quantitative risk analysis and Business Impact Analysis, the
study provided clear evidence of how security failures translate into
real business consequences. This supports the need for proactive
investment in security controls, which can reduce long-term financial
losses and improve organizational resilience.

The implementation of risk treatment strategies aligned with established
frameworks ensure that security efforts are structured, measurable, and
effective. Ultimately, this lab reinforces that effective cybersecurity
is achieved not only through tools, but through proper governance, risk
awareness, and continuous improvement.


# **References** 

International Organization for Standardization. (2022). *ISO/IEC 27001:
Information security, cybersecurity, and privacy protection ---
Information security management systems --- Requirements*. ISO.

National Institute of Standards and Technology. (2024). *Framework for
improving critical infrastructure cybersecurity (NIST Cybersecurity
Framework)*. <https://www.nist.gov/cyberframework>

National Institute of Standards and Technology. (2020). *Security and
privacy controls for information systems and organizations (NIST SP
800-53 Rev. 5)*.
<https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final>

Center for Internet Security. (2021). *CIS Critical Security Controls
v8*. <https://www.cisecurity.org/controls>

Payment Card Industry Security Standards Council. (2022). *Payment Card
Industry Data Security Standard (PCI DSS) Version 4.0*.
[https://www.pcisecuritystandards.org](https://www.pcisecuritystandards.org/?utm_source=chatgpt.com)

OWASP Foundation. (2021). *OWASP Top 10: The ten most critical web
application security risks*.
[https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/?utm_source=chatgpt.com)
