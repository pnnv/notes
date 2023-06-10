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

### # X-CTF Quals 2016 - Fact0r!z3 and Fact0r!z3_aga!n (Crypto)

Category: Crypto
Description: Can you decrypt this:
And we are given an `Encrypted.zip`.

The solution is to factorize the modulus value of the RSA public key, allowing you to calculate the decryption key.

```
→ tar zxvf 4b5978caa2cef859f97d0443ada4db40
x 8987609732e4da707a5d7563bd619f53
x flag.enc
```
It's quite obvious that we're suppose to decrypt `flag.enc` in order to obtain then flag.

Using `openssl`, we can obtain the content of the public key.

```bash
$ openssl rsa -text -pubin -in 8987609732e4da707a5d7563bd619f53

Public-Key: (447 bit)
Modulus:
    48:e8:f0:19:5d:8c:7b:0a:f1:4b:7f:ae:1b:d9:f8:
    e4:08:77:44:8e:66:44:e9:f5:83:cd:76:57:d2:36:
    5c:7f:83:51:99:08:e1:1f:6e:41:35:bb:f7:6a:76:
    b9:80:cc:d1:e6:99:43:dd:39:f5:3d
Exponent: 65537 (0x10001)
writing RSA key
-----BEGIN PUBLIC KEY-----
MFMwDQYJKoZIhvcNAQEBBQADQgAwPwI4SOjwGV2MewrxS3+uG9n45Ah3RI5mROn1
g812V9I2XH+DUZkI4R9uQTW792p2uYDM0eaZQ9059T0CAwEAAQ==
-----END PUBLIC KEY-----
```

Using some python kungfu, we can obtain the integer value of the Modulus to give:

we can use the following program:

```python
hex_modulus = "48:e8:f0:19:5d:8c:7b:0a:f1:4b:7f:ae:1b:d9:f8:e4:08:77:44:8e:66:44:e9:f5:83:cd:76:57:d2:36:5c:7f:83:51:99:08:e1:1f:6e:41:35:bb:f7:6a:76:b9:80:cc:d1:e6:99:43:dd:39:f5:3d"
decimal_modulus = int(hex_modulus.replace(":", ""), 16)

print(decimal_modulus)
```
it gives us: `207006830488235668671955689390815624796833363161842587562758966652474780634716637447867252305688653008916026906416134119860202636965181`

Throw this into `factordb.com`, and we can see that the modulus value is very easily factorized.

```
p = 3133337  
q = 66065932419090467661779020064172996647610315507665657272983712461339070975996720891454462863614304177595970974847625429329881413  
```

Using RSAtool.py we can reconstruct the private key file, allowing us to decrypt `flag.enc`.

```bash
→ python ~/CTF/tools/rsatool.py -p 3133337 -q 66065932419090467661779020064172996647610315507665657272983712461339070975996720891454462863614304177595970974847625429329881413 -e 65537 -o key.pem
Using (p, q) to initialise RSA instance

n =
48e8f0195d8c7b0af14b7fae1bd9f8e40877448e6644e9f583cd7657d2365c7f83519908e11f6e41
35bbf76a76b980ccd1e69943dd39f53d

e = 65537 (0x10001)

d =
d94d65c2a8045044cdf2ffaeb5ad759f5bf0b8584bb61f3bd878aa47267f99994b86491e0a427c57
2f77adc1ad492131dc6db513b3b221

p = 3133337 (0x2fcf99)

q =
18663ff92c4c79e1a244f109ad859cecfb34d162303f3f6e525e411dfa723a7a18af3732239f058b
2e524d819a28c3d4e9c4d83a945

Saving PEM as key.pem

→ openssl rsautl -decrypt -inkey key.pem -in flag.enc
XCTF{S33MZ_L!K3_Y0U_fact0r!zed_!T}
```
The flag is `XCTF{S33MZ_L!K3_Y0U_fact0r!zed_!T}`.

----
Some RSA problems will not be solved by default RSAtool runs. For those we will often need an extension names *Sage Math*