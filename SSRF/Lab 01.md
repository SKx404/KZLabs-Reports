## Title
Server-Side Request Forgery (SSRF) in Webhooks


## Summary
I found a Server-Side Request Forgery (SSRF) vulnerability in Webhooks section. The parameter is vulnerable.


## Affected URL
https://kzlabs.in/601.php


## Steps to Reproduce
1. Open the following url https://kzlabs.in/601.php
2. Navigate to Webhooks section and enter burp collaborator payload in webhooks, click on send test event
3. You will see source IP address of the web application


## Proof of Concept Request

<img width="2990" height="1692" alt="image" src="https://github.com/user-attachments/assets/ef9e32fe-26ed-4b26-af41-a71300675d55" />

<img width="3000" height="1290" alt="image" src="https://github.com/user-attachments/assets/fbd9df64-4d56-4937-835c-a9e2e8beaca8" />

<img width="3000" height="1692" alt="image" src="https://github.com/user-attachments/assets/69a567a4-3e06-4864-b566-d97e209cc222" />

<img width="2992" height="1262" alt="image" src="https://github.com/user-attachments/assets/977d7cf3-5711-455d-ac96-5244b30936ce" />


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
