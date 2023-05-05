# Elliptic Curve Cryptography

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

![[ecc_curve.png | 300]]

- Bitcoin uses a specific elliptic curve and set of mathematical constants as defined in a standard called `secp256k1`
- The `secp256k1` curve is defined by

$$y^2 = \frac{x^3+7}{F_p} \;\;\;\;\; or \;\;\;\;\; y^2 \; mod \; p = (x^3+7) \; mod \; p$$

- The $mod \; p$ indicates that this curve is over a finite field of prime order $p$, also written as $F_p$ where $p = 2^{256} - 2^{32} - 2^9 - 2^8 - 2^7 - 2^6 - 2^4 - 1$
---
- This curve is defined over a finite of prime order instead of over the real numbers
- It looks like a pattern of dots scattered in two dimensions, which makes it difficult to visualize
- The math is identical to that of an elliptic curve over real numbers
---
![[ecc_17.svg | 450]]
- The figure shows the same elliptic curve over a much smaller finite field of prime order 17, showing a pattern of dots on a grid
---
For example
- the following is a point P with coordinates (x,y) that is a point on the `secp256k1` curve :

```python
P = (55066263022277343669578718895168534326250603453777594175500187360389116729240,
32670510020758816978083085130507043184471273380659243275938904335757337482424)
```
- Using Python to confirm that this point is on the elliptic curve
```python
>>> p =
115792089237316195423570985008687907853269984665640564039457584007908834671663
>>> x =
55066263022277343669578718895168534326250603453777594175500187360389116729240
>>> y =
32670510020758816978083085130507043184471273380659243275938904335757337482424
>>> (x ** 3 + 7 - y**2) % p
0
```
---
- In elliptic curve math, there is a point called the *point at infinity* which roughly corresponds to the role of zero in addition
- It is represented by $x = y = 0$
- There is also a $+$ operator called *addition*, which have some properties similar to the traditional addition of real numbers
- Given two points $P_1$ and $P_2$ on the elliptic curve, there is a third $P_3 = P_1 + P_2$, also on the elliptic curve
- $P_3$ is calculated by drawing a line between $P_1$ and $P_2$
- This line will intersect the elliptic curve in exactly one additional place
- Call this point $P'_3 = (x,y)$
- Then reflect in the x-axis to get $P_3 = (x,-y)$
---
- If $P_1$ and $P_2$ are the same point, the line between $P_1$ and $P_2$ should extend to be the tangent on the curve at the point $P_1$
- This tangent will intersect the curve in exactly one new point
- We can use calculus techniques to determine the slope of the tangent line
---
- If $P_1$ and $P_2$  have the same x values but different y values then the tangent line will be vertical, in which case $P_3$ = *point at infinity*
- If $P_1$ is the *point at infinity* then $P_1 + P_2 = P_2$
- If $P_2$ is the *point at infinity* then $P_1 + P_2 = P_1$
- This shows the *point at infinity* plays the role of zero
---
- $+$ is associative, which means that $(A + B) + C = A + (B + C)$
- We can write $A + B + C$ without parentheses without ambiguity
---
Multiplication
- For a point P on the elliptic curve, if k is a whole number, then
$$
kP = P + P + P + ... + P \;\; (k \; times)
$$
---
**Generating a Public Key**
- Randomly generated number *k* is the private key
- The *generator point G* is the predetermined point on the curve
- The number *k* and point *G* is multiplied to produce another point son the curve which is the public key *K*
- The generator point is specified as part of the `secp256k1` standard and is always same for all keys in bitcoin
$$
K = k * G
$$
- where *k* is the private key, *G* is the generator point and *K* is the resulting public key
- As the generator point is always the same for all bitcoin users, a private key *k* multiplied with *G* will always result in the same public key *K*
- The relationship between *k* and *K* is fixed, but can only be calculated in one direction, from *k* to *K*
- That's why bitcoin address (derived from *K*) can be shared with anyone and does not reveal the user's private key (*k*)
- A private key can be converted into public key, but a public key cannot be converted back into a private key because the math only works one way
---
For example
- We take the private key *k* generated and multiply it with generator point *G* to find the public key *K*:
```
K = 1E99423A4ED27608A15A2616A2B0E9E52CED330AC530EDCC32C8FFC6A526AEDD * G
```
- Public key *K* is defined as a point `K = (x, y)`, where
```
x = F028892BAD7ED57D2FB57BF33081D5CFCF6F9ED3D3D7F159C2E2FFF579DC341A
y = 07CF33DA18BD734C600B96A72BBC4749D5141C90EC8AC328AE52DDFE2E505BDB
```
---
- Finding the multiple *kG* is same as adding *G* to itself *k* times in a row
- In elliptic curves, adding a point to itself is equivalent to 
	- drawing a tangent line on the point
	- finding where it intersects the curve again 
	- reflecting that point on the x-axis

![[ecc_multiply.png | 500]]

- Visualizing the multiplication of a point G by an integer k on an elliptic curve
- It shows the process of deriving G, 2G, 4G, as geometric operation on the curve