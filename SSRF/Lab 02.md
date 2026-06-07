## Title
Server-Side Request Forgery (SSRF) in Link URL


## Summary
I found a Server-Side Request Forgery (SSRF) vulnerability in Link URL section. The parameter is vulnerable.


## Affected URL
https://kzlabs.in/602.php


## Steps to Reproduce
1. Open the following url https://kzlabs.in/602.php
2. Navigate to Webhooks section and enter burp collaborator payload in Link URL, click on Generate preview.
3. You will see source IP address of the web application


## Proof of Concept Request

<img width="3000" height="1584" alt="image" src="https://github.com/user-attachments/assets/cd302890-ec6d-4a5c-934d-63f293824415" />

<img width="3000" height="1290" alt="Screenshot 2026-06-07 222435" src="https://github.com/user-attachments/assets/9db63757-39ca-4e4e-845e-ed550fa9f97a" />

<img width="3000" height="1714" alt="image" src="https://github.com/user-attachments/assets/82540c70-9aa5-4a80-9d92-c00204e2085b" />

<img width="2996" height="1350" alt="image" src="https://github.com/user-attachments/assets/786ed8af-0773-479b-88ec-2cccf42ea357" />


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
