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
#### Network Layers
While networking is often discussed in terms of topology in a horizontal way, between hosts, its implementation is layered in a vertical fashion within any given computer or network.

What this means is that there are multiple technologies and protocols that are built on top of each other in order for communication to function. Each successive, higher layer abstracts the raw data a little bit more.

It also allows you to leverage lower layers in new ways without having to invest the time and energy to develop the protocols and applications that handle those types of traffic.

The language that we use to talk about each of the layering schemes varies significantly depending on which model you use. Regardless of the model used to discuss the layers, the path of data is the same.

As data is sent out of one machine, it begins at the top of the stack and filters downwards. At the lowest level, actual transmission to another machine takes place. At this point, the data travels back up through the layers of the other computer.

Each layer has the ability to add its own “wrapper” around the data that it receives from the adjacent layer, which will help the layers that come after decide what to do with the data when it is handed off.

#### TCP/IP Model
The TCP/IP model, more commonly known as the *internet protocol suite* is a widely adopted layering model. It defines the four separate layers:

- **Application**: This layer is responsible for creating and transmitting user data between applications. The applications can be on remote systems, and should appear to operate as if locally to the end user. This communication is said to take place between **peers**.
- **Transport**: The transport layer is responsible for communication between processes. This level of networking utilises ports to address different devices.
- **Internet**: The internet layer is used to transmit data node to node in a network. This layer is aware of the endpoints of the connections, but is not concerned with the actual connection needed to get from one place to another. **IP** **addresses** are defined in this layer as a way of reaching remote systems in an addressable manner.
- **Link**: The link layer implements the actual topology of the local network that allows the internet layer to present an addressable interface. It establishes connections between neighbouring nodes to send data.

#### Interfaces
Interfaces are networking communication points for your computer. Each interface is associated with a physical or virtual networking device.

Typically, your server will have one configurable network interface for each Ethernet or wireless internet card you have.

In addition, it will define a virtual network interface called the “loopback” or localhost interface. This is used as an interface to connect applications and processes on a single computer to other applications and processes. You can see this referenced as the “lo” interface in many tools.

Many times, administrators configure one interface to service traffic to the internet and another interface for a LAN or private network.

In datacenters with private networking enabled, your VPS will have two networking interfaces. The "*eth0*" interface will be configured to handle traffic from the internet, while the "*eth1*" interface will operate to communicate with a private network.

#### Protocols
Networking works by piggybacking a number of different protocols on top of each other. In this way, one piece of data can be transmitted using multiple protocols encapsulated within one another.

#### Medium Access Control
Medium access control is a communications protocol that is used to distinguish specific devices. Each device is supposed to get a unique, hardcoded **media access control address** (MAC Address) when it is manufactured that differentiates it from every other device on the internet.

Addressing hardware by the MAC address allows you to reference a device by a unique value even when the software on top may change the name for that specific device during operation.

MAC addressing is one of the only protocols from the low-level link layer that you are likely to interact with on a regular basis.

#### IP
The IP protocol is one of the fundamental protocols that allow the internet to work. IP addresses are unique on each network and they allow machines to address each other across a network. It is implemented on the internet layer in the TCP/IP model.

Networks can be linked together, but traffic must be routed when crossing network boundaries. This protocol assumes an unreliable network and multiple paths to the same destination that it can dynamically change between.

There are a number of different implementations of the protocol. The most common implementation today is IPv4 addresses, which follow the pattern `123.123.123.123`, although IPv6 addresses, which follows the pattern `2001:0db8:0000:0000:0000:ff00:0042:8329`, are growing in popularity due to the limited number of available IPv4 addresses.

#### ICMP
ICMP stands for **internet control message protocol**. It is used to send messages between devices to indicate their availability or error conditions. These packets are used in a variety of network diagnostic tools, such as `ping`  and `traceroute`.

Ususlly ICMP packets are transmitted when a different kind of packet encounters a problem. They are used as a feedback mechanism for network communications.

#### TCP
(transmission control protocol).
It is implemented in the transport layer of the TCP/IP model and is used to establish reliable connections.

TCP is one of the protocols that encapsulates data into packets. It then transfers these to the remote end of the connection using the methods available on the lower layers. On the other end, it can check for errors, request certain pieces to be resent, and reassemble the information into one logical piece to send to the application layer.

The protocol builds up a connection prior to data transfer using a system called a three-way handshake. This is a way for the two ends of the communication to acknowledge the request and agree upon a method of ensuring data reliability.

After the data has been sent, the connection is torn down using a similar four-way handshake.

TCP is the protocol of choice for many of the most popular uses for the internet, including WWW, SSH, and email.

#### UDP
(user datagram protocol)
It is a popular companion protocol to TCP and is also implemented in the transport layer.

The fundamental difference between UDP and TCP is that UDP offers an unreliable data transfer. It does not verify that data has been received on the other end of the connection. This might sound like a bad thing, and for many purposes it is. However, it is also extremely important for some functions.

Because it is not required to wait for the confirmation that the data was received and forced to resend the data, UDP is much faster than TCP. It does not establish a connection with the remote host, it just sends data without confirmation.

Because it is a straightforward transaction, it is useful for communications like querying for network resources. It also doesn't maintain a state, which makes it great for transmitting data from one machine to many real-time clients. This makes it ideal for VIOP, games, and other applications that cannot afford delays.

#### HTTP
HTTP stands for hypertext transfer protocol. It is a protocol defined in the application layer that forms the basis for the communication on the web.

HTTP defines a 