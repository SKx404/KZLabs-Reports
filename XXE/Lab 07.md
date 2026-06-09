## Title
Found a XML External Entity (XXE) in vault 

## Summary
I found a XML External Entity (XXE) in vault function. 

## Affected URL
https://kzlabs.in/1407.php


## Steps to Reproduce & Proof of Concept
1. Go to Login page and enter your credentials
2. Click on login and capture the traffic using burp
3. Send that request to repeater
4. Inject the payload as showed in below in request and forward it to server.

<img width="2996" height="1260" alt="image" src="https://github.com/user-attachments/assets/1be48908-2146-4249-bedc-69b4663f7e79" />

5. You will etc/passwd file is being retrieved in response.

## XXE Impact

- An attacker can leverage the XXE vulnerability to read arbitrary files from the server.
- Sensitive information such as configuration files, credentials, API keys, and internal application data may be exposed.
- The vulnerability may allow interaction with internal services that are not intended to be accessible externally.
- Successful exploitation could lead to unauthorized disclosure of sensitive business and user information.
- Depending on the environment, this issue may be leveraged to facilitate further attacks against internal infrastructure.


## XXE Remediation

- Disable XML external entity processing and DTD support within the XML parser.
- Use secure parser configurations that prevent external resource resolution.
- Validate and restrict incoming XML data to only the expected format.
- Limit the application's file system and network permissions according to the principle of least privilege.
- Regularly update XML processing libraries and perform security reviews of XML-handling functionality.
