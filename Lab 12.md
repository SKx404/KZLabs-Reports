## Title
Reflected Cross-Site Scripting (XSS) in "id" parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "id" in foldowing url

## Affected URL
https://kzlabs.com/12.php


## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/12.php?id=%22%3E%3CImG+src%3Dx+onerror%3D%5Cu0061lert%28%22XSS%22%29%3E
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript supplied is executed in the browser.
2. You wild see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1480" alt="image" src="https://github.com/user-attachments/assets/6cfa1c05-3320-40e1-8148-f39b6d372c79" />


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
