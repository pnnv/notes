[source](https://github.com/blinils/CTF/blob/master/CTF-Jeopardy/2016-icectf/challenges/corrupt-transmission-50/README.md)
We are given a link to a file which is supposed to be an image and which name is "`corrupted.png`".

First we'll see what kind of stegano we have to deal with here.

```bash
pranav@eos ~/sandbox> file corrupted.png
corrupted.png: data
pranav@eos ~/sandbox> head -n2 corrupted.png
PNG
IHDbKGD	pHYs

            tIMet IDATxTَlYz[bLU]]ͦMaZu'1+Ed?a2
                                              TH`k3ďaOk$ر?lU)sD)QQ_Hr1Ҡ\#fgh-%Y9GkRH( 
                                  R(0B$H
                                        )!DJI)R
```
Assuming this is a real PNG file --- *Due to the presence of keywords such as **IHDR, IDAT or tIME*** --- something went wrong.

While `pngcheck` verifies the integrity of `png` files, `exiftool` checks the meta information.
But once more, no further information is given, except that it is CORRUPTED ERRORS DETECTED FILE FORMAT ERROR FBI GET ON THE GROUND!

```bash
pranav@eos ~/D/Image-ExifTool-12.62> ./exiftool ~/sandbox/corrupted.png    
ExifTool Version Number         : 12.62
File Name                       : corrupted.png
Directory                       : /home/pranav/sandbox
File Size                       : 469 kB
File Modification Date/Time     : 2023:06:02 16:29:31+05:30
File Access Date/Time           : 2023:06:02 16:29:31+05:30
File Inode Change Date/Time     : 2023:06:02 16:30:07+05:30
File Permissions                : -rw-r--r--
Error                           : File format error
```

The file command does not recognize the file as a picture, maybe because the *PNG signature verification* has been distorted.

```
The first eight bits of a PNG file always contain the following values:

   (decimal)              137  80  78  71  13  10  26  10
   
   (hexadecimal)           89  50  4e  47  0d  0a  1a  0a
   
   (ASCII C notation)    \211   P   N   G  \r  \n \032 \n
```

To check the hex we can use `xxd` [^1] command.

```bash
pranav@eos ~/sandbox [127]> xxd corrupted.png | head
00000000: 9050 4e47 0e1a 0a1b 0000 000d 4948 4452  .PNG........IHDR
00000010: 0000 01f4 0000 0198 0806 0000 00b4 e010  ................
00000020: ab00 0000 0662 4b47 4400 ff00 ff00 ffa0  .....bKGD.......
00000030: bda7 9300 0000 0970 4859 7300 000b 1300  .......pHYs.....
00000040: 000b 1301 009a 9c18 0000 0007 7449 4d45  ............tIME
00000050: 07e0 0614 0314 08a8 9865 7400 0020 0049  .........et.. .I
00000060: 4441 5478 da54 bcd9 8e6c 597a dff7 5bf3  DATx.T...lYz..[.
00000070: 1e62 cae9 4c55 5d5d d5cd a69a 144d 19be  .b..LU]].....M..
00000080: 9061 5a80 75c5 2731 a02b dffb 4564 3f85  .aZ.u.'1.+..Ed?.
00000090: 2108 b061 0332 0cd8 204c 0854 d312 4891  !..a.2.. L.T..H.
```

That's it, the first eight bytes of the file do not meet the PNG specifications, hence the file is corrupted.

We can fix that using a hex editor.
After doing so, the file now looks like:
```bash
$ xxd corrupted.png > hexDumped
$ nvim hexDumped
# now we make our edits
$ xxd -r hexDumped > repaired.png
```

We can not open `repaired.png`


[^1]: More about `xxd` can be found in [[Hex]].