## Title
Reflected Cross-Site Scripting (XSS) in "lname" Parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "lname" in following url

## Affected URL
https://kzlabs.com/punishment/9.php


## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/punishment/9.php?fname=%22%3E%3CImG+src%3Dx+onerror%3D%5Cu0061lert%28%22XSS%22%29%3E&lname=%22%3E%3CImG+src%3Dx+onerror%3D%5Cu0061lert%28%22XSS1%22%29%3E

2. You will see a javascript alert box is getting triggered.

3. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1348" alt="image" src="https://github.com/user-attachments/assets/9e260a30-ef33-4d27-9f57-5bd7c4192ff2" />

<img width="3000" height="1408" alt="image" src="https://github.com/user-attachments/assets/81f957d6-8240-403e-b036-fb286a877edd" />



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

