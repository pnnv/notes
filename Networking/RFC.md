### RFC
In theory, RFCs are the ground truth, All protocols are requires to exactly follow the specification.

RFCs or Request for Comments, is the way that the internet develops standards.

RFC documents has been used by the internet community for the last 40 years as a way to define new standards and share technical information. Researchers from universities and corporations publish these documents to offer best practices and solicit feedback on internet technologies. RFCs are managed by a worldwide organisation called **Internet Engineering Task Force**.

##### How to read RFCs and similar docs
[stackoverflow answer](https://softwareengineering.stackexchange.com/questions/179022/how-does-one-read-rfcs-and-similar-documents)

These are meant to be treated as one would treat any other standard reference.
They are much more useful as reference than as explanatory text.

##### TCP-IP Bible

The [TCP-IP Guide by NoStarch Press](https://nostarch.com/tcpip.htm) is recommended for any queries about protocols for beginners.

- The best thing about RFCs is that they will have the information that would never be found on Wikipedia or a normal reference.

```
1. what is the TC bit?
- TC TrunCation specifies that this message was truncated due to length greater than that permitted on the transimission protocol.
- It is a Bool.

The header contains the following fields:

                                    1  1  1  1  1  1
      0  1  2  3  4  5  6  7  8  9  0  1  2  3  4  5
    +--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+
    |                      ID                       |
    +--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+
    |QR|   Opcode  |AA|TC|RD|RA|   Z    |   RCODE   |
    +--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+
    |                    QDCOUNT                    |
    +--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+
    |                    ANCOUNT                    |
    +--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+
    |                    NSCOUNT                    |
    +--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+
    |                    ARCOUNT                    |
    +--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+--+
```


#### [rfc1149.txt](https://www.rfc-editor.org/rfc/rfc1149.txt)

This is a short RFC about "A Standard for the Transmission of IP Datagrams on Avian Carriers".