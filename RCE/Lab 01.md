## Title
Remote Code Execution (RCE) in Command field

## Summary
I found a Remote Code Execution (RCE) vulnerability in command field in following url

## Affected URL
https://kzlabs.in/1101.php


## Steps to Reproduce
1. Login to the application and Open the following url https://kzlabs.in/1101.php
2. ENter the following command cat /etc/passwd
3. You will see files from the passwd directory

## Proof of Concept Request

<img width="2994" height="1704" alt="image" src="https://github.com/user-attachments/assets/c425132f-378c-4f46-b968-8954afea7878" />


## Impact
- It allows attacker to run arbitary code on server
- It potentially leads to full server compromise
- Attacker can escalate priviledges and access sensitive data
- It might let attacker install malware or persist access
- Attacker can exfiltrate database or config files


## Remediation
- User supplied input should be validated at server level
- Avoid eval, exec, system or similar commands with user input
- Use secure libraries for code execution or templating
- Restrict file and command paths, whitelist allowed values
- Use whitelisting instead of blacklist for special charecters
- Log and alert on suspicious file access attempts
- Restrict file paths and disallow traversal sequences
- Use strong WAF like cloudflare to block malicious payloads
