### Modern Cryptography
#### Symmetric Encryption:
It is a type of encryption where same key is used for both encryption and decryption process. In other words, sender and receiver have the same key which they use to encrypt and decrypt the message.

#### Asymmetric encryption:
Also called Public-Key encryption. It allows us to estabilish secure communications even we have no opportunity to agree on a secret key ahead of time or via another communication channel. This is crucial for secure transactions over the internet. 

- The magic of public key cryptography derives from three important points:
	- A message may be encrypted with a private key and then decrypted with the corresponding(paired) public key, OR it can be encrypted with a public key and then decrypted with the corresponding private key.
	- A message encrypted with a certain public key can ONLY be correctly decrypted with the corresponding private key, and vice versa.
	- Because only private key needs to be protected, public keys can be shared openly, and therefore the limitation of symmetric encryption is alleviated.

**Encrypted Communications:**
In this scenario, Alice encrypts the message with Bob's public key which then Bob decrypts with his own private key.

- This solves the confidentiality problem for Alice, but how does Bob know that he was sent the right message from the right person?

**Authenticated Communications:**
In this scenario, Alice encrypts her message with her private key. Bob decrypts the message with Alice' public key and therefore Bob can be sure about the sender of the message.

When we combine these two methods into one, we get **Confidential and Authenticated Communications**.ts 

### RSA Encryption
(Rivest, Shamir & Adleman Encryption)
- General: The RSA encryption scheme provides commutative, asymmetric encryption.
- Math Description: The public key consists of two large integers (e, n) and the private key consists of two large integers (d, n). *Note that the second number n is the same in both!* The three numbers e, d and n are related in a special way, which requires a bit more mathematics to go into.
	- n is guaranteed to be the product of two primary numbers, i.e. *n = pq* for two primes *p* and *q*. If you know e and n, and you've found factorization of of n into pq, you can compute d easily.
	- So, the security of RSA requires that the factoring a large integer is difficult.
	- Today RSA might use 4096-bit number for n. Nobody currently knows how to factor the numbers of that size quickly, which is to say that RSA is pretty secure.

#### The security of RSA
- **Finding prime factors of the modulus.** It is always *possible* to crack RSA by computing someone's private key from their public key. All it takes is being able to factor the modulus (the number n that's common to both public and private key) into its two prime factors. However, if the modulus is big enough, even though it will be *possible* to do the factorization
