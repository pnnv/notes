#### IP Address and basic Networking
It is just a way through which other computers know who you are, and based off of a complicated routing system. 

To find out IP Address we can run `ip addr`. This will print out a list of things called interface and some other stuff. IP addresses of the form `127.0.0.1` are known as **IPV4** addresses. (There's another format known as IPV6).

`127.0.0.1` is called our local host, aka, out computer's local IP address.

#### Routing
```bash
$ traceroute google.com
```

This shows a printout of all the hosts we are hopping across, starting with our gateway router and ending with google.com server. This family of commands is useful for troubleshooting networking problems.

Our local IP address is completely different from our public IP this is because of something called **NAT** or Network Address Translation which is a method of mapping one IP address to another by modifying packets while they are in transit.
- In simple terms, our local IP is stored by some NAT server which ensures that any responses to traffic from us that leave our network, come back to out locally assigned IP. On the other hand, nobody should be able to connect into a box behind NAT because they will not know the local IP address and either way, a local address shouldn't be routed across the internet.
- Basically, NAT allows connections out and responses back, but does not allow connections in.

#### VM Networking
Virtualisation software gives an option to switch your VM between a NAT'd IP address and a Bridged IP address.

- Bridged IP addresses are IP addresses assigned by your local router, which will be NAT'd by the router when you try to connect out. NAT'd IP addresses are IP addresses assigned by out virtualisation software, which puts that box behind a NAT.
- This means that if we are NAT'd, other computers can't connect to us directly, but if we are bridged, our IP address will be routable.



