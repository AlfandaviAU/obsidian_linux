##### Information Security About
Preventing attacks, using several mechanism, refer CIA triad
1. Security <mark style="background: #FF5582A6;">Attack/Threat</mark> -> Possible way to breach
2. Security <mark style="background: #ADCCFFA6;">Service</mark> -> Defending it
3. Security <mark style="background: #FFF3A3A6;">Mechanism</mark> -> How to defend it


##### Security Attack

- Phishing
- Brute-force
- Man-in-the-middle
- DDoS

How to break integrity -> <mark style="background: #FF5582A6;">Modify the data transfered
</mark>


##### <mark style="background: #FFF3A3A6;">Passive Attack</mark> : Interception
- Unauthorised individual gains access to private information
- Hard to detect -> because no traces left
- Example : Wiretapping, Illegal copying, Sniffing (Wireshark)
- Prevented by encryption
- <mark style="background: #FF5582A6;">Confidentiality</mark>

##### <mark style="background: #FFB86CA6;">Active Attack</mark> : Interruption (DDoS)
- Make resources unavailable for users
- Example : 
	- Cutting communication line
	- Disabling file management system
	- Overloading server -> Server cannot respond
- <mark style="background: #FF5582A6;">Availability</mark>

##### <mark style="background: #FFB86CA6;">Active Attack</mark> : Tampering / Modification
- Modify resources that attacker not authorised to modify
- A -> Legit Message -> Z -> Modify -> Fake Message -> B
- Example : 
	- Modify content of messages in network
	- Change information stored in filesystem
	- Altering program to perfom differently
	- Reconfiguring system hardware
- <mark style="background: #FF5582A6;">Integrity</mark>

##### <mark style="background: #FFB86CA6;">Active Attack</mark> : Fabrication
- Attacker pretend to be authorised user, and send fake message
- Impersonation
- <mark style="background: #FF5582A6;">Authenticity</mark>

##### <mark style="background: #FFB86CA6;">Active Attack</mark> : Replay Attack
- Passively capture data
- Retransmit the data -> pretend to be the person
- <mark style="background: #FF5582A6;">Non-repudiation</mark>

| Passive Attacks                                                                  | Active Attacks                                         |
| -------------------------------------------------------------------------------- | ------------------------------------------------------ |
| Monitor and scan systems for vulnerabilities or entry points to intercept system | Involve data stream modification                       |
| Hard to detect but easy to prevent                                               | Involve interaction between attacker and target system |
|                                                                                  | Hard to prevent, easy to detect                        |


Phishing -> Fabrication, Interception
DDoS -> Interruption
Man-in-the-Middle -> Interruption, Interception, Modification
Brute-force -> Fabrication, Interception


#### Security Services
1. Confidentiality
2. Integrity
3. Availability
4. Authentication
	1. Origin : Verify source of the data -> using CORS
	2. Identity : Verify the entity that making the request is true -> Credentials, MFA, OAuth
5. Non-repudiation
6. Access control

| Security Services | Description                                                                                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Confidentiality   | Information only available to authorized entities (using encryption)                                                                                                                             |
| Integrity         | Assurance that data received is sent by authorised entity (Message Auth Code, Auth Encryption, Digital signature)                                                                                |
| Availability      | Make computing resources available for authorised users                                                                                                                                          |
| Authentication    | Ensure that communicating entities is true (Entity -> User/Process/Device, Origin -> Source) \| (PIN -> You know, Magnetic Swipe card -> You have, Biometrics, Fingerprints, and etc -> You are) |
| Non-repudiation   | Protection against denial by one parties -> proof that 2 parties are communicating each other (Ensure both parties cant deny their actions) \| (Digital Signature)                               |
| Access control    | Prevention of unauthorised user so they cant use protected resources (File permissions, access control IAM)                                                                                      |
#### Security Mechanism
- Technical tools and techniques to implement security service
- Detect, prevent, recover from security attack
- 2 Type : 
	- Specific : Provide specific security services
	- Pervasive : Provide to general services

##### 1. Encipherment (Encryption)
- Hide or covers data
- Using mathematical algorithm
- Cryptography and Steganography techniques used
- Provide confidentiality service

	Hello crypto -> Enc -> `akhsbakjsbjkbssas`

##### 2. Data Integrity
- Protect against modification of data
- Provides data integrity
- Use hashing functions to ensure it

##### 3. Digital Signature
- Ensure the sender can sign the data, and receiver can verify
- Verify the authenticity of digital messages
- Asymmetric Cryptography
- Provides non-repudiation

##### 4. Access control
- Client information to decide access grant for some resources owned by a system

##### 5. Authentication Exchange
- Ensure both parties identity -> Verified
- Using username,password
- Public key infrastructure
- SSO
- OAuth
- OpenID Connect

##### 6. Traffic Padding
- Insertion of bits into gaps in data stream -> Make traffic analysis attempts harder

##### 7. Routing Control
- Continuously change different available routes between sender and receiver 
- Make traffic analysis on particular router harder

##### 8. Notarization
- 3rd party to control communication between the two parties
- Provide non-repudiation service
- Ensure request sent by both parties, so noone can deny it
