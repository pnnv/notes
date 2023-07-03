##### Capture Packets (Without Wireshark)
We won't always have wireshark around but we'll always have a need to capture packets. That's where `tcpdump` comes in (A little about it is given in [[Scripting and Tshark]].


To capture packets using `tcpdump` use:
```bash
$ tcpdump -i enp6s0 -w packets.pcap
tcpdump: listening on enp6s0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
```

