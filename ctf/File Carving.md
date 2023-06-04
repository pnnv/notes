# File Carving

There are ways to hide files inside other files, which is demonstrated in the following problem.

[source](https://github.com/HackThisSite/CTF-Writeups/tree/master/2017/EasyCTF/Zooooooom)
*Problem Statement*: Hekkerman is looking awfully spooky. That hekker glare could pierce a firewall. What can he see that you can't?
*Hint:* Sometimes there's more than meets the eye.

> Hekkerman is a jpg image and that is all we have to work with.

If we check the Hex for the image, we find three JPG footer bytes `FF D9` which means there are 3 jpgs in that one file.

We can use a tool called `scalpel` to extract the remaining jpgs.

```
$ scalpel -c scalpelConfig.txt hekkerman.jpg -o output
```


*Another Writeup*

[source](https://github.com/hoppersroppers/ctfWriteups/blob/main/CSAW15/FOR300-Mandiant/readme.md)
#### CSAW/FOR300-Mandiant

You are given file Mandient.pdf. It's a long legit looking file so we won't waste our time reading through it.

First step, like any other file format challenge, is to run scan tools on it like `binwalk` or `scalapel` and look for extra files that pop out.

```
binwalk Mandiant_c920fc463eaf996489749457abc9b2eb.pdf

DECIMAL       HEXADECIMAL     DESCRIPTION
----------------------------------------------------------------------
0             0x0             PDF document, version: "1.4"
106           0x6A            Zlib compressed data, best compression
```

After that we look for any anomalies in the file format.
- If a tool can find it for us, that is always the best option.
- If we can look at a file's specification, check the headers and know what's happening, that also works but requires a lot more knowledge.
- If we're going with luck, we will find the answer on a long enough timeline, but it will be painful
	- If we are going with luck, make sure to document what we've done so that when someone else tries to help, they don't have to try the same guesses that we did.
	- Google sheets are good for collaborative note taking.

In this case, It's a PDF, and plenty of tools exist. [`pdf-parser` is a good one](https://blog.didierstevens.com/programs/pdf-tools/). It comes preinstalled on some distros like Kali, for others we can get from [here](https://www.aldeid.com/wiki/Pdf-parser). If we don't have the tool available, we can  read through the [specs](https://www.adobe.com/content/dam/acom/en/devnet/acrobat/pdfs/PDF32000_2008.pdf) or using other tools but it will take longer.

Using our knowledge of PDF tools we can either go with:
- `pdf-parser`: this is somewhat straightforward as demonstrated in [this writeup]()
- If `pdf-parser` is not available to us we can also use `qpdf`. Use of `qpdf` is shown in [this writeup](https://github.com/ctfs/write-ups-2015/tree/master/csaw-finals-ctf-2015/forensic/mandiant).
	- `qpdf` is able to pull streams (and other parts of the complicated pdf file format) into plaintext for easy parsing using `$ qpdf --qdf --object-streams=disable`.
		- Read [this](http://qpdf.sourceforge.net/files/qpdf-manual.html#ref.filtered-streams) to understand what is going on.
	- After using this, we will be able to scan through or search content of the `.pdf` in a generally plaintext format which makes life easier.
		- We can search for the words *Embeddedfile*.

-----

Using `qpdf` and a common text editor, we can extract the embedded file (base64 encoded) in a simple manner:

```bash
$ qpdf --qdf --object-streams=disable Mandiant_c920fc463eaf996489749457abc9b2eb.pdf out.pdf
```

No matter the tool, if we scan through we'll find a very off lump of base64 text, which is the sign that we are on a right path.

Use the magic of base64 -decode and pipes (ensure to trim out new line characters with tr -d '\\n') to convert the base64 text into a new file.

After that  we scan through `out.pdf` searching for the keyword *Embeddedfile* and find a long-ass string encoded in base64.
Turns out it was a `.png` file.

```bash
$ base64 --decode out.pdf > out.png
```

```bash
$ binwalk out.png                                                                  

DECIMAL       HEXADECIMAL     DESCRIPTION
----------------------------------------------------------------------
0             0x0             PNG image, 610 x 467, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, compressed
160173        0x271AD         7-zip archive data, version 0.4
```

Looks like there's a 7Zip archive.
After unzipping it, we find `secret.txt` inside which there is a big block of base64, turns out it's another image (int `.jpeg` format).

`binwalk` gives us nothing about this image, so now we convert it to hex and look for abnormalities.

#### JPG Analysis.
Looking at the hex dump/ strings again, We can find more base64 data appended to the end of the image (two base64 strings to be precise).
After decoding the data it does not make sense and we can't go any further.
That is, until we get a hint to look for something called `Free File Camouflage`.
Sadly i can't download and install the required software right now but it's pretty straightforward from now on, we give the software our files and it gives us an executable, we run the executable and out pops the flag.
 
-----
## Intigriti CTF
[source](https://the-bilal-rizwan.medium.com/intigriti-ctf-writeup-737009900a42)
*The first hint*: The CTF starts off with [this](https://twitter.com/intigriti/status/1082979668972748803) link which is a link to a twitter thread. There is a picture attached to the  tweet which isn't available right now.
However, when it was available to download, after `binwalk`ing it we could find that there is a `Zip archive data` inside the file.
- Renaming the file to \<file\>.zip and unzipping, we find a pdf file named `nottheflag.pdg`, and there is a base64 string in it.
- Decoding the string we get a [url](https://go.intigriti.com/07b0fL24lkmva#) which is a download link for `data.zip`.
- It happens to be a password protected zip file.
- Referring to the second hint given in the contest, which is the link to the image uploaded on the twitter, doesn't help.
- Then comes the third hint which tells us to look for the cover.
- Apparently it refers to the banner of their twitter profile, which in fact carries the password.
- The file contains a shit ton of black and white jpgs, which clearly means binary.
- Apparently it does not xD we combine the images to find that they form a qr code.