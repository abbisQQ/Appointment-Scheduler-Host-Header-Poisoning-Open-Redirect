# Appointment-Scheduler-Host-Header-Poisoning-Open-Redirect
A common vulnerability found in a github repository.
https://github.com/slabiak

Host Header Poisoning in the context of Open Redirect is a security vulnerability where an attacker manipulates the Host header of an HTTP request to inject a malicious value. When a web server relies on the Host header to construct URLs for redirects or other operations without proper validation, it can be tricked into redirecting users to an attacker-controlled domain. This can be exploited to perform phishing attacks, steal user credentials, or distribute malware.

Impact:
An attacker can use this vulnerability to redirect users to a malicious website, leading to potential credential theft, malware distribution, or other malicious activities. This can compromise user trust and the security of the affected application.

Proof of concept
I run the application on my local machine on port 8080


 ![application](https://github.com/user-attachments/assets/da0af86d-636b-4cf6-8c4c-3c8130768025)

The application redirects to the /login if an unauthenticated use tries to visit the web application.


![normal_host1](https://github.com/user-attachments/assets/4171f5c3-2bad-4a20-9b07-f264f21acc74)

![normalhost1 1](https://github.com/user-attachments/assets/2f1d5097-fa63-45d8-8920-497a558942e2)

Currently, the application accepts the Host header without any validation or checks.
Changing the host header from localhost to example.com we can see in the images below that the application redirects the user to that web site.


![Arbitary host1](https://github.com/user-attachments/assets/065a3097-abb4-4afc-8586-e5c6691c7d8c)

![Arbitary host2 2](https://github.com/user-attachments/assets/05a378ed-1190-4d00-bd04-51a20ae4e079)
 
This demonstrates that an attacker can supply an arbitrary Host header, potentially redirecting users to malicious websites, thereby facilitating various attacks.

Mitigation:
To mitigate this vulnerability, ensure that the Host header is properly validated against a whitelist of allowed values. Additionally, avoid using the Host header to construct URLs for redirects or other security-critical operations.
