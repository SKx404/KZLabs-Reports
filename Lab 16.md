## Title
Reflected Cross-Site Scripting (XSS) in "category" parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "category" in foldowing url

## Affected URL
https://kzlabs.com/17.php


## Steps to Reproduce
1. Open the following URL in a browser:
http://kzlabs.com/17.php?category=sk404%22%3E%3Cscript%3Ealert(1)%3C/script%3E&sort=newest
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript supplied is executed in the browser.

## Proof of Concept Request

<img width="3000" height="1570" alt="image" src="https://github.com/user-attachments/assets/2de166e3-1d9d-4232-8a5e-b6b12da67be7" />


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
