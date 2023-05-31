Base64 is another encoding scheme that uses 64 characters to represent data in ASCII text format. It is commonly used to encode binaries that would not be able to be sent via methods that only use ASCII, such as in HTML, in URLs, or in some email formats.

Base64 uses '=' at the end of a string of letters and numbers which is a visual distinction which can be used to identify base64.

To manipulate base64 in terminal, we use the command `base64`.

https://gchq.github.io/CyberChef/
This is a useful tool released by GCHQ. It is a great tool for converting encoding/encryption.

```bash
$ echo "Hello World" | base64 
$ echo "Hello World" > 64dText
$ base64 --decode 64dText 
$ base64 --decode SGVsbG8gV29ybGQ=
```