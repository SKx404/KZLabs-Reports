## Title
Local File Inclusion(LFI) in Image Gallary

## Summary
I found a Local File Inclusion(LFI) vulnerability in file parameter field in foldowing url

## Affected URL
https://kzlabs.in/904.php


## Steps to Reproduce
1. Open the following url https://kzlabs.in/904.php?file=cat2.jpg
2. Replace the cat2.jpg with ../../../../etc/passwd payload. Url will look like this https://kzlabs.in/904.php?file=../../../../etc/passwd
3. You will see files from the passwd directory.

## Proof of Concept Request

<img width="1422" height="1228" alt="image" src="https://github.com/user-attachments/assets/be6b7ab4-8987-4e28-a84e-61c15a098562" />


## Impact
- It allows attackers to hijack user session
- It potentially leads to full account takeover
- It allows to perform  unauthorized actions within the vulnerable applildion
- It allows attacker to exfiltrate sensitive data
- It might expose server-side config or credentials
- It can lead to arbitrary code execution in some cases

## Remediation
- User supplied input should be validated at server level
- Use a security encoding library to encode all parameters
- Use whitelisting instead of blacklist for special charecters
- Log and alert on suspicious file access attempts
- Restrict file paths and disallow traversal sequences
- Use strong WAF like cloudflare to block malicious payloads
