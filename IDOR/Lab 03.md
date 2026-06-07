## Title
Insecure Direct Object Reference (IDOR) in Lab results


## Summary
I found an Insecure Direct Object Reference (IDOR) vulnerability in lab results section. The id paramter is vulnerable to IDOR in following url


## Affected URL
https://kzlabs.in/703.php


## Steps to Reproduce
1. Login in to your account and Open the following url https://kzlabs.in/703.php
2. Navigate to Lab results section and click on a report and view details
3. Replace id value to some other values like 02, 03. You will be able other user's report


## Proof of Concept Request

<img width="3000" height="1532" alt="image" src="https://github.com/user-attachments/assets/a9f5559d-235e-4379-8e9d-61a05b2230f7" />

<img width="3000" height="1514" alt="image" src="https://github.com/user-attachments/assets/37ec8529-7caf-4635-9e34-e8dac09ef25a" />

Accessing other user's data

<img width="2982" height="1520" alt="image" src="https://github.com/user-attachments/assets/38560db7-223a-49c7-bef7-7571821d5a09" />

<img width="3000" height="1430" alt="image" src="https://github.com/user-attachments/assets/5f4a2ca1-9934-4e31-97a3-60e641eca26b" />


## Impact
- It allows attackers to access resources belonging to other users
- It potentially leads to unauthorized access to sensitive information
- It may lead to modification or deletion of another user's data
- It can expose personal, financial, or business sensitive information
- It could impact the confidentiality and integrity of user data


## Remediation
- Implement proper server-side authorization checks for every request
- Do not rely on client-side validation for access control decisions
- Verify that the authenticated user owns or is authorized to access the requested resource
- Use indirect object references instead of exposing sequential IDs
- Use role-based access control (RBAC) where applicable
- Log and monitor unauthorized access attempts for suspicious activity
- Perform access control validation on both read and write operations
