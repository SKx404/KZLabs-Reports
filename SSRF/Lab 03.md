## Title
Server-Side Request Forgery (SSRF) in Run Health Check


## Summary
I found a Server-Side Request Forgery (SSRF) vulnerability in Run Health Check section. The parameter is vulnerable.


## Affected URL
https://kzlabs.in/602.php


## Steps to Reproduce
1. Open the following url https://kzlabs.in/602.php
2. Navigate to Webhooks section and enter burp collaborator payload in Run Health Check
3. You will see source IP address of the web application


## Proof of Concept Request

<img width="2996" height="1698" alt="image" src="https://github.com/user-attachments/assets/a3d5c541-bb39-499a-ace9-d6d338ca0666" />

<img width="2996" height="1350" alt="Screenshot 2026-06-07 223847" src="https://github.com/user-attachments/assets/84e4ab0c-e760-4891-8d0c-221c9d70aea4" />


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
