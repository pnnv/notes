`diff` takes two pieces of text and compares them, looking for differences. With text files usage is as simple as:
```bash
$ diff file1.txt file2.txt
```
and the results will display.

It is slightly more complicated with binary files or other dense formats like images. To see what the difference between the original image and the new mangled file we played with in [[Hex]]:

```bash
$ diff -y <(xxd copyOfPng.png) <(xxd modified.png)  
```

This will display the differences between the two files.

There are GUI versions of diff and also some online ones, one of which is [diffchecker]( https://www.diffchecker.com/).

