## Title
Reflected Cross-Site Scripting (XSS) in "p" Parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "p" in following url

## Affected URL
https://kzlabs.com/56.php


## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/56.php?p='><img src=x onerror=confirm("XSS")>

2. You will see a javascript alert box is getting triggered.

3. This confirms that arbitrary javascript supplied via the parameter "p" is executed in the browser.


## Proof of Concept Request

<img width="2932" height="1680" alt="image" src="https://github.com/user-attachments/assets/05ff2dff-1bb9-4024-8915-6f52303a6dd4" />


## Impact
- It allows attackers to hijack user session
- It potentially leads to full account takeover
- It allows to perform  unauthorized actions within the vulnerable application
- It allows attacker to exfiltrate sensitive data


## Remediation
- User supplied input should be validated at server level.
- Use a security encoding library to encode all parameters
- Use whitelisting instead of blacklist for special charecters
- Use HTTPOnly flag. This will prevent client-side scripts from accessing cookies
- Use CSP header and avoid using eval, unsafe-inline etc directives in CSP.
- Use strong WAF like cloudflare to block malicious payloads.
