## Title
Found a XML External Entity (XXE) in vault 

## Summary
I found a XML External Entity (XXE) in vault function. 

## Affected URL
https://kzlabs.in/1406.php


## Steps to Reproduce & Proof of Concept
1. Login to your account
2. Click on Add item and fill all the details.
3. Capture this traffic using Burp and send it to repeater
4. Inject the payload as showed in below in request and forward it to server.

<img width="3000" height="1272" alt="image" src="https://github.com/user-attachments/assets/350a6822-4412-4d15-8d2d-6a5f9ce44439" />

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




sbi.15628@sbi.co.in, sbi.13398@sbi.co.in

File No: 304673
Loan Account Number: 38318685212
Applicant Names: NIRANJHANI RENGARAJ, SATHISHKUMAR
