1. single key -> symmetric
2. pair of keys (public and private) -> asymmetric
3. public key crypto help address key distribution problem


##### Distribution of Public Keys
1. Public Announcement
	1. User distribute public keys (broadcast) to large community
		- Cant verify/auth the announcer
		- Vulnerable to masquerade attack
2. Publicly Available Directory
	1. User store public keys at public directory
	2. Controlled by trusted entity/organization
	3. Properties:
		1. {name,public-key} entries
		2. register securely with directory
		3. can replace key at any time
		4. periodically published
		5. accessed electronically
	4. Vulnerable to tampering/forgery
		1. because we cant verify the identity of the creator

###### Preventing Active Attack
1. Bob need to make sure, he has correct Alice public key
2. Bob need to test the truth of message from alice public key
3. Only Alice can produce message that can pass bob's test

- Bob should able to test the truth of message
- Only allice can make message, that can be verified by bob test


