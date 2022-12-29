**Cryptographic primitives** 
- They are the basic building blocks of a security protocol or system
- They are used for securing a blockchain ecosystem
- They provides services like
	- Confidentiality
	- Integrity
	- Authentication
	- Non-repudiation
	- Accountability

**Security protocol** 
- It is a set of steps taken to achieve the required security goals by utilizing appropriate security mechanism
- Various types of security protocols
	- Authentication protocols
	- Non-repudiation protocols
	- Key management protocols

Taxonomy of Cryptographic Primitives :

![[cryptographic-primitives-taxanomy.svg]]

# Symmetric Cryptography

- Same key is used to encrypt and decrypt the data
- Also known as **shared key cryptography** or **secret key cryptography**
- The key must be agreed upon before the data exchange takes place
- There are two types of symmetric ciphers :
	1. Stream Cipher
		- RC4
		- A5
	2. Block Cipher
		- Data Encryption Standard (DES)
		- Advanced Encryption Standard (AES)

### Stream Ciphers
- They apply encryption algorithms on a bit-by-bit basis (one bit at a time) to a plaintext using a keystream
- There are two types of stream ciphers
	1. **Synchronous stream ciphers**
		- the keystream is dependent only on the key
	2. **Asynchronous stream ciphers**
		- the keystream is also dependent on the encrypted data
- Encryption and decryption are the same function because they are simple modulo-2 addition or XOR operations
- Security and Randomness of the keystream is fundamentally important
- Techniques ranging from pseudorandom to true random number generators have been developed to generate random numbers
- It is very important that all the key generators be cryptographically secure

![[stream-cipher.svg]]

# Data Encryption Standard

# Advanced Encryption Standard