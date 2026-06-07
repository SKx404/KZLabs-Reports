## Title
Found a Cross-Site Request Forgery (CSRF) in change password 

## Summary
I found a Cross-Site Request Forgery (CSRF) in change password mechanism

## Affected URL
https://kzlabs.in/1307.php?action=settings


## Steps to Reproduce & Proof of Concept
1. Login as an Attacker and Open the following URL in a browser: https://kzlabs.in/1307.php?action=settings
2. Navigate to change password module
3. Enter password which you want to set for victim. Here i used attacker@123 as password.
   
<img width="2986" height="1556" alt="image" src="https://github.com/user-attachments/assets/59afefe7-459a-4d66-9e77-5a7c7f8bacd3" />

4. Capture this traffic and use Burp CSRF generator to craft poc.

<img width="3000" height="1658" alt="image" src="https://github.com/user-attachments/assets/c0c459e1-fd99-4e9f-a4df-30524e579368" />
   
5. Share the link with victim. When the victim clicks the link while he/she authenticated, it will change the password 

<img width="3000" height="1632" alt="image" src="https://github.com/user-attachments/assets/307d8353-0846-4e5b-aff1-091f8829d175" />


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
