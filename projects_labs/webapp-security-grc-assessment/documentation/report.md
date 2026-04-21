**Web Application Security Assessment and GRC Risk Analysis**

**(OWASP Top 10 Evaluation of a Legacy Application Environment)**

**Prepared By:**

**Ayuba Amadi**

**Program:**

**GRC Engineering**

**International Cybersecurity and Digital Forensics Academy (ICDFA)**

**Course: GRC-103**

**19/04/2026**

**Executive Summary**

This report presents the findings of a comprehensive web application
security assessment conducted on a legacy application environment hosted
on the OWASP Broken Web Applications (BWA) platform. The objective of
the assessment was to identify critical security vulnerabilities,
evaluate their potential impact on business operations, and assess
compliance with established security frameworks, including the OWASP Top
10 (2021), NIST Cybersecurity Framework, and PCI DSS.

The assessment was carried out using a combination of automated scanning
techniques and manual testing methodologies. Initial reconnaissance
activities identified multiple exposed services and web applications,
including BodgeIt Store and WebGoat. These applications were further
analyzed using Burp Suite Professional to uncover vulnerabilities that
are not typically detected through automated tools alone.

The assessment revealed several high-risk vulnerabilities, most notably
broken access control mechanisms, transmission of sensitive data in
plaintext, and weak authentication controls. These issues expose the
system to unauthorized access, credential compromise, and potential data
breaches. Additionally, while initial testing for injection
vulnerabilities did not confirm successful exploitation, gaps in input
validation suggest the possibility of further undiscovered weaknesses.

From a governance, risk, and compliance perspective, these findings
indicate significant deficiencies in secure application development
practices and a lack of adherence to industry-standard security
controls. The absence of fundamental protections such as encryption,
proper access restrictions, and robust authentication mechanisms
highlights weaknesses in the organization's Secure Development Lifecycle
(SDLC).

Overall, the environment presents a high-risk security posture and
requires immediate remediation. This report provides actionable
recommendations aimed at mitigating identified risks, improving security
controls, and aligning development practices with recognized industry
standards

# **Phase 1: Discovery and Reconnaissance**

## **Objective**

The objective of this phase is to identify active systems, enumerate
exposed services, and discover accessible web applications to define the
system's attack surface.

# **Step 1: Target Discovery**

## **Command Executed**

ping -c 4 10.124.186.214

## **Purpose of the Command**

The ping command is used to verify whether the target system is
reachable over the network. It sends ICMP echo requests and waits for
responses.

This step is essential because:

-   It confirms the target is active

-   It validates network connectivity before scanning

-   It prevents wasting time scanning unreachable systems

## **Result and Interpretation**

The system responded to all four ICMP requests with no packet loss. This
confirms that:

-   The host is active

-   The network path is stable

-   The system is ready for further assessment

![](./media/184e3737a9d2d15290e40020978a505c154c687c.png){width="7.1875in"
height="3.0520833333333335in"}

# **Step 2: Service Enumeration (Nmap Scan)**

## **Command Executed**

sudo nmap -sV -sC -O -p- -oA initial_scan 10.124.186.214

## **Purpose of the Command**

This is not just a scan; it is a **comprehensive enumeration process**.
Each flag has a specific role:

-   -sV: Detects service versions (critical for identifying
    vulnerabilities)

-   -sC: Runs default scripts (reveals misconfigurations)

-   -O: Attempts OS detection

-   -p-: Scans all 65,535 ports (ensures nothing is missed)

-   -oA: Outputs results in three formats (.nmap, .xml, .gnmap)

This command is used because:

-   GRC analysis depends on **accurate asset visibility**

-   Vulnerabilities are tied to **specific versions**

-   Compliance violations often come from **unnecessary or exposed
    services**

![](./media/a214542ba170b8a3547b5e4dbd41e3737978cc4a.png){width="7.1875in"
height="5.90625in"}

## **Result and Interpretation**

The scan revealed multiple open ports and services. These are not just
technical findings; they represent **exposure points**.

