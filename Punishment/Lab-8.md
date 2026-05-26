## Title
Reflected Cross-Site Scripting (XSS) in "lname" Parameter

## Summary
I found a Reflected Cross-Site Scripting vulnerability in the parameter "lname" in following url

## Affected URL
https://kzlabs.com/punishment/8.php


## Steps to Reproduce
1. Open the following URL in a browser:
https://kzlabs.com/punishment/8.php?fname=%22%3E%3CImG+src%3Dx+onerror%3D%5Cu0061lert%28%22XSS%22%29%3E&lname=%22%3E%3CImG+src%3Dx+onerror%3D%5Cu0061lert%28%22XSS1%22%29%3E

2. You will see a javascript alert box is getting triggered.

3. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1248" alt="image" src="https://github.com/user-attachments/assets/5651fbe9-7e40-4176-a271-2fb28162a824" />

<img width="3000" height="1222" alt="image" src="https://github.com/user-attachments/assets/ee0ff37f-b9c3-4f58-b552-3431661c34d2" />



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
