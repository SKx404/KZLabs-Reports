## Title
Reflected Cross-Site Scripting (XSS) in "q" parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "q" in foldowing url

## Affected URL
https://kzlabs.com/7.php


## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/7.php?q=sk404%3C/h1%3E%3CImG%20src=x%20onerror=\u0061lert(%22XSS%22)//
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="2962" height="1482" alt="image" src="https://github.com/user-attachments/assets/3cb5ac79-185a-4fa8-abaf-f7e73558ced6" />


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