### **Key Services Identified**

  -----------------------------------------------------------------------------
  **Port**   **Service**   **Version**     **Risk Implication**
  ---------- ------------- --------------- ------------------------------------
  80         HTTP          Apache 2.2.14   Outdated, vulnerable web server

  8080       HTTP          Tomcat          Application layer attack surface

  8081       HTTP          Jetty 6.1.25    Legacy web service exposure

  22         SSH           OpenSSH 5.3     Weak or outdated encryption support

  443        HTTPS         Expired         Broken trust and encryption
                           Certificate     

  139/445    SMB           Samba           Weak authentication controls

  143        IMAP          Courier         Legacy service exposure

  5001       Java Object   Unknown         Possible insecure deserialization
  -----------------------------------------------------------------------------

## **Security Interpretation**

This system exposes multiple web services and legacy protocols. From a
governance and compliance standpoint, this indicates:

-   Lack of proper service hardening

-   Poor patch management practices

-   Expanded attack surface beyond business necessity

This directly relates to:

-   **CIS Control 9** (Limitation of Network Services)

-   **NIST CSF PR.IP-1** (Baseline Configuration Management)

# **Step 3: Conversion of Nmap XML to HTML Report**

## **Command Executed**

xsltproc -o initial_scan_report.html /usr/share/nmap/nmap.xsl
initial_scan.xml

![](./media/707700138ab5efeb4eda1177b99bde12a07a6a33.png){width="7.1875in"
height="0.6354166666666666in"}

**Purpose of the Command**

Nmap produces raw output that is not suitable for management reporting.
The XML file is structured but not readable for non-technical
stakeholders.

This command converts:

-   XML → HTML (human-readable format)

This is important because:

-   GRC reporting requires **clear communication**

-   Stakeholders need **visual and structured reports**

-   It supports **audit documentation and evidence presentation**

The result is a structured HTML report that:

-   Organizes ports and services clearly

-   Improves readability

-   Can be shared with management

![](./media/6e080d708d79b42ce8b155cdcd66450bfd766130.png){width="7.1875in"
height="4.479166666666667in"}

![](./media/3acdfabf19b2303eda1703a866ca2c573972ab3d.png){width="7.1875in"
height="2.65625in"}

# ![](./media/63079519c690ef572f850c22d2201917b924a025.png){width="7.1875in" height="2.7083333333333335in"}

# **Step 4: Application Discovery**

## **Action Performed**

Accessed the target system via web browser:

<http://10.124.186.214>

![](./media/b210cf5ecf3cc01c3aac7428089cc0dd6ff1383d.png){width="6.53125in"
height="4.489583333333333in"}

## **Purpose of the Action**

This step identifies:

-   Available web applications

-   Entry points for testing

-   Application-level attack surface

## **Findings**

The system hosts multiple vulnerable applications, including:

-   WebGoat

-   BodgeIt Store

-   DVWA

These applications are intentionally vulnerable and will be used for:

-   OWASP Top 10 testing

-   Manual vulnerability validation

![](./media/26e86b9da80ff91c946aa4920c85c512c805effd.png){width="7.1875in"
height="5.229166666666667in"}

![](./media/64ccb9f068a43f90263c2f86f85d2767d3620f43.png){width="7.0in"
height="4.052119422572178in"}

![](./media/fdad274ab20dddcbabd1833ec426bdff5a121a79.png){width="6.895833333333333in"
height="5.104166666666667in"}

# **Phase 2: Tool Configuration and Automated Scanning**

## **Objective**

The objective of this phase is to configure Burp Suite Professional as
the main interception and assessment tool, route browser traffic through
it, populate the application structure for analysis, and perform an
initial automated scan to identify low-hanging web application security
issues. This phase is important because it establishes the technical
visibility required for both manual testing and structured GRC analysis.

## **Step 4: Configuring Burp Suite Professional**

### **Purpose of This Step**

Burp Suite Professional acts as an interception proxy between the
browser and the target web application. This means every request sent by
the browser and every response returned by the server can be captured,
reviewed, and modified. In practical terms, this gives the assessor
visibility into how the application works, how user input is handled,
and where weaknesses may exist.

### **Actions Performed**

Burp Suite Professional was launched, and a temporary project was used
for the assessment session. The browser proxy was then configured so
that all web traffic would be routed through Burp Suite using the local
listener on 127.0.0.1 and port 8080.

After the proxy settings were configured, Burp Intercept was turned on.
The target application was then opened in the browser and requests were
forwarded through Burp one by one. This allowed Burp Suite to observe
and register the application structure inside the **Target** site map.
Once the site map was populated, Intercept was turned off so that
browsing could continue normally while traffic was still monitored in
the background.

