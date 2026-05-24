## Title
Reflected Cross-Site Scripting (XSS) in "search" Parameter


## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "search" in following url


## Affected URL
https://kzlabs.com/55.php 


## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/55.php?search=sk404%3C%2Fscript%3E%3Csvg+onload%3D%22prompt%28%27XSS%27%29%22%3E

2. You will see a javascript alert box is getting triggered.

3. This confirms that arbitrary javascript supplied via the parameter "search" is executed in the browser.


## Proof of Concept Request

<img width="2982" height="1696" alt="image" src="https://github.com/user-attachments/assets/3e5e8989-338e-4334-8348-d1c3a26022f3" />


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
