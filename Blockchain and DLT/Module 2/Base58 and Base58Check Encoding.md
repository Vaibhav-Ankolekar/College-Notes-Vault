# Base58 and Base58Check Encoding

- To represent long numbers in a compact way using fewer symbols, computer systems use mixed-alphanumeric representations with a base higher than 10
- Traditional decimal systems uses 10 numerals from 0 to 9
- Hexadecimal system uses 16, with the letters A to F as six additional symbols
- Number represented in hexadecimal format is shorter than the equivalent decimal representation
- Even more compact, Base64 representation uses 26 lowercase letters, 26 capital letters, 10 numerals and 2 more characters `+` and `/`
---
- Base56 is a text-based binary-encoding format developed for use in bitcoin and used in many cryptocurrencies
- It offers a balance between compact representation, readability, and error detection and prevention
- Base56 is subset of Base64
- It uses upper- and lower-case letters and numbers but omitting characters that are frequently mistaken for one another and can appear identical when displayed in certain fonts
- Base56 is Base64 without the 0 (zero), O (capital o), l (lower L), I (capital i) and symbols `+` and `/`
- Basically, it is a set of lowercase and capital letters and numbers without the four (0, O, l, I)
---
- Base58Check is used to add extra security against typos or transcription errors
- It is a Base58 encoding format which has a built-in error-checking code
- Checksum is an additional four bytes added to the end of the data that is being encoded
- The checksum is derived from the hash of the encoded data and can be used to detect and prevent transcription and typing errors
- The decoding software will calculate the checksum of the data and compare it to checksum included in the code
- This prevents a mistyped bitcoin address from being accepted by the wallet software as a valid destination, an error that would otherwise result in loss of funds
---
- To convert data (a number) into a Base58Check format, we first add a prefix to the data, called the "version byte"
- In case of bitcoin address, the prefix is zero (0x00 in hex), whereas the prefix used when encoding a private key is 128 (0x80 in hex)
- Next, we compute the "double-SHA" checksum, meaning we apply the SHA256 hash algorithm twice on the previous result (prefix and data)
$$checksum = SHA256(SHA256(prefix+data))$$
- From the resulting 32-bytes hash, we take only the first four bytes
- These four bytes serve as the error-checking code or checksum
- The checksum is appended to the end
- The result is composed of three items: a prefix, the data, and a checksum
- This result is encoded using the Base58 alphabet
---
![[base58check.svg]]