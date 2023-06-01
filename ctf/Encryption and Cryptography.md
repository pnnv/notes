There are variety of common cryptography problems such as:
1. Cipher-text only
2. Cipher-text + private key and algorithm
3. Cipher-text and custom source code
4. Cipher-text + public key and algorithm

## Classic Ciphers

#### Caesar

The most common and most famous is Caesar cipher. The easiest way to understand Caesar cipher is to think of cycling the position of letters. In a Caesar cipher of shift 3, A becomes D, B becomes E and so on.

- Standard Caesar has the alphabets shifted by 3 to the right.
- ROT13 is just Caesar cipher with a shift of 13.

#### Substitution Cipher

All the substitution ciphers can be cracked using the following steps:

- Scan through the cipher, looking for single-letter words, they're almost definitely A or I.
- Count how many times each symbol appears in the puzzle. The most frequent symbol is probably E. It could also be T, A, or O, especially if the cryptogram is fairly short.
- Pencil in the guesses over the cipher-text. If the words don't appear to be revealing themselves, be prepared to change those guesses.
- Look for apostrophes. They're generally followed by S, T, D, M, LL, or RE.
- Look for repeating letter patterns. They may be most common letter groups, such as TH, SH, RE, CH, TR, ING, ION, and ENT.
- Try to decipher two-, three-, and four letter words.
	- two letter words almost always have one vowel and one consonant, the five most common two-letter words in order of frequency, are OF, TO, IN, IS, and IT.
	- The most common three-letter words are THE, AND, FOR, WAS, and HIS.
	- The most common four-letter word is THAT.

#### Frequency Analysis
Frequency Analysis is the study of the distribution (and count) of the letters in text. Analysis of frequencies helps cryptanalysis and decrypting substitution-based ciphers using the fact that some letters apparitions are varying in a given language.
- In English, the letters E, T or A are common while Z and Q are rare.

Frequency analysis generates a Histogram that allows decrypting a text by comparing letters frequencies in a plain text message with letters frequencies in the ciphered message.

|   |   |   |   |
|---|---|---|---|
|E|12.7 %|M|2.4 %|
|T|9.1 %|W|2.4 %|
|A|8.2 %|F|2.2 %|
|O|7.5 %|G|2.0 %|
|I|7.0 %|Y|2.0 %|
|N|6.7 %|P|1.9 %|
|S|6.3 %|B|1.5 %|
|H|6.1 %|V|1.0 %|
|R|6.0 %|K|0.8 %|
|L|4.0 %|J|0.2 %|
|D|4.3 %|X|0.2 %|
|C|2.8 %|Q|0.1 %|
|U|2.8 %|Z|0.1 %|


- A list of classical ciphers can be found on [this website.](http://practicalcryptography.com/ciphers/classical-era/) 

#### Vignere Cipher
It is a polyalphabetic substitution cipher that is natural evolution of Caesar cipher.

In Vignere cipher, a message is encrypted using a secret key, as well as an encryption table (called a Vignere square, Vignere table or tabula recta). The tabula recta typically contains the 26 letters of the Latin alphabet A to Z on top of each column, and repeated along the left side at the beginning of each row. Each row of the square has the 26 letters of the Latin alphabet, shifted one position to the right in a cyclic way as the rows progress downwards.

IMPROVE YOUR PUZZLE SOLVING SKILLS

After finalizing the plaintext, the person encrypting would then pick a secret key, which would help encrypt and decrypt the message. Our example secret key here is:

BOXENTRIQ

The next step is repeating the secret key enough times so its length matches the plain text.

IMPROVE YOUR PUZZLE SOLVING SKILLS
BOXENTR IQBO XENTRI QBOXENT RIQBOX

Once the two lines are split into five-letter groups, start encrypting. Take one letter from the plaintext group and a letter from the secret key group (we’re going to start with I and B), and find the entry in the tabula recta where the row and column intersect. For this example, the first letter of the encrypted cipher text is J. 


#### XOR

Characters including letters and numbers are represented by a byte, that byte can be converted into different bases in order to obscure the text.

The XOR or *exclusive or* is a bitwise operation indicated by `^` and shown by the following truth table:

|A|B|A ^ B|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|

So what XOR'ing bytes in the action `0xA0 ^ 0x2C` translates to is:

|1|0|1|0|0|0|0|0|
|---|---|---|---|---|---|---|---|
|0|0|1|0|1|1|0|0|
|1|0|0|0|1|1|0|0|

**Encryption**:
XOR is a cheap way to encrypt data with a password. Any data can be encrypted using XOR as shown in the following Python example:

```python
>>> data = 'CAPTURETHEFLAG'
>>> key = 'A'
>>> encrypted = ''.join([chr(ord(x) ^ ord(key)) for x in data])
>>> encrypted
'\x02\x00\x11\x15\x14\x13\x04\x15\t\x04\x07\r\x00\x06'
>>> decrypted = ''.join([chr(ord(x) ^ ord(key)) for x in encrypted])
>>> decrypted
'CAPTURETHEFLAG'
```

**Exploiting XOR Encryption**:

