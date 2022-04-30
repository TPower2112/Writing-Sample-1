# Log4j: CVE-2021-44228
#### Summary of Log4j Vulnerability & Mitigations


## Table of Contents
1. [Executive Summary](#execsum)
2. [Identification of Vulnerable Endpoints and Services](#vulnend)
3. [Mitigations](#mits)
    
    A. [Block at the Border](#borderblock)
    
    B. [Install CrowdStrike on Server Endpoints](#installcs)
    
    C. [Place Vulnerable Enterprise Apps Behind the F5](#vulnf5)

4. [Resources and Additional Reading](#resources)

## Executive Summary <a name="execsum"></a>
Log4j is a logging tool used in many Java-based applications.  In December 2021, Apache disclosed a remote code execution (RCE) vulnerability where an attacker with permission to modify the logging configuration file can construct and execute malicious code. According to Apache, Log4j2 versions 2.0-beta7 through 2.17.0 are vulnerable to a RCE vulnerability.  The NIST National Vulnerability Database assigned the highest CVSS score, 10.0 out of 10.0, for this vulnerability. **The only way to fully mitigate this vulnerability is to upgrade to Log4j 2.3.2(for Java 6), 2.12.4(for Java 7), or 2.17.1(for Java 8 and later).**

Threat actors are exploiting this vulnerability in the wild on internet-facing systems to deploy ransomware.  Patching vulnerable endpoints must be done in a timely manner.  The mitigations described below, buy a limited amount of time for teams to develop and test patching plans, but they are not long-term solutions.

## Identification of Vulnerable Endpoints and Services <a name="vulnend"></a>
The biggest challenge is identifying vulnerable endpoints. Each department needs to contact their respective vendor(s) to determine if their applications and services are vulnerable.  To assist with identifying vulnerable services, Logpresso is a command-line tool for CVE-2021-44228 scanning.

## Mitigations <a name="mits"></a>
### A. Block at the Border <a name="borderblock"></a>
Security Operations enabled snort rules at the border internet firewall to block inbound attempts to exploit this vulnerability.  These rules block inbound internet traffic on non-encrypted common web ports, such as HTTP.  These rules will not provide any protection for a site running HTTPS as the traffic cannot be intercepted and decrypted by the border internet firewall. Exploits for this vulnerability are quite specific, and the chance for false positives is very low.
### B. Install CrowdStrike on Server Endpoints <a name="installcs"></a>
Endpoint detection and response software is required on all endpoints per [Information Security Standard U7](https://cio.ubc.ca/information-security-standards/U7). Security Operations recommends installing the CrowdStrike Falcon sensor on all server endpoints, since the sensor provides visibility into vulnerable endpoints and prevents exploitation from threat actors. 
