##### Capture Packets (Without Wireshark)
We won't always have wireshark around but we'll always have a need to capture packets. That's where `tcpdump` comes in (A little about it is given in [[Scripting and Tshark]].


To capture packets using `tcpdump` use:
```bash
$ tcpdump -i enp6s0 -w packets.pcap
tcpdump: listening on enp6s0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
```

`ipconfig` has now been replaced by `ip`.
`$ ip addr` can be used to get the IP address of each interface.

```bash
$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp6s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 04:7c:16:2f:af:c8 brd ff:ff:ff:ff:ff:ff
    inet 172.16.132.89/24 brd 172.16.132.255 scope global dynamic noprefixroute enp6s0
       valid_lft 2805sec preferred_lft 2805sec
    inet6 fe80::1a66:67ff:faf1:c052/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 16:59:05:c2:8c:70 brd ff:ff:ff:ff:ff:ff permaddr 84:7b:57:0d:58:27
```

- Here we see that for `lo`, loopback, out ip address is `127.0.0.1...` which is also ours, and every other computer on the planet, because packets never leave our device therefore its fine for everyone to have same loopback address.
- `enp6s0` is my local Ethernet adapter.
- `wlan0` is the wireless interface, it has an `ipv4` address, ab=n Ethernet link address and a bunch of `ipv6` addresses.

`$ ip neigh` returns the ARP cache:
```bash
$ ip neigh
172.16.132.1 dev enp6s0 lladdr 00:00:cd:2c:0c:b7 REACHABLE 
fe80::1 dev enp6s0 lladdr c8:3a:35:14:69:90 router STALE
```
Many things can be done with these.

`$ ip route` prints out the routing tables
```bash
$ ip route
default via 172.16.132.1 dev enp6s0 proto dhcp src 172.16.132.89 metric 100 
172.16.132.0/24 dev enp6s0 proto kernel scope link src 172.16.132.89 metric 100 
```

We can also use `ip` command to change values, whether that's out
```bash
## Disable the NIC so you can modify it
$ ip link set dev $NIC down
## set new MAC address ##
$ ip link set dev $NIC address DE:AD:BE:EF:BA:BE
## Re-enable the NIC
$ ip link set dev $NIC up
```
