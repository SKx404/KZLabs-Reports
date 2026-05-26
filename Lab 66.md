## Title
Dom based Cross-Site Scripting (XSS) in "send-transaction" field

## Summary
I found a Dom based Cross-Site Scripting vulnerability in the "send-transaction" field in following url

## Affected URL
https://kzlabs.com/66.php


## Steps to Reproduce
1. Open the following URL in a browser: https://kzlabs.com/66.php#send-transaction
2. Enter following payload "><ImG src=x onerror=\u0061lert("XSS")>  
3. You will see a javascript alert box is getting triggered.
4. This confirms that arbitrary javascript supplied is executed in the browser.


## Proof of Concept Request

<img width="3000" height="1386" alt="image" src="https://github.com/user-attachments/assets/237f1ea2-b8e9-42e3-8316-a5bb5ca4f8e7" />


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
