## Title
Stored Cross-Site Scripting (XSS) in "Site title, Site Description, Welcome message, Footer text" fields

## Summary
I found a Stored Cross-Site Scripting vulnerability in the "Subject and Description" fields field in foldowing url

## Affected URL
https://kzlabs.com/22.php


## Steps to Reproduce
1. Login to the application
2. Enter the following payload <scRipt>aler\u0074('XSS')</ScrIpt> in "Subject and Description" fields 
3. You will see a javascript alert box is getting triggered.
4. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="2994" height="1260" alt="image" src="https://github.com/user-attachments/assets/769d58f2-11c7-44cc-a5ca-805af9f06ef8" />

<img width="3000" height="1340" alt="image" src="https://github.com/user-attachments/assets/a2cd8207-15b9-4c07-b9cc-e17403d3d4f6" />

<img width="3000" height="1610" alt="image" src="https://github.com/user-attachments/assets/fb34f616-8220-49c9-b6bb-47aa2714fad2" />


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


