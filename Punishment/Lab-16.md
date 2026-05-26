## Title
Reflected Cross-Site Scripting (XSS) in "item" parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "item" in following url

## Affected URL
https://kzlabs.com/punishment/16.php


## Steps to Reproduce
1. Open the following URL in a browser: https://kzlabs.com/punishment/16.php?item="><ImG src=x onerror=\u0061lert("XSS")>
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request

<img width="2998" height="1356" alt="image" src="https://github.com/user-attachments/assets/611ae902-9399-44c6-a0e7-689ed3408897" />



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
