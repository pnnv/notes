- Relatively small networks of close-by computers are called **Local Area Networks (LAN)**
	- The most famous and successful LAN technique is Ethernet
	  A series of computers are connected to a single Ethernet cable as the computer sends the data, it writes the data as an electrical signal onto the cable, because the network is shared, every computer plugged into the network sees the connection to solve this, each computer has a **Media Access Control Address (MAC Address)**.
- Every computer connected to a network gets an IP address.
#### OSI Model and Encapsulation

The OSI Model (Open Systems Interconnection Model) is a useful mental model of how internet communications system work and interact with each other.

The idea is that each level of the model is different part of what is necessary for data to be transferred from one place to another.

| OSI Referencce Model                | TCP/IP Conceptual Layers |
| ----------------------------------- | ------------------------ |
| Application, Presentation & Session | Application              |
| Transport                           | Transport                |
| Network                             | Network                  |
| Data Link & Physical                | Network Interface        |

But the competitor to the OSI model is the TCP/IP model, which is basically the same thing, but with less layers. It all shows the same thing, just with different levels of specificity.

#### Encapsulation
Encapsulation is the process of wrapping a piece of data in the routing information required to pass to the next level of the networking stack. Once it gets to the bottom of the stack at the physical layer and is actually sent across the network, once it is received "de-encapsulation" occurs, and each level of encapsulation is removed. Eventually, the data, as sent from the first computer reaches its destination.

### Networking Glossary

- **LAN:** LAN stands for "Local Area Network". It refers to a network that is not a publicly accessible to the greater internet. A home or office network is an example of LAN.
- **WAN:** WAN stands for "wide area network". It means a network that is much more extensive than LAN. While WAN is the relevant term to use to describe large, dispersed networks in general, It is usually meant to mean the internet, as a whole.
- **Protocol:** A protocol is a set of rules and standards that define a language that devices can use to communicate. There are a great number of protocols in use extensively in the networking, and they are often implemented in different layers.
  
  Some low level protocols are TCP, UDP, IP and ICMP. Some familiar examples of applications of application layer protocols, built on those lower protocols, are HTTP (for accessing web content), SSH, and TLS/SSL.

- **Port:** A port is an address on a single machine that can be tied to a specific piece of software. It is not a physical interface or location, but it allows your server to be able to communicate using more than one application.
- **Firewall**: A firewall is a program that decides whether traffic coming or going from a server should be allowed. A firewall usually works by creating rules for which type of traffic is acceptable on which ports. Generally, firewalls block ports that are not used by a specific application on a server.
- **NAT**: NAT stands for network address translation. It is a way to repackage and send incoming requests to a routing server to the relevant devices or  as a way to route requests through one IP address to the necessary backend servers.
- **VPN:** It is a means of connecting separate LANs through the internet, while maintaining privacy. This is used to connect remote systems as if they were on a local network, often for security reasons.
