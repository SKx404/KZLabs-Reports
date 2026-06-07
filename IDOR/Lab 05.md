## Title
Insecure Direct Object Reference (IDOR) in Transfer


## Summary
I found an Insecure Direct Object Reference (IDOR) vulnerability in Transfer section. The ref parameter is vulnerable to IDOR in following url


## Affected URL
https://kzlabs.in/705.php


## Steps to Reproduce
1. Login in to your account and Open the following url https://kzlabs.in/705.php
2. Navigate to Transfer section and click on a Reference transaction number and view details
3. Replace ref value to some other values like TXN-10004, TXN-10005. You will be able other user's data


## Proof of Concept Request

<img width="3000" height="1562" alt="image" src="https://github.com/user-attachments/assets/75de39e0-4d5d-43da-94ea-f2086d0a75f6" />

<img width="3000" height="1688" alt="image" src="https://github.com/user-attachments/assets/26eac40d-102f-4701-aab3-8ae447d0b8ea" />

Accessing other user's data.

<img width="2998" height="1688" alt="image" src="https://github.com/user-attachments/assets/5d25ebd5-5ab5-404b-a619-14332c89fb31" />

<img width="2996" height="1652" alt="image" src="https://github.com/user-attachments/assets/737835d8-258d-4d38-838c-67c5120539c3" />


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