![](./media/83d2f9e04b81020508ff40b1f225f394380fc3f0.png){width="7.1875in"
height="4.885416666666667in"}

### **What This Configuration Achieved**

This configuration achieved three important things.

First, it confirmed that browser traffic was successfully routed through
Burp Suite.\
Second, it allowed the target applications and paths to be discovered
and recorded in the site map.

Third, it created a reliable base for both passive scanning and later
manual testing using tools such as Repeater and Intruder.

### **Observations**

The browser-to-Burp routing was successful. Burp was able to receive the
traffic and begin live auditing of the application. This confirms that
the environment was correctly configured for controlled web application
testing.

![](./media/fe6a4738d8539585266307defdabb8b2b0335736.png){width="7.1875in"
height="5.458333333333333in"}

**Step 5: Automated Passive and Active Scanning**

### **Purpose of This Step**

After the site map was populated, Burp Suite's scanner was used to
perform an initial automated assessment. The purpose of this step was to
identify obvious or common weaknesses before starting detailed manual
testing.

Automated scanning does not replace manual testing, but it is useful for
quickly identifying issues such as missing security headers, insecure
cookie settings, reflected cross-site scripting, unencrypted
communications, and potential injection points. From a GRC perspective,
this step supports early identification of control failures and helps
prioritize areas that require deeper validation.

### **Actions Performed**

Inside the **Target** site map, the host corresponding to the target
application was selected. A scan was launched using the built-in scan
option. The configuration was reviewed before execution, and the task
was then started.

The Burp Dashboard was used to monitor progress. Burp carried out
passive checks while also performing live crawling and audit activities
in the background. During this process, the scanner began identifying
issues of different severity levels.

![](./media/79f2cd7b77adb622d1fba69548a4ced82d5dd5e4.png){width="7.1875in"
height="5.260416666666667in"}

### **What the Automated Scan Revealed**

The automated scan produced a number of early findings. These included
issues such as:

-   unencrypted communications

-   cookies without the HttpOnly flag

-   missing or weak client-side protections

-   reflected cross-site scripting

-   file path manipulation

-   SQL injection indicators

-   HTTP TRACE method enabled

-   weak or invalid TLS configuration

These findings are important because they show that the application
contains weaknesses that map directly to recognized web security risk
categories. The scan does not by itself prove every issue beyond doubt,
but it provides strong leads for targeted manual verification.

### **Security & GRC Interpretation**

This stage shows the value of combining technical testing with risk
thinking. The automated scanner is not just listing flaws; it is
identifying possible failures in application security controls.

For example:

Unencrypted communication suggests failure to protect sensitive data in
transit.\
Cookies without secure flags suggest weak session handling controls.\
Reflected cross-site scripting indicates inadequate input handling and
output encoding.\
SQL injection findings suggest poor server-side validation and
potentially serious data exposure risk.

These results support later mapping to OWASP Top 10 categories and
relevant compliance requirements, especially where customer data,
authentication, and web application integrity are concerned.

### **Observations**

The Burp scan produced both passive and active findings. The second scan
view showed multiple higher-risk issues, including reflected cross-site
scripting, file path manipulation, and SQL injection indicators. This
confirms that the target environment is suitable for deeper manual
validation in the next phase.

# **Phase 3: Manual Testing Against OWASP Top 10**

## **Overview**

This phase involved controlled manual testing of selected web
applications hosted on the OWASP Broken Web Applications (BWA)
environment. The purpose was to validate the presence of high-impact
vulnerabilities aligned with the OWASP Top 10 (2021), beyond what
automated tools can reliably detect.

Unlike automated scanning, manual testing allows for deeper inspection
of application logic, authentication flows, and access control
mechanisms. Each test was conducted through controlled interaction with
the application and supported by traffic analysis using Burp Suite
Professional

# **Step 6: A01 -- Broken Access Control (BodgeIt Store)**

## **Objective**

To determine whether the application properly enforces authorization
controls by restricting access to administrative resources based on user
roles.

## **Test Execution**

The test began by interacting with the BodgeIt Store application as a
standard user. A new account was created and used to log into the
system. Normal application usage was simulated, including browsing
products and adding items to the shopping cart, to establish a
legitimate session context.

