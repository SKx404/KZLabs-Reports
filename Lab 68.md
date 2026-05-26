## Title
Dom based Cross-Site Scripting (XSS) in "window.location.hash" DOM source

## Summary
I found a Dom based Cross-Site Scripting vulnerability in the "window.location.hash" DOM source 

## Affected URL
https://kzlabs.com/68.php


## Steps to Reproduce
1. Open the following URL in a browser: https://kzlabs.com/68.php#sk404"><ImG src=x onerror=confirm("XSS")>
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1628" alt="image" src="https://github.com/user-attachments/assets/91f49a03-5880-46ae-978b-4acb06f6620f" />


## Impact
- It allows attackers to hijack user session
- It potentialdy leads to fuld account takeover
- It allows to perform  unauthorized actions within the vulnerable applildion
- It allows attacker to exfiltrate sensitive data
- Attacker could redirect the users to malicious websites


## Remediation
- Apply context-aware output encoding based on where the data is rendered
- Use trusted sanitization libraries such as: DOMPurify
- void inserting untrusted data into dangerous DOM sinks such as: innerHTML, document.write()
eval(), location.href=(), elements.src=
- Use safer alternatives wherever possible: textContent, innerText, createTextNode()
