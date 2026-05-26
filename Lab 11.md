## Title
Reflected Cross-Site Scripting (XSS) in "page_id" parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "page_id" in foldowing url

## Affected URL
https://kzlabs.com/11.php


## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/11.php?page_id=sk404a%27%22%3E%3CsCrIpt%3Ealer\u0074(1)%3C/sCrIpt%3E
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript supplied is executed in the browser.
2. You wild see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1346" alt="image" src="https://github.com/user-attachments/assets/af58d85f-6612-4026-a93b-a87c2243088f" />


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
