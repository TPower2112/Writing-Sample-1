# Log4j: CVE-2021-44228
#### Summary of Log4j Vulnerability & Mitigations


## Table of Contents
1. [Executive Summary](#execsum)
2. [Identification of Vulnerable Endpoints and Services](#vulnend)
3. [Mitigations](#mits)
    
    A. [Block at the Border](#borderblock)
    
    B. [Install Endpoint Detection & Response (EDR) on Server Endpoints](#installcs)
    
    C. [Place Vulnerable Enterprise Apps Behind the F5](#vulnf5)

4. [Resources and Additional Reading](#resources)

## Executive Summary <a name="execsum"></a>
Log4j is a logging tool used in many Java-based applications.  In December 2021, Apache disclosed a remote code execution (RCE) vulnerability where an attacker with permission to modify the logging configuration file can construct and execute malicious code. According to Apache, Log4j2 versions 2.0-beta7 through 2.17.0 are vulnerable to a RCE vulnerability.  The NIST National Vulnerability Database assigned the highest CVSS score, 10.0 out of 10.0, for this vulnerability. **The only way to fully mitigate this vulnerability is to upgrade to Log4j 2.3.2(for Java 6), 2.12.4(for Java 7), or 2.17.1(for Java 8 and later).**

Threat actors are exploiting this vulnerability in the wild on internet-facing systems to deploy ransomware.  Patching vulnerable endpoints must be done in a timely manner.  The mitigations described below, buy a limited amount of time for teams to develop and test patching plans, but they are not long-term solutions.

## Identification of Vulnerable Endpoints and Services <a name="vulnend"></a>
The biggest challenge is identifying vulnerable endpoints. Each department needs to contact their respective vendor(s) to determine if their applications and services are vulnerable.  To assist with identifying vulnerable services, [Logpresso](https://github.com/logpresso/CVE-2021-44228-Scanner) is a command-line tool for CVE-2021-44228 scanning.

## Mitigations <a name="mits"></a>
### A. Block at the Border <a name="borderblock"></a>
Network administrators can enabled snort rules at the border internet firewall to block inbound attempts to exploit this vulnerability.  These rules block inbound internet traffic on non-encrypted common web ports, such as HTTP.  These rules will not provide any protection for a site running HTTPS as the traffic cannot be intercepted and decrypted by the border internet firewall. Exploits for this vulnerability are quite specific, and the chance for false positives is very low.
### B. Install EDR on Server Endpoints <a name="installcs"></a>
EDR software is required on all endpoints per [Information Security Standard U7](https://cio.ubc.ca/information-security-standards/U7). Security Operations recommends installing EDR on all server endpoints first, since the sensor provides visibility into vulnerable endpoints and prevents exploitation from threat actors. 

### C. Place Vulnerable Enterprise Apps Behind the F5 <a name="vulnf5"></a>
System owners may need time to work with vendors to patch CVE-2021-44228. System owners with vulnerable services can contact the application security team to build a WAF (web application firewall) signature to protect web traffic between an application and the internet. The F5 monitors and filters malicious web traffic as the JNDI injection signatures related to this vulnerability.

## Resources and Additional Reading <a name="resources"></a>
[Apache Migration from Loj4j 1 to Log4j2](https://logging.apache.org/log4j/2.x/manual/migration.html)

[Apache Security Vulnerability - Log4j](https://logging.apache.org/log4j/2.x/security.html)

[CrowdStrike Log4j Learning Center](https://www.crowdstrike.com/log4j2/)

[CVE-2021-44228](https://cve.mitre.org/cgi-bin/cvename.cgi?name=cve-2021-44228)

[CVE-2021-44228-NVD](https://nvd.nist.gov/vuln/detail/CVE-2021-44228)

[F5 and Log4j2 Vulnerability Mitigation](https://support.f5.com/csp/article/K59329043)

[Logpresso Vulnerability Scanner](https://github.com/logpresso/CVE-2021-44228-Scanner)

[Microsoft Security Response Center - Log4j2](https://msrc-blog.microsoft.com/2021/12/11/microsofts-response-to-cve-2021-44228-apache-log4j2/)

[MSRC-Guidance for preventing, detecting, and hunting Log4j2](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/)
