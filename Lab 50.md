## Title
Self Cross-Site Scripting (XSS) in "search" field

## Summary
I found a Self Cross-Site Scripting vulnerability in the "search" field in following url

## Affected URL
https://kzlabs.com/50.php


## Steps to Reproduce
1. Open the following URL in a browser: http://kzlabs.com/50.php
2. Enter following payload "><ImG src=x onerror=\u0061lert("XSS")>  
3. You will see a javascript alert box is getting triggered.
4. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="2996" height="1412" alt="image" src="https://github.com/user-attachments/assets/920a3fe0-9e20-44e3-a7e0-75f8a806d5cb" />


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
