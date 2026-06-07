## Title
Server-Side Request Forgery (SSRF) in Instances


## Summary
I found a Server-Side Request Forgery (SSRF) vulnerability in Instances section. The parameter Meta data url is vulnerable.


## Affected URL
https://kzlabs.in/606.php


## Steps to Reproduce
1. Open the following url https://kzlabs.in/606.php
2. Enter burp collaborator payload in Meta data url and click on Fetch
3. You will see source IP address of the web application


## Proof of Concept Request

<img width="2998" height="1702" alt="image" src="https://github.com/user-attachments/assets/38b01f5a-cea1-494f-a252-2ad78cac4c97" />

<img width="2996" height="1350" alt="Screenshot 2026-06-07 223847" src="https://github.com/user-attachments/assets/796d81ad-d83e-4c58-bc6f-04018dc927d4" />


## SSRF Impact

- It allows attackers to make arbitrary requests from the vulnerable server
- It may lead to unauthorized access to internal applications and network services
- It allows attackers to enumerate internal infrastructure and perform network reconnaissance
- It may result in disclosure of sensitive information from internal systems
- It can potentially expose cloud metadata and credentials, leading to further compromise of the environment


## SSRF Remediation

- Restrict outbound requests using a strict allowlist of approved domains and destinations
- Block requests to private, loopback, link-local, and internal IP address ranges
- Prevent access to cloud metadata services and sensitive internal resources
- Disable or validate redirects to prevent allowlist bypasses
- Implement network-level egress filtering and monitoring of outbound requests
