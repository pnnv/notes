# RSA
RSA is one of the most common modern cryptosystems, known for its public and private key encryption. If we see public and private keys, there is a strong chance that it's an RSA problem, or at least RSA derived.

#### [What is RSA?](https://ctf101.org/cryptography/what-is-rsa/)
I've written about it in [[Modern Crypto]].

#### Implementation:
RSA follows 4 steps to be implemented:

##### Key Generation
>Note:
>In This example we are using _Carmichael's_ totient function where λ(n) = lcm(λ(p), λ(q)), but _Euler's_ totient function is perfectly valid to use with RSA. Euler's totient is φ(n) = (p − 1)(q − 1)

1. Choose two prime numbers such as:
	- p = 61 and q = 53
2. Find n:
	- n = pq = 3233
3. Calculate λ(_n_) = lcm(_p_-1, _q_-1)
	- λ(3233) = lcm(60, 52) = 780
4. Choose a public exponent such that 1 < _e_ < λ(_n_) and is coprime (not a factor of λ(_n_)).
   The standard in most cases is 65537, but we will be using
   - e = 17
5. Calculate *d* as the modular multiplicative inverse or in english find *d* such that _d_ x _e_ mod λ(_n_) = 1:
	- _d_ x 17 mod 780 = 1
	- *d* = 413
Now we have public key of (3233, 17) and a private key of (3233, 413)

##### Encryption

With the public key, *m* can be encrypted trivially
The ciphertext is equal to _m^e_ mod _n_ or:
c = m^17 mod 3233

##### Decryption

With the private key, *m* can be decrypted trivially as well
The plaintext is equal to *c^d* mod n or:
_m_ = _c^413_ mod 3233

#### Exploitation

**Attacks:**
- Weak public key factorization
- Wiener's attack
- Hastad's attack (Small public exponent attack)
- Small q (q < 100,000)
- Common factor between ciphertext and modulus attack
- Fermat's factorisation for close p and q
- Gimmicky Primes method
- Past CTF Primes method
- Self-Initializing Quadratic Sieve (SIQS) using Yafu
- Common factor attacks across multiple keys
- Small fractions method when p/q is close to a small fraction
- Boneh Durfee Method when the private exponent d is too small compared to the modulus (i.e d < n0.292)
- Elliptic Curve Method
- Pollards p-1 for relatively smooth numbers
- Mersenne primes factorization