![](./media/caa5097581806ddf21ecc81d77fdb2c79cb26f1f.png){width="7.1875in"
height="4.177083333333333in"}

After authentication, attention shifted to identifying restricted
endpoints. Without performing any privilege escalation or role
modification, a direct request was made to the administrative interface
using the URL:

<http://10.124.186.214/bodgeit/admin.jsp>

This approach tests whether the application relies solely on front-end
controls (such as hidden links) rather than enforcing backend
authorization checks

## **Observed Behaviour**

The administrative interface was successfully loaded and displayed
sensitive internal data, including:

-   User account details

-   Assigned roles (including administrative roles)

-   Transactional and basket data

No authentication or authorization barrier was triggered when accessing
this resource.

![](./media/714b2720ae5657d1959d15f186392421d6adad08.png){width="7.1875in"
height="5.8125in"}

## **Technical Analysis**

This behaviour confirms that the application fails to enforce
server-side authorization controls. The absence of role validation
allows any authenticated use or potentially even unauthenticated users
to access privileged functionality.

This is not a misconfiguration. It is a **fundamental design failure**
in access control enforcement.

**Risk Evaluation**

This vulnerability introduces a direct path to privilege escalation. An
attacker does not need to exploit complex vulnerabilities; they only
need to know or guess the administrative endpoint.

Impact includes:

-   Full disclosure of sensitive user data

-   Unauthorized administrative actions

-   Manipulation of application state

-   Potential complete system compromise

## **GRC Perspective**

This issue represents a direct violation of:

-   Principle of Least Privilege

-   NIST SP 800-53 AC-6 (Least Privilege)

-   PCI DSS 7.2.1 (Access Control Enforcement)

From a governance standpoint, this indicates a failure in secure
application design and lack of access control validation during
development and testing phases.

# **Step 7: A02 -- Cryptographic Failures (WebGoat)**

## **Objective**

To verify whether sensitive information, particularly authentication
credentials, is transmitted securely across the network.

## **Test Execution**

The WebGoat application was accessed through the browser, and a login
attempt was performed. Burp Suite Proxy was configured to intercept and
log all HTTP traffic between the browser and the target server.

![](./media/26e86b9da80ff91c946aa4920c85c512c805effd.png){width="7.1875in"
height="6.041666666666667in"}The HTTP history within Burp Suite was then
analysed, with a focus on POST requests carrying authentication data.

**Observed Behaviour**

Captured HTTP requests revealed that user credentials were transmitted
in plaintext within the request body. Specifically:

-   The username and password were visible in clear text

-   No encryption (HTTPS) was enforced

-   No obfuscation or hashing was applied at the transport layer

![](./media/8521d110a4d87ac904a1da5d2626e968a9beb731.png){width="7.135416666666667in"
height="5.78125in"}

![](./media/adb2f9107e7ff72d33c8a014830121e5bcd1c858.png){width="6.885416666666667in"
height="4.0in"}

## **Technical Analysis**

This indicates that the application does not enforce secure transport
mechanisms such as HTTPS/TLS. Any attacker with access to the network
could intercept and read sensitive authentication data.

This is not a minor issue it is a **critical cryptographic failure**.

## **Risk Evaluation**

The exposure of plaintext credentials introduces:

-   Immediate credential compromise

-   Account takeover risk

-   Lateral movement across systems if credentials are reused

## **GRC Perspective**

This violates core data protection requirements, including:

-   PCI DSS 4.1 (Encryption of data in transit)

-   NIST CSF PR.DS-2 (Protect Data-in-Transit)

From a compliance standpoint, this alone could fail an audit.

# **Step 8: A03 -- Injection (SQL Injection Testing -- BodgeIt Search)**

## **Objective**

To assess whether the application is vulnerable to SQL Injection through
improper input validation.

## **Test Execution**

The search functionality of the BodgeIt Store was selected as a
potential injection point. User input was intercepted using Burp Suite
and forwarded to the Repeater tool for controlled testing.

Several standard SQL injection payloads were tested, including:

-   \' (to trigger syntax errors)

-   \' OR \'1\'=\'1 \-- (authentication bypass logic)

-   \' UNION SELECT \... (data extraction attempts)

