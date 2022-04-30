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
Log4j is a logging tool used in many Java-based applications.  In December 2021, Apache disclosed a remote code execution (RCE) vulnerability where an attacker with permission to modify the logging configuration file can construct and execute malicious code. According to Apache, Log4j2 versions 2.0-beta7 through 2.17.0 are vulnerable to a RCE vulnerability.  The NIST National Vulnerability Database assigned the highest CVSS score, 10.0 out of 10.0, for this vulnerability. ** The only way to fully 
