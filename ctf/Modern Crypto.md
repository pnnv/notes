### Modern Cryptography
To get really good at crypto --> [this](https://www.hoppersroppers.org/roadmap/training/crypto.html)

#### Symmetric Encryption:
It is a type of encryption where same key is used for both encryption and decryption process. In other words, sender and receiver have the same key which they use to encrypt and decrypt the message.

#### Asymmetric encryption:
Also called Public-Key encryption. It allows us to establish secure communications even we have no opportunity to agree on a secret key ahead of time or via another communication channel. This is crucial for secure transactions over the internet. 

- The magic of public key cryptography derives from three important points:
	- A message may be encrypted with a private key and then decrypted with the corresponding(paired) public key, OR it can be encrypted with a public key and then decrypted with the corresponding private key.
	- A message encrypted with a certain public key can ONLY be correctly decrypted with the corresponding private key, and vice versa.
	- Because only private key needs to be protected, public keys can be shared openly, and therefore the limitation of symmetric encryption is alleviated.

**Encrypted Communications:**
In this scenario, Alice encrypts the message with Bob's public key which then Bob decrypts with his own private key.

- This solves the confidentiality problem for Alice, but how does Bob know that he was sent the right message from the right person?

**Authenticated Communications:**
In this scenario, Alice encrypts her message with her private key. Bob decrypts the message with Alice' public key and therefore Bob can be sure about the sender of the message.

When we combine these two methods into one, we get **Confidential and Authenticated Communications**.

### RSA Encryption
- more about RSA in [[RSA]].
(Rivest, Shamir & Adleman Encryption)
- General: The RSA encryption scheme provides commutative, asymmetric encryption.
- Math Description: The public key consists of two large integers (e, n) and the private key consists of two large integers (d, n). *Note that the second number n is the same in both!* The three numbers e, d and n are related in a special way, which requires a bit more mathematics to go into.
	- n is guaranteed to be the product of two primary numbers, i.e. *n = pq* for two primes *p* and *q*. If you know e and n, and you've found factorization of of n into pq, you can compute d easily.
	- So, the security of RSA requires that the factoring a large integer is difficult.
	- Today RSA might use 4096-bit number for n. Nobody currently knows how to factor the numbers of that size quickly, which is to say that RSA is pretty secure.

#### The security of RSA
- **Finding prime factors of the modulus.** It is always *possible* to crack RSA by computing someone's private key from their public key. All it takes is being able to factor the modulus (the number n that's common to both public and private key) into its two prime factors. However, if the modulus is big enough, even though it will be *possible* to do the factorization, it will not be *feasible*-- meaning the time/ computing-power required to do it is simply too great.

#### CAC knows crypto
> CAC stands for Certificate Authority Certificate. It is a third party organization responsible for issuing digital that are responsible for verifying authenticity and integrity of the public key and its associated identity.

CAC supports a number of different cryptographic algorithms, including:
Hashing: **SHA-512**
Symmetric encryption: **AES-256**
Asymmetric Encryption: **RSA-2048**
... and others.

Included on out CAC are public/private key pairs that we can use to decrypt e-mails intended only for us, and to digitally sign documents.

- **Just increase the key size:** RSA has been used since 1970 because as the computers get faster, we can simply use a bigger (and therefore harder to factor) numbers for moduli in our RSA keys.
- **N-bit RSA** means 'n' bits is the modulus size. Decades ago we used to have 512-bit RSA keys which were deemed pretty secure, since then the computing powers have increased by a thousand-fold and today we use 2048-bit RSA key which are considered pretty secure.

#### Digital Signatures Introduction

- **The signature:** Alice does the following 
	- Computes the hash of the contract agreement
	- Alice encrypts that hash with the private key
	- sends the result (which is the "digital signature"), along with the contract (which itself needs not be encrypted), to the Bob.
- **The Check:** Anyone can take the contract, hash it, and compare the result with what you get when you decrypt the digital signature with Alice's public key. If it matches then the contract must be exactly the same as the Alice sent, because :
	- Alice must've sent it, because only Alice can encrypt something that decrypts properly with her public key.
	- The contract can't have been modified, because the hash value would've changed


#### Man-in-the-Middle Attack Introduction

- **The Problem:** Asymmetric encryption is almost magical because --- you create security out of insecurity. However, there is still one weakness that's fundamental: *certifying the connection between a public key and its associated identity.*
- Example:
	- Hi, I'm Bob and my public key is
	`(106d231ecc13338084a1b857bb82a20b,a265d9387a8a395527c98eeb024806dd)`
How do we know that the public key really belongs to the guy you know as "Bob"? While we can be sure that the message can only be decrypted by the one who has the corresponding private key the weakness is the fact that we have to *trust* the source through which we are getting the public key.