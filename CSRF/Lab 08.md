## Title
Found a Cross-Site Request Forgery (CSRF) in update email address 

## Summary
I found a Cross-Site Request Forgery (CSRF) in update email address  mechanism

## Affected URL
https://kzlabs.in/1308.php?action=settings


## Steps to Reproduce & Proof of Concept
1. Login as an Attacker and Open the following URL in a browser: https://kzlabs.in/1308.php?action=settings
2. Navigate to update email address field
3. Enter the email address which you want to set for victim. Here i used attacker2@test.com

<img width="3000" height="1490" alt="image" src="https://github.com/user-attachments/assets/7b1d0fe7-2ebe-4b42-a7bb-68a3653bb58e" />

4. Capture this traffic and use Burp CSRF generator to craft poc.

<img width="3000" height="1642" alt="image" src="https://github.com/user-attachments/assets/0cb38eac-e66a-460b-9b14-d3d9bd7499a8" />

6. Share the link with victim. When the victim clicks the link while he/she authenticated, it will change the email

Before the attack

<img width="3000" height="1774" alt="image" src="https://github.com/user-attachments/assets/e722c727-d1a3-4c4d-b7d2-2be6fbc80626" />

After the attack

<img width="3000" height="1676" alt="image" src="https://github.com/user-attachments/assets/785fdc84-a9b3-4712-b240-2bd1099dc9ef" />



## CSRF Impact

- It allows attackers to perform unauthorized actions on behalf of authenticated users
- It may lead to unauthorized modification of account settings and sensitive user data
- It can potentially result in account takeover when targeting email or password change functionalities
- It allows attackers to abuse privileged user sessions to perform administrative actions
- It may lead to financial loss or business logic abuse if sensitive transactions are affected


## CSRF Remediation

- Implement anti-CSRF tokens for all state-changing requests and validate them server-side
- Enforce SameSite=Lax or SameSite=Strict attributes on session cookies
- Validate Origin and Referer headers for sensitive requests
- Avoid using GET requests for state-changing operations
- Require re-authentication or additional verification for critical account actions
