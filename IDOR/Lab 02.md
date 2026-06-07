## Title
Insecure Direct Object Reference (IDOR) in Trip history


## Summary
I found an Insecure Direct Object Reference (IDOR) vulnerability in trip history section. id paramter is vulnerable to IDOR in following url


## Affected URL
https://kzlabs.in/702.php


## Steps to Reproduce
1. Login in to your account and Open the following url https://kzlabs.in/702.php?action=trips
2. Navigate to Trip History section and click on any trip and view it
3. Capture the traffic and send it to repeater
4. Replace id value to some other values like 02, 03. You will be able other user's trips


## Proof of Concept Request

<img width="3000" height="1228" alt="image" src="https://github.com/user-attachments/assets/d975b417-925a-4dbc-a4ca-02f0beb8c46a" />

<img width="2996" height="1382" alt="image" src="https://github.com/user-attachments/assets/1090df14-e073-45dd-8403-84e59611d4fb" />

Accessing other user's data by changing the values in id parameter

<img width="3000" height="1264" alt="image" src="https://github.com/user-attachments/assets/4ce4226a-6ead-4187-b866-3d03d8696a61" />


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
