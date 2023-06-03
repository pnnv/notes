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
