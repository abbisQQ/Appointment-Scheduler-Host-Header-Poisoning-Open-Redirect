#CVE-2024-42671 Appointment-Scheduler-Host-Header-Poisoning-Open-Redirect 
A common vulnerability found in a github repository.
[https://github.com/slabiak](https://github.com/slabiak/AppointmentScheduler)

Host Header Poisoning in the context of Open Redirect is a security vulnerability where an attacker manipulates the Host header of an HTTP request to inject a malicious value. When a web server relies on the Host header to construct URLs for redirects or other operations without proper validation, it can be tricked into redirecting users to an attacker-controlled domain. This can be exploited to perform phishing attacks, steal user credentials, or distribute malware.

Impact:
An attacker can use this vulnerability to redirect users to a malicious website, leading to potential credential theft, malware distribution, or other malicious activities. This can compromise user trust and the security of the affected application.

Proof of concept
I run the application on my local machine on port 8080


 ![application](https://github.com/user-attachments/assets/da0af86d-636b-4cf6-8c4c-3c8130768025)

The application redirects to the /login if an unauthenticated use tries to visit the web application.

![normat redirect 1](https://github.com/user-attachments/assets/40050ab1-debe-4143-a4ea-257cc0362f75)

![normat redirect 2](https://github.com/user-attachments/assets/0ce1626c-239b-4001-807a-aa7fe16ce1a3)

Currently, the application accepts the Host header without any validation or checks.
Changing the host header from localhost to example.com we can see in the images below that the application redirects the user to that web site.

![arbitary 1](https://github.com/user-attachments/assets/2c4e0bae-d254-4f53-bdaa-06a7f3637e03)

 ![arbitary 2](https://github.com/user-attachments/assets/1efbbcf0-d961-40cb-a21a-c8be3a82d329)

This demonstrates that an attacker can supply an arbitrary Host header, potentially redirecting users to malicious websites, thereby facilitating various attacks.

Mitigation:
To mitigate this vulnerability, ensure that the Host header is properly validated against a whitelist of allowed values. Additionally, avoid using the Host header to construct URLs for redirects or other security-critical operations.

Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-42671
