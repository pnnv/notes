#### tshark
[basics](https://hackertarget.com/tshark-tutorial-and-filter-examples/)
Even better than viewing packets in a GUI is playing with them in a scripting language. (tbh wireshark is good for 99% of all use cases that don't involve insanely large pcaps).

tshark is a command line tool to do the same thing as [[Wireshark]] does, but all in Python. It allows us to script complex activities which we would never be able to do in wireshark.

#### Basic Commands
Since we can't always have Wireshark or tshark around, but we'll always have a need to capture packets. That's where tcpdump comes in. 

The following command lists the interfaces available to work with:
```bash
$ tcpdump -D
1.enp6s0 [Up, Running, Connected]
2.any (Pseudo-device that captures on all interfaces) [Up, Running]
3.lo [Up, Running, Loopback]
4.wlan0 [Up, Wireless, Not associated]
5.bluetooth0 (Bluetooth adapter number 0) [Wireless, Association status unknown]
6.bluetooth-monitor (Bluetooth Linux Monitor) [Wireless]
7.nflog (Linux netfilter log (NFLOG) interface) [none]
8.nfqueue (Linux netfilter queue (NFQUEUE) interface) [none]
9.dbus-system (D-Bus system bus) [none]
10.dbus-session (D-Bus session bus) [none]
```

These are meant to be human readable names for various networking devices on the system.
