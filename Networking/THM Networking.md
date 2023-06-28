> **Note**: This is highly summarised version of the original article.

The internet is a giant network that consists of many, many small networks within itself. 

- The first Iteration of the internet was within the ARPANET project in the late 1960s. This project was funded by the United States Defence department and the first documented action. The internet as we know was invented by Tim Berners-Lee by the creation of the World Wide Web (WWW).

- An **IP Address** is a set of numbers that are divided into four octets. The value of each octet will summarise to be the IP address of the device on the network. This number is calculated through a technique known as IP addressing and subnetting.
- IP addresses follow a set of standards known as protocols. These protocols are the backbone of networking.

- **MAC Addresses**: Device on a network all have a physical interface, which is a microchip board found on the device's motherboard. This network interface as assigned a unique address at the factory it was built at, called MAC (Media Access Control) address. The MAC address is a twelve-character hexadecimal number split into two's and separated by a colon.
	- Interestingly these can be faked in a process known as **spoofing**. This spoofing occurs when a networked device pretends to identify as another using its MAC address. When it occurs, it can often break poorly implemented security designs that assume that devices talking on a network are trustworthy.

#### Ping (ICMP)
- Ping is one of the most fundamental tools. It uses **Internet Control Usage Protocol** (ICMP) packets to determine the performance of a connection between devices, for example, if the connection exists or is reliable.
- The time taken for ICMP packets travelling between devices is measured  by using ping. 

```bash
PING google.com (216.58.200.206) 56(84) bytes of data.
64 bytes from del11s07-in-f14.1e100.net (216.58.200.206): icmp_seq=1 ttl=117 time=60.8 ms
64 bytes from del11s07-in-f14.1e100.net (216.58.200.206): icmp_seq=2 ttl=117 time=61.1 ms
64 bytes from nrt12s12-in-f206.1e100.net (216.58.200.206): icmp_seq=3 ttl=117 time=60.8 ms
64 bytes from del11s07-in-f14.1e100.net (216.58.200.206): icmp_seq=4 ttl=117 time=60.7 ms
64 bytes from nrt12s12-in-f206.1e100.net (216.58.200.206): icmp_seq=5 ttl=117 time=60.7 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 60.678/60.823/61.070/0.135 ms
```
This is the output of the command `$ ping -c 5 google.com` (i.e. ping google.com 5 times).

- Here are we are pinging the device which has the private address of `216.58.200.206`. Ping informs us that we have sent five ICMP packets, all of which were received with the average time of 4 seconds.