```bash
$ echo "Hello!" > file4
$ xxd file4
```
xxd is able to convert a file into its hexadecimal representation.

- File formats (and networking protocols and other stuff on the internet) are defined in documents known as RFCs. All files follow the rule for their file format.

#### Hex-editing

xxd is not a hex editor, it just displays hex. However, we can use it to convert files into hex, make edits to them, then convert the files back to their correct formats.

```bash
$ xxd copyOfPng.png > hexDumped
```

Now we open the hexDumped in a text editor, we make an edit to the file and change the first four characters (the magic numbers) to be 0000.

After saving we rebuild the file using the following command:

```bash
$ xxd -r hexDumped > modified.png
```

modified.png does not open because we mangled[^1] the file header!


One useful tool to find the difference between files is to use [[diff]].

To fix the mangled file header, we can use a hex-editor. Hex-editors do a similar thing to xxd, but also give us ability to edit in a nice GUI.

One of the GUI hex editors in `bliss`.



[^1]: that's the technical term for corrupted