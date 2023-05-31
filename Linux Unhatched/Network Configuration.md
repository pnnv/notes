The `ipconfig` command stands for *"interface configuration"* ans is used to display network configuration information.

```
ifconfig [OPTIONS]
```

> The `iwconfig` command is similar to `ifconfig` command, but it is dedicated to wireless network interfaces.

IPv4 address of the primary network device `eth0` is `192.168.1.2` and that device is currently active (UP).

```bash 
**root@localhost:~#** ifconfig                                     
`eth0`      Link encap:Ethernet  HWaddr 02:42:c0:a8:01:02                         
          `inet addr:192.168.1.2`  Bcast:192.168.1.255  Mask:255.255.255.0        
          `UP` BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                    
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0                   
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0                 
          collisions:0 txqueuelen:1000                                          
          RX bytes:4346 (4.3 KB)  TX bytes:5602 (5.6 KB)                        
                                                                                
lo        Link encap:Local Loopback                                             
          inet addr:127.0.0.1  Mask:255.0.0.0                                   
          UP LOOPBACK RUNNING  MTU:65536  Metric:1                              
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0                    
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0                  
          collisions:0 txqueuelen:1000                                          
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
```


The `lo` network device is referred to as the *loopback* device. It is a special network device used by the system when sending network-based data to itself.

- The `ifconfig` command can also be used to temporarily modify the network settings.[^1]
- The `ping` command is used to verify connection between two computers. It does this by sending packets to another machine on a network. If the sender receives a response it should be possible to connect to that machine.
- Information sent using 'packets' is encapsulated unit of data sent over network. In order for the packets to find other computer, they will need an address. The `ping` command uses IP addresses to identify a computer on the network that it wants to connect to.
- By default, the `ping` command will continue sending packets until the break command is entered at the console. To limit how many pings are sent, use the `-c` option followed by the number of pings to be sent.
- If the `ping` command fails, you  will receive a message stating `Destination host unreachable`.
- The `ping` command may fail even though the remote machine is connecting. This is because some administrators configure their machines, or even entire networks, not to respond to `ping` requests as a security measure. The `ping` command also works with a hostname, or domain name like yahoo.com. Using this first saves time, if that `ping` command is successful, there is proper name resolution AND the IP address is functioning properly as well.



[^1]: Typically these changes should be permanent, so using the `ifconfig` command to make such changes is fairly rare.