Sherlock Scenario
As a fast-growing startup, Forela has been utilising a business management platform. Unfortunately, our documentation is scarce, and our administrators aren't the most security aware. As our new security provider we'd like you to have a look at some PCAP and log data we have exported to confirm if we have (or have not) been compromised.


Task 1

We believe our Business Management Platform server has been compromised. Please can you confirm the name of the application running?

BonitaSoft
Here, I checked the .json file given. After beautifing it to make it easy to read, I noticed the following line
![Screenshot (1634)](https://github.com/user-attachments/assets/847dbdbb-11e8-4e55-acc2-efc540bc50a3)


Task 2

We believe the attacker may have used a subset of the brute forcing attack category - what is the name of the attack carried out?

Credential Stuffing
Here we search for http, we see many attempts to log in to the "http://forela.co.uk:8080/bonita/loginservice" path. We also notice that the attacker uses a different username and password for each login attempt. This username and password are not the common types found in dictionary attacks. Checking the Matre Attack framework, the bruteforce attack coming close to what we have noticed is credential stuffing.
![Screenshot (1635)](https://github.com/user-attachments/assets/30a3c566-ad06-4493-aa45-fd7956d5c477)

Task 3

Does the vulnerability exploited have a CVE assigned - and if so, which one?

CVE-2022-25237
From the same .json file where we found the software name, we also have the CVE present. This can help us understand the vulnerability better.
![Screenshot (1634)](https://github.com/user-attachments/assets/847dbdbb-11e8-4e55-acc2-efc540bc50a3)

Task 4

Which string was appended to the API URL path to bypass the authorization filter by the attacker's exploit?

i18ntranslation
Still with our http search parameter, we notice a couple of 404 errors, A change in error code to 204 showing that the request succeeded, We check the http request before it and find the path "POST /bonita/API/pageUpload;i18ntranslation?action=add HTTP/1.1\r\n", here we notice that the attacker added the "i18ntranslation" string that bypassed the authorization filter.
![Screenshot (1636)](https://github.com/user-attachments/assets/cbb1696e-b2e3-4e8e-90f6-0f0195c65425)


Task 5

How many combinations of usernames and passwords were used in the credential stuffing attack?

**

Task 6

Which username and password combination was successful?

username:password

Task 7

If any, which text sharing site did the attacker utilise?

******.*o

Task 8

Please provide the filename of the public key used by the attacker to gain persistence on our host.

Filename

Task 9

Can you confirmed the file modified by the attacker to gain persistence?

/****/******/.***/**********_***s

Task 10

Can you confirm the MITRE technique ID of this type of persistence mechanism?

T****.***
