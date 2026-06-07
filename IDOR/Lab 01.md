## Title
Insecure Direct Object Reference (IDOR) in My orders


## Summary
I found an Insecure Direct Object Reference (IDOR) vulnerability in my orders section. id paramter is vulnerable to IDOR in following url


## Affected URL
https://kzlabs.in/701.php


## Steps to Reproduce
1. Open the following url https://kzlabs.in/701.php and login to your account.
2. Navigate to My orders section and click on any invoice and view it.
3. Capture the traffic and send it to repeater
4. Replace id value to some other values like 02, 03. You will be able other users invoices.


## Proof of Concept Request

<img width="3000" height="1234" alt="image" src="https://github.com/user-attachments/assets/0e3fc9f0-7aae-49d8-ad29-92705dbfa6d6" />

<img width="2988" height="1688" alt="image" src="https://github.com/user-attachments/assets/85e5299a-4368-481c-9e0a-90f770e27cb0" />

Accessing other user's data by tampering id parameter

<img width="3000" height="1208" alt="image" src="https://github.com/user-attachments/assets/5dd9468f-2422-415e-9878-f1195ebbdeb8" />

<img width="3000" height="1272" alt="image" src="https://github.com/user-attachments/assets/c9b0b654-45fd-46ed-8e97-a9c7dd643130" />



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
