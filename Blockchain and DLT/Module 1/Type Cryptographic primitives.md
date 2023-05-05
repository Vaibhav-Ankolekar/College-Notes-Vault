# Type Cryptographic primitives

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

![[stream-cipher.svg | center]]

### Block Ciphers
- They break up the plaintext to be encrypted into blocks of a fixed length and apply the encryption algorithm block-by-block
- They use *Feistel cipher* design strategy
- Feistel ciphers are based on the Feistel network
- Feistel network structure is based on the idea of combining multiple rounds of repeated operations to achieve desirable cryptographic properties known as *confusion* and *diffusion*
- They operate by
	- dividing  data into two blocks and
	- processing these blocks via keyed *round functions* in iterations to provide sufficient pseudorandom permutation
- Confusion property
	- It makes the relationship between encrypted text and plaintext complex
	- It is achieved by substitution
	- *A* in plaintext is replaced by *X* in encrypted text
	- The substitution is performed using lookup tables called *S-boxes*
	- It is required to make finding the encrypted key very difficult, even if many encrypted and decrypted data pairs are created using same key
	- It is achieved by transposition or permutation
- Diffusion property
	- It spread the plaintext statistically over the encrypted data
	- Even if a single bit is changed in the input text, it results in changing at least half of the bits in the ciphertext
- Advantage of using Feistel cipher
	- encryption and decryption operations are almost identical
	- only requires a reversal of the encryption process to achieve decryption
- Various modes of operation for block cipher
	- Electronic Code Block (ECB) mode
	- Cipher Block Chaining (CBC) mode
	- Output Feedback (OFB) mode
	- Counter (CTR) mode

**Block Encryption mode**
- Plaintext is divided into blocks of fixed length
- Then encryption function is applied to each block
- most common block encryption modes are
1. **Electronic Code Book (ECB)**
	- Basic mode of operation
	- Encryption algorithm is applied one-by-one to each block of plaintext to produced encrypted data
	- It should not be used in practice as it is insecure and can reveal information
	![[electronic-code-book.svg]]
	- Plaintext P provided as an input to the block cipher encryption function, along with a key KEY and ciphertext C is produced as an output
	
2. **Cipher Block Chaining**
	- Each block of plaintext is XOR'd with the previously-encrypted block
	- It used Initialization Vector (IV) to encrypt the first block and it is randomly chosen
	![[cipher-block-chaining.svg]]

3. **Counter mode**
	- It uses block cipher as a stream cipher
	- A unique nonce is supplied that is concatenated with the counter value to produce a *keystream*
	![[counter-mode.svg]]
	- **Keystream generation mode**
		- The encryption function generated a keystream that is then XOR'd with the plain stream to achieve encryption

**Message authentication mode**
- An encryption function results a *Message Authentication Code (MAC)*
- MAC is a cryptographic checksum that provides an integrity service
- Most common method : CBC-MAC where a part of the last block of the chain is used as a MAC
- MAC can be used to ensure that if a message is modified by an unauthorized entity
- The message is encrypted with a key using MAC function
- The resultant message and MAC of the message is then sent to the receiver
- The receiver can check by encrypting the received message with the key and comparing it with the received MAC
- If they both match, then the massage has not been modified by unauthorized user thus integrity service is provided
- If they both don't match, then it means that message is modified by unauthorized entity during the transmission

**Cryptographic hash mode**
- Hash functions are primarily used to compare a message to a fixed-length digest
- Here, block ciphers are used as a compression function to produce a hash of plaintext

# Data Encryption Standard

- It was introduced by the U.S. National Institute of Standards and Technology (NIST) during 1980s
- It does not prove to be very resistant to brute force attacks due to advances in technology
- In 1998, Electronic Frontier Foundation (EFF) broke DES using a special-purpose machine called EFF DES cracker (or *Deep Crack*)

# Advanced Encryption Standard