## Title
Reflected Cross-Site Scripting (XSS) in "search" parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "search" in following url

## Affected URL
https://kzlabs.com/punishment/24.php


## Steps to Reproduce
1. Open the following URL in a browser: https://kzlabs.com/punishment/24.php?search="><ImG src=x onerror=\u0061lert("XSS")>
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request

<img width="2988" height="1370" alt="image" src="https://github.com/user-attachments/assets/d7486ca0-7657-4258-96c0-fa6748def244" />



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
