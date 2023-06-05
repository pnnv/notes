## Steganography

CTF image Stegangraphy checklist
[source](https://stegonline.georgeom.net/checklist)

[Stegosolve](https://github.com/eugenekolo/sec-tools/tree/master/stego/stegsolve/stegsolve)
[StegHide](http://steghide.sourceforge.net/)

Steganography is the practice of hiding data in plain sight. Steganography is often embedded in images or audio.

#### LSB Steganography

Files are made of bytes. Each byte is composed of eight bits.

Changing the least-significant bit (LSB) doesn't change the value very much.
So we can modify LSB without changing the file noticably. By doing so, we can hide a message inside.

*In images:*
The data is recorded in the least significant bit of a byte.
Decoding LSB steganography is exactly the same as encoding, but in reverse. For each byte, grab the LSB and add it to your decoded message. Once you’ve gone through each byte, convert all the LSBs you grabbed into text or a file. (You can use your file signature knowledge here!)


### CSAW Quals 2016: Watchword - Forensics 250
[source](https://github.com/krx/CTF-Writeups/blob/master/CSAW%2016%20Quals/for250%20-%20Watchword/jk_actual_writeup.md)
For this challenge we are given `powpow.mp4`

#### MP4 Analysis
There are two main things to get out of this file:

```
$ exiftool powpow.mp4
...
Artist                          : Stefan Hetzl
Title                           : aHR0cDovL3N0ZWdoaWRlLnNvdXJjZWZvcmdlLm5ldC8=
...
```

Stefan Hetzl is the author of `StegHide`, and the base64 decodes to `http://steghide.sourceforge.net/`. This is usually used with JPEGs.

Now we use the `foremost` tool and we get a png.

#### PNG Analysis
`steghide` doesn't work with `PNG`s, so we have to keep looking. File carving doesn't get us anywhere here, so it must be something else. *The PNG format is ideal for lossless compression*, so we use stegsolve next.
We save the blue LSB plane because it looks sus.

```
ff6c3fdc00008128 8c49230000202000  .l?....( .I#..  .
0002000080000ff6 d8008600048180e0  ........ ........
8038181208040201 40a0482c1c170783  .8...... @.H,....
81a0d07070281508 85c441e1188c421e  ...pp(.. ..A...B.
100804a2a1a8b44a 27190a04020170fc  .......J '.....p.
...
```

looking at the stream of bits we can see how the encoding works.

```
111111110110110000111111110111000000000000000...
|  FF  | |  D8  | |  FF  | |  E0  | |  00  | ...
```

There's just an extra bit placed after every encoded byte, so if we skip every 9th bit, when we convert binary to ascii, we should get the image.

It starts with `\xFF` which is what we'd want for a `jpeg`, but the rest is junk. The following python script:

```python
#!/usr/bin/env python
from PIL import Image
import sys

def b2a(b):
    s = ''
    while len(b) != 0:
        binbyte = b[:8]  # Get a byte
        s += chr(int(binbyte, 2)) # Convert it
        b = b[9:]  # Skip every 9th bit
    return s

# Load image data
img = Image.open(sys.argv[1])
w,h = img.size
pixels = img.load()

binary = ''
for y in xrange(h):
    for x in xrange(w):
        # Pull out the LSBs of this pixel in RGB order
        binary += ''.join([str(n & 1) for n in pixels[x, y]])
print b2a(binary)
```

```bash
$ ./lsb.py img1.png > img2.jpg
```

Voila! we get a jpg.

#### Using Steghide

So now we have a JPEG, but where's the password? Well, it's not there :( you can either run a dictionary attack or guess that the password is `password`.

```bash
$ steghide extract -sf img2.jpg -p password
wrote extracted data to "base64.txt".
$ cat base64.txt
W^7?+dsk&3VRB_4W^-?2X=QYIEFgDfAYpQ4AZBT9VQg%9AZBu9Wh@|fWgua4Wgup0ZeeU}c_3kTVQXa}eE
```

The encoded text is base85

```bash
$ python3
>>> import base64
>>> base64.b85decode('W^7?+dsk&3VRB_4W^-?2X=QYIEFgDfAYpQ4AZBT9VQg%9AZBu9Wh@|fWgua4Wgup0ZeeU}c_3kTVQXa}eE')
flag{We are fsociety, we are finally free, we are finally awake!}
```

### Pragyan CTF 2015: What you see is what you get.
[source](https://github.com/ctfs/write-ups-2015/tree/master/pragyan-ctf-2015/stegano/what_you_see_is_what_you_get)
We get a link to download `stego_50.jpg`.

Using `binwalk`, we see that the provided picture contains a zip archive:

```bash
$ binwalk stego_50.jpg
DECIMAL       HEXADECIMAL     DESCRIPTION
------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard  1.02
10541         0x292D          Zip archive data, at least v1.0 to extract, compressed size: 37,  uncompressed size: 37, name: "usethis"
10720         0x29E0          End of Zip archive
```

The zip file contains a `txt` file named `usethis`.
```bash
$ cat usethis
steghide.sourceforge.net/download.php
```
So we use `steghide` to extract additional hidden data in the picture:

```bash
$ steghide extract -sf stego_50.jpg
Enter Passphrase: 
```

We get the passphrase using `strings -a stego\_50.jpeg`
```bash
$ strings -a stego_50.jpg
JFIF
  %*5-%'2(  .?/279<<<$-BFA:F5;<9
  9& &99999999999999999999999999999999999999999999999999
[...]
RP!h
usethisUT
steghide.sourceforge.net/download.phpPK
usethisUT
Delta_Force\m/
```

So,the passphrase is `Delta_Force\m/`.
Which gives us `key_stego_1`.

```bash
$ steghide extract -sf stego_50.jpg
Enter Passphrase: (Delta_Force\m/)
wrote extracted data to "key_stego_1"
$ cat key_stego_1
Congrats! This was way too wasy :P

This is the key:

PrAgyaNCTF_sTeg1_key
```