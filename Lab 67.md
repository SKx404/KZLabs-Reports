## Title
Dom based Cross-Site Scripting (XSS) in "slug" field

## Summary
I found a Dom based Cross-Site Scripting vulnerability in the "slug" field in following url

## Affected URL
https://kzlabs.com/67.php


## Steps to Reproduce
1. Open the following URL in a browser: https://kzlabs.com/67.php?slug=sk404%22%3E%3CImG%20src=x%20onerror=\u0061lert(%22XSS%22)%3E
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1520" alt="image" src="https://github.com/user-attachments/assets/d476927e-7411-4156-be23-c9120ee0a9b9" />


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
