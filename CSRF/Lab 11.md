## Title
Found a Cross-Site Request Forgery (CSRF) in 2FA authentication module 

## Summary
I found a Cross-Site Request Forgery (CSRF) in 2FA authentication module. I can enable/disable 2FA authentication of any user

## Affected URL
https://kzlabs.in/1311.php


## Steps to Reproduce & Proof of Concept
1. Login as an Attacker and Open the following URL in a browser: https://kzlabs.in/1311.php?action=security
2. Navigate to security page click on disable 2FA authentication
3. Capture this traffic and use Burp CSRF generator to craft poc.

<img width="3000" height="1660" alt="image" src="https://github.com/user-attachments/assets/f76d7bfd-4cdf-4358-8dea-a9a2c9bdc13a" />
 
4. Share the link with victim. When the victim clicks the link while he/she authenticated, it will disable 2FA authentication

Beforre the attck
<img width="3000" height="1740" alt="image" src="https://github.com/user-attachments/assets/c5e85a8d-d492-4f06-b5de-c6a6aa876a6a" />

After the attack
<img width="3000" height="1678" alt="image" src="https://github.com/user-attachments/assets/533fce49-135e-4f98-bd96-9282aca58441" />



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
