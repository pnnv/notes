##### Local Area Network (LAN) Topologies
By the term "topology", we are actually referring to  the design or look of the network at hand.

#### Star Topology
- The main premise is that devices are individually connected via central networking device such as a switch or a hub. This topology is the most commonly found today because of its reliability and scalability- despite the cost.
- Any information sent to the device using this topology is sent via the central device to which it connects.
- Because more cabling and the purchase of dedicated networking equipment is required for this topology, it is more expensive than any of the other topologies. However, despite the added cost, this does provide some significant advantages:
	- It is much more scalable in nature, which means that it is much easier to add more devices as the demand for the network increases.
	- As the network scales more maintenance is required to keep the network functional, which also makes troubleshooting much harder.
	- It is still prone to failure - albeit reduced. i.e. if the central device fails, these devices will no longer be able to send and receive data.

#### Bus Topology
- This type of connection relies upon single connection which is known as the backbone cable.
- Because all the data destined for each device travels along the same cable, it is very prone to becoming slow and bottlenecked if the devices within the topology are simultaneously requesting data. This bottleneck also results in very difficult troubleshooting because it quickly becomes difficult to identify which device is experiencing issues.
- Bus topoligies are one of the easier and more cost-efficient topologies to set up because of their expenses, such as cabling or dedicated networking equipment used to connect these devices.
- Lastly, another disadvantage of the bus topology is that there is little redundancy in place of these failures .This disadvantage is because there is single point of failure along the backbone cable. If this cable were to break, devices can no longer receive or transmit data along the bus.

#### Ring Topology
- Aka token topology. Devices such as computers are connected to each other to form a loop, meaning that there is little cabling required and less dependence on the dedicated hardware such as within star topology.
- It works by sending the data around the ring until it reaches the destination.
- These are less prone to bottlenecks, such as within topology, as large amounts of traffic are not travelling across the network at any one time. The design of this topology does, however, mean that a fault such as a cut cable, or broken device will result in the entire network breaking.

#### Switches
- These are dedicated devices within the network that are designed to aggregate multiple other devices such as computers, printers, or any other networking-capable devices using the Ethernet. These multiple devices plug into a switch's port.
- There are generally found in places which have larger networks.
- Switches are more efficient than their lesser counterpart (hubs/repeaters). Switches keep track of what device is connected to which port. This way, when they receive a packet, instead of repeating that packet to every port like hub would do, it just sends it to the intended target, thus reducing network traffic.
- Both switches and routers can be connected to one another. The ability to do this increases the reliability of the network by adding multiple paths for data to take. If one path goes down, another can be used. Whilst this may reduce the overall performance of a network because packets have to take longer to travel, there is no downtime -- a small price to pay considering the alternative.

#### Routers
- It's a router's job to connect the networks and pass data between them. It does this by using routing (hence the name router).
- Routing is the label given to the process of data travelling across the networks. Routing involves creating a path between networks so that this data can be successfully delivered.
- Routing is useful when devices are connected by many paths.

#### Subnetting
Subnetting is the term given to splitting up a network into smaller, minature networks withing itself.
- Networks need to know the address to send the data to hte correct location. Network administrators use subnetting to categorise and assign specific parts of a network to reflect this.
- It is achieved by splitting up the number of hosts that can fit within the network, represented by a number called a subnet mask. 

Subnets use IP addresses in 3 different ways:
- Identify the network address
- identify the host address
- identify the default gateway

-  Network address:
	- This address identifies the start of the actual network and is used to identify a network's existence. 
	  
	  For example, a device with the IP address of 192.168.1.100 will be on the network identified by 192.168.1.0
- Host address:
	- An IP address here is used to identify a device on the subnet.
	  For example, a device will have the network address of 192.168.1.1
- Default gateway:
	- The default gateway address is a special address assigned to a device on the network that is capable of sending information to another network.
	- Any data that needs to go to a device that isn't on the same network (i.e. isn't on 192.168.1.0) will be sent to this device. These devices can use any host address but usually use either the first or last host address in a network (.1 or .254)
