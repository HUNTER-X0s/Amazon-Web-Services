AWS SSL-TLS



Secure Sockets Layer and Transport Layer Security 

Cryptographic protocols designed to provide secure communication over a computer network





TLS is the successor to SSL. 





How SSL/TLS Secure Data ?

It encrypts data and ensures its integrity, confidentiality, and authenticity between a client and a server. 





To ensure confidentiality the data is only accessed by the client server and encryption is used. 

To ensure integrity, data is not modified in between, hashing is used for it. 

To ensure authentication, verifying the identity of the parties who they are supposed to be, certificates are used here. 





Encryption :

converting the plain text information into coded form, (cipher text). 





* Encrypt DEMO to GHPR, shift each character by three forward. 
* Decrypt GHPR to DEMO, shift each character by three backward. 





Encryption types: symmetric and asymmetric 





Symmetric Encryption :

* Same key is used for both encryption and decryption.
* Encrypt DEMO to GHPR, shift each character by three forward. Key = 3. 
* Decrypt GHPR to DEMO, shift each character by three backward. Key = 3
* Faster and more efficient, suitable for large data.
* Challenging Key Distribution: Single key must be kept secret.





Asymmetric encryption :

* Different key is used for encryption and decryption.
* Encrypt DEMO to GHPR. Shift each character by 3 forward.  key=3
* Decrypt GHPR to DEMO. Shift each character by 23 forward. Key is 23. 
* It is more secure. 
* It is slower and suitable for small data.
* Simplified fee distribution, secured even if the public key is shared





\-> The client will use the public key to encrypt the message sent by him and the server will use the private key to decrypt the message. 





Hybrid encryption: 

* It combines the strengths of both symmetric and asymmetric encryption to achieve efficient and secure communication. 
* Asymmetric encryption is used to securely exchange the symmetric key between the parties. 
* Once the symmetric key is securely exchanged, it is used to encrypt and decrypt the actual data. 
* Symmetric encryption is faster and more efficient, making it ideal for encrypting large amounts of data. 





Some algo examples:

Asymmetric:- 

* DSA
* RSA
* ECC
* ECDH

Symmetric:-

* AES
* 3DES
* RC4





How real life AES encryption looks like...

Message: DEMO



Key 256 bit HEX:

cb5a6cefcf5b7e88f9bff6f27f32d6095a86db829d8518cf8e db6af2740ff8eb



Initialiation Vector (IV):

a8d246bb6ebae2b0e7651843b3053384



AES-256-CBC Encryption:

8?Q3?B??Z)?07h??







HASHING : 

Hashing is the process of converting data into a fixed-size string of characters, as a sequence of numbers and letters.



DEMO --> 37 (4+5+13 + 15 = 37)

ABCDEFGHIJKLMNOPQRSTUVWXYZ





MESSAGE AUTH CODE (MAC)

Combining MESSAGE + CODE

Message: DEMO

Secret Key: key123

DEMOkey123 --> 84

ABCDEFGHIJKLMNOPQRSTUVWXYZ





Most Common Hashing Algo

* MD5 (Message Digest Algorithm 5) (128bits)
* SHA (Secure Hash Algorithm)

&#x20;- sha-1

&#x20;- sha-2/3 224 256 384 512

Hash-based Message Authentication Code (sha256hmac)





* Confidentiality

Data is only accessed by client/server

Encryption



* Integrity

Data is not modified in between

Hashing



* Authentication

Verifying the identity of the parties who they are supposed to be.

certificates







Certificate Authority :

* A Certificate Authority (CA) is a trusted organization that issues digital certificates to verify the identity of websites and enable secure, encrypted communication over the internet.
* CAs ensure the authenticity and integrity of the SSL certificates they provide.









1\. PEM Format

* Encoding: Base64 (readable text format)
* Extensions: .pem, .crt, .cer
* Usage: Web servers and email
* Private Key: No (unless it is a specific key file)

2\. DER Format

* Encoding: Binary (raw data format)
* Extensions: .der, .cer
* Usage: Java platforms and binary data handling
* Private Key: No

3\. PKCS#7 Format

* Encoding: Base64 or Binary
* Extensions: .p7b, .p7c
* Usage: Certificate chains
* Private Key: No

4\. PKCS#12 Format

* Encoding: Binary
* Extensions: .p12, .pfx
* Usage: Exporting and importing certificates along with keys
* Private Key: Yes













1\. Client Hello

Client: "Hello, I support these SSL/TLS versions and cipher suites..."



2\. Server Hello

Server: "Hello, I choose this SSL/TLS version and cipher suite..."



3\. Server Certificate

Server: "Here is my certificate with my public key..."



4\. Certificate Verification

Client: "I verify your certificate..."



5\. Key Exchange

Client: "I encrypt a pre-master secret with your public key..."

Server: "I decrypt the pre-master secret with my private key..."



6\. Session Key Generation

Both: "We generate a session key using the pre-master secret..."



7\. Client Finished

Client: "Handshake complete (encrypted with session key)..."



8\. Server Finished

Server: "Handshake complete (encrypted with session key)..."



9\. Secure Communication

Both: "Let's communicate securely using the session key..."























&#x20;

## Remember the three security goals

TLS protects a connection through **confidentiality** (encryption), **integrity** (tamper detection), and **authentication** (certificate validation). Hashing alone is not encryption: a hash is a one-way digest; a MAC adds a secret key to authenticate data; a digital signature uses asymmetric keys to verify a signer and integrity.

The handshake in the original notes is a simplified teaching picture. Modern TLS versions negotiate algorithms and use authenticated key exchange to derive session keys; they do not generally work as the old RSA “encrypt a pre-master secret with the public key” sketch suggests. Bulk application data uses efficient symmetric encryption after the handshake. Use current TLS configurations and managed certificates rather than implementing cryptography yourself.

**Recall check:** A site encrypts traffic but presents a certificate for the wrong hostname. Which goal fails? Authentication/identity verification, even though encryption may still occur.

**Console practice:** [ACM certificate walkthrough](guides/aws-console/certificate-manager.md) · [CloudFront walkthrough](guides/aws-console/cloudfront.md)

