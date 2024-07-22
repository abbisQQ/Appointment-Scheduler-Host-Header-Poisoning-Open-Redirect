# Appointment-Scheduler-Host-Header-Poisoning-Open-Redirect
A common vulnerability found in a github repository.
https://github.com/slabiak

Host Header Poisoning in the context of Open Redirect is a security vulnerability where an attacker manipulates the Host header of an HTTP request to inject a malicious value. When a web server relies on the Host header to construct URLs for redirects or other operations without proper validation, it can be tricked into redirecting users to an attacker-controlled domain. This can be exploited to perform phishing attacks, steal user credentials, or distribute malware.

Impact:
An attacker can use this vulnerability to redirect users to a malicious website, leading to potential credential theft, malware distribution, or other malicious activities. This can compromise user trust and the security of the affected application.

Proof of concept
I run the application on my local machine on port 8080

![image](https://github.com/user-attachments/assets/c88e2589-21a0-4de1-9f7d-15ead5569c9f)

 
The application redirects to the /login if an unauthenticated use tries to visit the web application.

![image](https://github.com/user-attachments/assets/eeddc3e8-5b93-4340-bf44-cafbe19b74bf)

![image](https://github.com/user-attachments/assets/d9307fe8-1395-44c1-a38f-23c2e05f685b)

 
Currently, the application accepts the Host header without any validation or checks.
Changing the host header from localhost to example.com we can see in the images below that the application redirects the user to that web site.

![image](https://github.com/user-attachments/assets/a9535fb2-bc5c-4cc3-a6d2-bd2b0273283f)

![image](https://github.com/user-attachments/assets/20b15442-7324-4910-86bb-8c39a9f09d40)

 
This demonstrates that an attacker can supply an arbitrary Host header, potentially redirecting users to malicious websites, thereby facilitating various attacks.

Mitigation:
To mitigate this vulnerability, ensure that the Host header is properly validated against a whitelist of allowed values. Additionally, avoid using the Host header to construct URLs for redirects or other security-critical operations.