![](./media/77a8b3fb6d9fa4845531c9c36b7506f1ab33a049.png){width="7.1875in"
height="2.3125in"}![](./media/dc60f2e7b7732eb588eb9765c529c27f74507adc.png){width="7.1875in"
height="2.3125in"}![](./media/7fc975dbc003af48a45703351e9f25c3e7d5409a.png){width="7.1875in"
height="2.3125in"}**Observed Behaviour**

All injection attempts resulted in HTTP 404 responses, indicating that
the targeted endpoint (home.jsp) was not valid or not processing the
injected parameters.

![](./media/360669de29ff8053ba3b9095735baaa539b2cbae.png){width="7.1875in"
height="4.802083333333333in"}

![](./media/48fff3bd00c21c7711c8875d635af64a0d4bb103.png){width="7.1875in"
height="4.4375in"}

## **Technical Analysis**

Here is where you need to be sharp:

The failure of these payloads does **not confirm the absence of SQL
injection vulnerabilities**.

It only confirms that:

-   The tested endpoint is not vulnerable

-   Or the injection point was incorrectly targeted

## **Risk Evaluation**

-   No confirmed SQL injection on this endpoint

-   Potential blind spots remain in other application inputs

## **GRC Perspective**

Injection remains one of the highest-risk categories under OWASP Top 10.
Even unsuccessful tests must be documented because they demonstrate due
diligence in control validation.

# **Step 9: A07 -- Identification and Authentication Failures**

## **Objective**

To evaluate the robustness of authentication mechanisms and resistance
to brute-force attacks

## **Test Execution**

The login functionality of the BodgeIt Store was tested using:

1.  Common weak credential combinations

2.  Automated password testing via Burp Suite Intruder

The login request was intercepted and configured for a Sniper attack,
targeting the password parameter with a list of commonly used passwords.

![](./media/7c2cd16aad0cc83da16de811e16b05f9bce6d484.png){width="7.1875in"
height="4.645833333333333in"}

![](./media/92a30c7a8aa20174c90a3e8b4eafce49bb6e264b.png){width="7.1875in"
height="4.593777340332458in"}

**Observed Behaviour**

The application responded with HTTP 200 status codes for all attempts;
however, response lengths varied across different payloads.

This variation suggests that the application processes inputs
differently depending on credential validity, potentially indicating
successful authentication attempts or distinguishable responses

## **Technical Analysis**

The absence of account lockout mechanisms and consistent response
handling indicates weak authentication controls. The system does not
effectively mitigate brute-force attempts.

## **Risk Evaluation**

-   High likelihood of unauthorized access

-   Increased attack surface for credential stuffing

-   Potential initial access vector for attackers

## **GRC Perspective**

Violates:

-   CIS Control 5 (Account Management)

-   NIST CSF PR.AC-1 (Identity Management and Access Control)

**Conclusion**

The results of this assessment highlight critical security weaknesses
within the evaluated web application environment, primarily stemming
from the absence of fundamental security controls rather than
sophisticated attack vectors. The identified vulnerabilities, including
broken access control, plaintext transmission of sensitive data, and
weak authentication mechanisms, significantly increase the likelihood of
unauthorized access, data breaches, and system compromise.

These findings underscore the importance of integrating security into
every phase of the application development lifecycle. The current state
of the system reflects a lack of effective governance and insufficient
implementation of security best practices, which are essential for
protecting organizational assets and maintaining operational integrity.

From a GRC standpoint, the assessment demonstrates clear misalignment
with key security frameworks such as OWASP Top 10, NIST Cybersecurity
Framework, and PCI DSS. Compliance with these standards is not only a
regulatory requirement but also a critical component of risk management
and organizational resilience.

To address these challenges, it is essential for the organization to
adopt a proactive and structured approach to security. This includes
implementing secure coding practices, enforcing strong authentication
and access control mechanisms, ensuring encryption of sensitive data in
transit, and integrating security testing into the development and
deployment pipeline. Additionally, continuous training and awareness for
development teams will play a vital role in preventing the recurrence of
similar vulnerabilities.

In conclusion, effective risk management requires more than the use of
security tools; it demands strong governance, well-defined processes,
and a security-focused culture. Addressing the issues identified in this
assessment will significantly improve the organization's security
posture and reduce its exposure to evolving cyber threats.
