## Title
Reflected Cross-Site Scripting (XSS) in "t3_u9po1l" Parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "t3_u9po1l" in following url

## Affected URL
https://kzlabs.com/59.php


## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/59.php

2. Click on any profile. You will see the url like this https://kzlabs.com/59.php/svc/shreddit/api/comments/askreddit/t3_u9po1l/t1_i5sxroa

3. Now add this payload "><img src=x onerror=confirm("XSS")> after t3_u9po1l

4. Now URL will look like this https://kzlabs.com/59.php/svc/shreddit/api/comments/askreddit/t3_u9po1l"><img src=x onerror=confirm("XSS")>

5. Hit enter, You will see a javascript alert box is getting triggered.

3. This confirms that arbitrary javascript supplied via the parameter "t3_u9po1l" is executed in the browser.


## Proof of Concept Request

<img width="2958" height="1702" alt="image" src="https://github.com/user-attachments/assets/d1531917-c3fb-4bc7-848f-1bcc19f4d21f" />

<img width="2990" height="1696" alt="image" src="https://github.com/user-attachments/assets/aea7bda6-cbf1-4cf6-a7b0-efc4974edfb8" />

<img width="3000" height="1698" alt="image" src="https://github.com/user-attachments/assets/7c95c20f-238b-499e-bce3-ac2b8d131219" />

<img width="2988" height="1650" alt="image" src="https://github.com/user-attachments/assets/d582e5ec-0dfa-475d-851c-45c8e03f4fc6" />


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
