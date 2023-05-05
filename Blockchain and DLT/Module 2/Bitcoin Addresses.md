- It is string of digits and characters that can be shared with anyone who wants to send you money
- It is produced from public keys
- It consist of a string of numbers and letters, beginning with the digit `1`
- example, `1J7mdg5rbQyUHENYdx39WVWK7fsLpEoXZy`
---
- Bitcoin address is derived from the public key through the use of one-way cryptographic hashing
- Secure Hash Algorithm (SHA) and RACE Integrity Primitives Evaluation Message Digest (RIPEMD) are used to make bitcoin address from public key
- Specifically SHA256 and RIPEND160 are used
---
- Starting with public key K, we compute the SHA256 and then compute the RIPEND160 hash of the result, producing a 160-bit (20-byte) number:
$$ A = RIPEMD160(SHA256(K)) $$
- where K is the public key and A is the resulting bitcoin address
---
- Bitcoin addresses are always encoded as **Base58Check** which uses 58 characters and a checksum
- This helps for
	- human readability
	- avoid ambiguity
	- protect against errors in address transcription and entry
---
![[public_key_to_bitcoin_address.svg]]
Conversion of a public key into a bitcoin address


