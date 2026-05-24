## Title
Reflected Cross-Site Scripting (XSS) in "username" Parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "username" in following url

## Affected URL
https://kzlabs.com/58.php


## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/58.php

2. Click on any conversation. You will see the url like this https://kzlabs.com/58.php/account/SaturnV/messages

3. Replace the username field with following payload "><img src=x onerror=confirm("XSS")>

4. Now URL will look like this https://kzlabs.com/58.php/account/"><img src=x onerror=confirm("XSS")>/messages

5. Hit enter, You will see a javascript alert box is getting triggered.

3. This confirms that arbitrary javascript supplied via the parameter "username" is executed in the browser.


## Proof of Concept Request

<img width="2658" height="1724" alt="58" src="https://github.com/user-attachments/assets/ae7656f9-c0af-4d57-8a6e-3c60784ccba9" />

Select any conversation
<img width="2678" height="1690" alt="image" src="https://github.com/user-attachments/assets/001067b4-f961-4689-9bb7-10a1b83657ae" />

Replace the username with above mentioned payload and click enter. You will see a pop up.
<img width="2662" height="1698" alt="image" src="https://github.com/user-attachments/assets/ff2a4d9e-24dd-4c70-9e12-76af6c2cc64d" />

<img width="2670" height="1692" alt="image" src="https://github.com/user-attachments/assets/9eb207de-4218-4d9e-aca6-49b4e69be9f6" />


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
