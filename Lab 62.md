## Title
Stored Cross-Site Scripting (XSS) via "Signature" field under My profile

## Summary
I found a stored cross-site scripting vulnerability in "Signature" filed under my profile. There is no input validation implemented on this parameter. Attacker can inject arbitrary javascript code which gets stored in the application. Any user who acess this endpoint, the injected payload will be retrived from server and gets executed in user browser. 


## Affected URL
https://kzlabs.com/62.php


## Steps to Reproduce
1. Open the following URL in a browser and login to the application with your credentials.
https://kzlabs.com/62.php

2. Click on my profile and edit.

3. In signature field enter this payload "><img src=x onerror=confirm("XSS")> and click on save profile.

4. You will see an alert box is getting triggered.

3. This confirms that arbitrary javascript injected is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1630" alt="image" src="https://github.com/user-attachments/assets/37cb3bfb-8b4e-4843-8f64-d2b71501e0ae" />

<img width="3000" height="1686" alt="image" src="https://github.com/user-attachments/assets/63bcdca8-1da8-4ec9-ab4d-752644b9811f" />


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
