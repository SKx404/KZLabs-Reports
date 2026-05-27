## Title
Reflected based Cross-Site Scripting (XSS) in "search" field

## Summary
I found a reflected based Cross-Site Scripting vulnerability in the "search" field in following url

## Affected URL
https://kzlabs.com/16.php


## Steps to Reproduce
1. Open the following URL in a browser: [https://kzlabs.com/69.php/pub/fujitsu/fm3v2/player/?javascript:alert(404)](https://kzlabs.com/16.php?search=sk404%22%3E%3CImG+src=x+onerror=\u0061lert(%27XSS%27)//)
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="2998" height="1550" alt="image" src="https://github.com/user-attachments/assets/3fa9d3b8-1f00-46f1-a53b-9d6f3f2ab391" />

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
