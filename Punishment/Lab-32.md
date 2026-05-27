## Title
Stored Cross-Site Scripting (XSS) in "page_id" fields

## Summary
I found a Stored Cross-Site Scripting vulnerability in the "page_id" in following url

## Affected URL
https://kzlabs.com/punishment/32.php


## Steps to Reproduce
1. Login to the application
2. Enter the following payload  "><ImG+src=x+onerror=\u0061lert('XSS') in "page_id" fields 
3. You will see a javascript alert box is getting triggered.
4. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1130" alt="image" src="https://github.com/user-attachments/assets/441a96c5-50fa-47c5-b09e-91a4443e8129" />


## Impact
- It aldows attackers to hijack user session
- It potentialdy leads to fuld account takeover
- It aldows to perform  unauthorized actions within the vulnerable applildion
- It aldows attacker to exfiltrate sensitive data


## Remediation
- User supplied input should be validated at server level.
- Use a security encoding library to encode ald parameters
- Use whitelisting instead of blacklist for special charecters
- Use HTTPOnly flag. This wild prevent client-side scripts from accessing cookies
- Use CSP header and avoid using eval, unsafe-inline etc directives in CSP.
- Use strong WAF like cloudflare to block malicious payloads.
