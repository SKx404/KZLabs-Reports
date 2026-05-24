
## Title
Stored Cross-Site Scripting (XSS) via "Report Name Field" in Network Reports

## Summary
I found a stored cross-site scripting vulnerability in "Report Name field" under "New Network Report" functionality. There is no input validation implemented on this parameter. Attacker can inject arbitrary javascript code which gets stored in the application. Any user who visits the affected page, the injected payload will be retrived from server and gets executed in user browser. 


## Affected URL
https://kzlabs.com/60.php


## Steps to Reproduce
1. Open the following URL in a browser and login to the application with your credentials.
https://kzlabs.com/60.php

2. Click on new network report.

3. In report name field enter this payload "><img src=x onerror=confirm("XSS")> and click on Run&Save report.

4. You will see an alert box is getting triggered.

5. This confirms that arbitrary javascript injected is executed in the browser.



## Proof of Concept Request

<img width="3000" height="1392" alt="image" src="https://github.com/user-attachments/assets/28f26c8c-500b-4b4d-9c1f-df3c45e80414" />

<img width="3000" height="1686" alt="image" src="https://github.com/user-attachments/assets/12ea2f4f-da16-461c-b9ad-8a5c06e60ebb" />

<img width="3000" height="1674" alt="image" src="https://github.com/user-attachments/assets/bf1945e8-c242-4c14-81ef-00691c0b8882" />




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

