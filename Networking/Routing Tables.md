#### Routers
- A router is a networking device that forwards data packets between computer network. This device is usually connected to two or more different networks. When a data packet comes to a router port, the router reads the address information in the packet to determine out which port the packet will be sent.
  E.g. A  router provides you internet access by connecting your LAN with the internet.

- When a packet arrives at a Router, it examines destination IP address of a received packet and make routing decisions accordingly. Routers use **Routing Tables** to determine out which determines which interface the packet will be sent to. A routing table lists all networks for which routes are known. Each router's routing table is unique and stored in the RAM of the device.

#### Routing Table
A routing table is a set of rules, often viewed in table format, that is used to determine where data packets travelling over an Internet Protocol (IP) network will be directed. All IP-enabled devices, including routers and switches, use  routing tables.

```
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         172.16.132.1    0.0.0.0         UG        0 0          0 enp6s0
172.16.132.0    0.0.0.0         255.255.255.0   U         0 0          0 enp6s0
```

- The entry corresponding to the *default* gateway configuration is a network destination of `0.0.0.0` with a network mask (netmask) of  `0.0.0.0` . The Subent Mask of default route is always  `0.0.0.0`.

Each entry of the routing table consists of the following entries:

1. **Network ID**: The network ID or destination corresponding to the route.
2. **Subnet Mask**: The mask that is used to match a destination IP address to the network ID.
3. **Next Hop**: The IP address to which the packet is forwarded.
4. **Outgoing Interface**: Outgoing Interface the packet should go out to reach the destination network
5. **Metric**: A common use of the metric is to indicate the *minimum number of hops* (routers crossed) to the network ID.

Routing table entries can be used to store the following types of routes:

- Directly Attached Network IDs
- Remote Network IDs
- Host Routes
- Default Route
- Destination

- These routing tables can be maintained manually or dynamically. In dynamic routing, devices build and maintain their routing tables automatically by using routing protocols to exchange information about the surrounding network topology. Dynamic Routing tables allow devices to "listen" to the network and respond to occurrences like device failures and network congestion. Tables for static network devices do not change unless a network administrator manually changes them.
