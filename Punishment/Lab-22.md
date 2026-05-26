## Title
Reflected Cross-Site Scripting (XSS) in "color" parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "color" in following url

## Affected URL
https://kzlabs.com/punishment/22.php


## Steps to Reproduce
1. Open the following URL in a browser: https://kzlabs.com/punishment/22.php?color="><ImG src=x onerror=\u0061lert("XSS")>
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request

<img width="2998" height="1496" alt="image" src="https://github.com/user-attachments/assets/0fd97b09-606c-4fb3-b46c-304297bc0965" />



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


