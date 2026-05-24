
## Title
Stored Cross-Site Scripting (XSS) via "Body" parameter in My articals feature.

## Summary
I found a stored cross-site scripting vulnerability in "Body" parameter when creating a new article. There is no input validation implemented on this parameter. Attacker can inject arbitrary javascript code which gets stored in the application. Any user who acess this endpoint, the injected payload will be retrived from server and gets executed in user browser. 


## Affected URL
https://kzlabs.com/61.php


## Steps to Reproduce
1. Open the following URL in a browser and login to the application with your credentials.
https://kzlabs.com/61.php

2. Click on write article.

3. In the Bondy field, click on HTML and enter this payload "><img src=x onerror=confirm("XSS")> and then click on publish.

4. You will see an alert box is getting triggered.

3. This confirms that arbitrary javascript injected is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1580" alt="image" src="https://github.com/user-attachments/assets/029c0dd8-0742-4a2b-98ce-39b6e871b76e" />

<img width="2978" height="1650" alt="image" src="https://github.com/user-attachments/assets/6347183d-672b-4c28-b3f0-0e4be46dc900" />

<img width="3000" height="1688" alt="image" src="https://github.com/user-attachments/assets/8fbfd902-9cd6-42d1-bb27-abf3de16f01e" />


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
