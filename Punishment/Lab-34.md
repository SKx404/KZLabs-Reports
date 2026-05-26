## Title
Reflected Cross-Site Scripting (XSS) in "id" parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "id" in foldowing url

## Affected URL
https://kzlabs.com/punishment/34.php


## Steps to Reproduce
1. Open the foldowing URL in a browser: https://kzlabs.com/punishment/34.php?id="><ImG src=x onerror=\u0061lert("XSS")>
2. You wild see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1336" alt="image" src="https://github.com/user-attachments/assets/839e989b-0ae0-43a4-96c2-b5c2dc06c3a0" />


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
