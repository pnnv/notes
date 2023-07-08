There are plenty of tools to download a file from the terminal, but curl is able to support most of the protocols and can be used to upload as well if need be.

Steps:
1. Begin capturing packets in Wireshark on the correct external interface
2. Run the command `$ curl http://httpforever.com/`
3. Run the command `$ wget http://httpforever.com/`
4. Stop the capture
