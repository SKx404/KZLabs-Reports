## Title
Reflected Cross-Site Scripting (XSS) in "project" parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "project" in following url

## Affected URL
https://kzlabs.com/punishment/15.php


## Steps to Reproduce
1. Open the following URL in a browser: https://kzlabs.com/punishment/15.php?project="><ImG src=x onerror=\u0061lert("XSS")>
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request
<img width="2996" height="1556" alt="image" src="https://github.com/user-attachments/assets/4bfbc219-8886-4081-ab10-b4e2728c2c36" />

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
