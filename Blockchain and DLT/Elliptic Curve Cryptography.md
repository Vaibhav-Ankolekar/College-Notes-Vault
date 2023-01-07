- Elliptic Curve Digital Signature Algorithm or ECDSA is a cryptographic algorithm used by Bitcoin to ensure that funds can only be spent by their rightful owner
- Bitcoin uses elliptic curve multiplication as the basis for its cryptography
---
Elliptic curve multiplication
- It is a type of function called a *trap door* function
- It is easy to do in one direction (multiplication) and impossible to do in the reverse direction (division)
- Owner of private key can easily create public key and share it with the world knowing no one can reverse the function and calculate the private key from the public key
- This is the basis of unforgeable and secure digital signature that prove ownership of bitcoin funds
---
**Elliptic Curve Cryptography**
- It is based on discrete logarithm problem as expressed by addition and multiplication on the points of an elliptic curve
- It is used to generate public and private keys in the Bitcoin network
- Bitcoin uses a specific elliptic curve and set of mathematical constants as defined in a standard called `secp256k1`
- The `secp256k1` curve is defined by

$$y^2 = \frac{x^3+7}{F_p} \;\;\;\;\; or \;\;\;\;\; y^2 \; mod \; p = (x^3+7) \; mod \; p$$

- The $mod \; p$ indicates that this curve is over a finite field of prime order $p$, also written as $F_p$ where $p = 2^{256} - 2^{32} - 2^9 - 2^8 - 2^7 - 2^6 - 2^4 - 1$
---
- This curve is defined over a finite of prime order instead of over the real numbers
- It looks like a pattern of dots scattered in two dimensions, which makes it difficult to visualize
- The math is identical to that of an elliptic curve over real numbers
---
![[ecc_17.svg]]
- The figure shows the same elliptic curve over a much smaller finite field of prime order 17, showing a pattern of dots on a grid
---
