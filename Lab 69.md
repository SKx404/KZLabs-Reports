## Title
Dom based Cross-Site Scripting (XSS) in "document.location.search" field

## Summary
I found a Dom based Cross-Site Scripting vulnerability in the "document.location.search" field in following url

## Affected URL
https://kzlabs.com/69.php


## Steps to Reproduce
1. Open the following URL in a browser: https://kzlabs.com/69.php/pub/fujitsu/fm3v2/player/?javascript:alert(404)
2. You will see a javascript alert box is getting triggered.
3. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1656" alt="image" src="https://github.com/user-attachments/assets/302722f0-9a8e-40eb-a76d-7ca01cb75e36" />


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
