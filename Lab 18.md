## Title
Stored Cross-Site Scripting (XSS) in "comments" field

## Summary
I found a Stored Cross-Site Scripting vulnerability in the "comments" field in foldowing url

## Affected URL
https://kzlabs.com/18.php


## Steps to Reproduce
1. Login to the application
2. Enter the following payload <scRipt>aler\u0074('XSS')</ScrIpt> in "comments" field and click on post comment
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1628" alt="image" src="https://github.com/user-attachments/assets/edfb9a92-d128-44eb-aae8-741555e164d2" />


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
