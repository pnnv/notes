Packets have a header portion that contains information about the packet including the source and destination, timestamps, network hops, etc. The main portion of the packet contains the actual data being transferred. It is sometimes called the body or the payload.

**Protocol**: A protocol is a set of rules and standards that define a language that devices can use to communicate. There are great number of protocols in use extensively in networking, and they are often implemented in different layers.

Some low level protocols are TCP, UDP, IP, and ICMP. Some examples of application layer protocols, built on these protocols, are HTTP (for accessing web content), SSH, and TLS/SSL.

- **Port**: A port is an address on a single machine that can be tied to a single piece of software. It allows the server to be able to communicate using more than one application.
- **Firewall**: A firewall is a program that decides whether traffic coming or going from a server should be allowed. A firewall usually works by creating rules for which type of traffic is acceptable on which ports. Generally, firewalls block ports that are not used by a specific application on a server.
- **NAT**: NAT stands for network address translation. It is a way to repackage and send incoming requests to a routing server to the relevant devices or servers on LAN. This is usually implemented in physical LANs as a way to route requests through one IP address to the necessary backend servers.
- **VPN**: VPN stands for virtual private network. It is a means of connecting separate LANs through internet, while maintaining privacy. This is used to connect remote systems as if they were on a local network, often for security reasons.

#### Network Layers
While networking is discussed in a horizontal way, its implementation is layered in a vertical fashion within any given computer or network.

Which means that there are multiple technologies and protocols that are built on top of each other in order for communication to function. Each successive, higher layer abstracts the raw data a little bit more.

The language that we use to talk about each of the layering schemes varies significantly depending on which model we are using. Regardless of the model used in communication, the path of the data is the same.

As the data is sent out of one machine, it begins at the top of the stack and filters downwards. At the lowest level, actual transmission to another machine takes place. At this point, the data travels back up through the layers of the other computer.

#### TCP/IP Model

Commonly known as the internet protocol suite, is a widely adopted layering model. It defines the four separate layers:

- **Application**: In this model, the application layer is responsible for creating and transmitting user data between applications. The applications can be on remote systems, and should appear to operate as if locally to the end user. This communication is said to take place between **peers**.
- **Transport**: The transport layer is responsible for communication between processes. This level utilises ports.
- **Internet**: The internet layer is used to transport data from node to node in a network. This layer is aware of the endpoints of the connections, but is not concerned with the actual connection needed to get from one place to another. That's a job for IP addresses.
- **Link**: The link layer implements the actual topology of the local network that allows the internet layer to present an addressable interface. It establishes connections between nodes to send data.

#### Interfaces
Interfaces are networking communication points. Each interface is associated with a physical or virtual networking device.

Typically, your server will have one configurable network interface for each Ethernet or wireless card we have.

In addition, it will define a virtual network interface called the "loopback" or localhost interface. This is used as an interface to connect applications and processes on a single computer to other applications and processes. It is referred to as 'lo' interface in many tools.

Many times, administrators configure one interf