## Title
Reflected Cross-Site Scripting (XSS) in "returnTo" Parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "returnTo" in following url

## Affected URL
https://kzlabs.com/57.php

## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/57.php?returnTo=javascript:alert(document.domain)

2. Now click on continue button, You will see a javascript alert box is getting triggered.

3. This confirms that arbitrary javascript supplied via the parameter "returnTo" is executed in the browser.


## Proof of Concept Request

<img width="2680" height="1640" alt="image" src="https://github.com/user-attachments/assets/ac60f005-5a2a-4077-b67c-674e39f3f63e" />

After clicking on continue button, it has trggered alert pop-up

<img width="2666" height="1668" alt="image" src="https://github.com/user-attachments/assets/3a59c644-a4c5-4c3f-b702-bc6cdea801df" />


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
