## Analyst Notes

### Key Observations
- FTP allows anonymous login
- Telnet transmits credentials in plaintext
- Multiple outdated services detected (Apache, MySQL, PostgreSQL)

### Challenges Encountered
- Nmap OS scan initially failed due to missing root privileges
- Nikto installation required fixing repository connectivity issues

### Interpretation
The system is intentionally vulnerable, exposing multiple high-risk services and weak configurations that significantly increase attack surface.
