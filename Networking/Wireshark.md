### Wireshark
It is an open-source, cross-platform packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP).

It is commonly used as one of the most best packet analysis tools. 

#### Use Cases
- Detecting and troubleshooting network problems, such as network load failure points and congestion.
- Detecting security anomalies, such as rogue hosts, abnormal port usage, and suspicious traffic.
- Investigating and learning protocol details, such as response codes and  payload data.

> Note that wireshark is not an Intrusion Detection System (IDS). It only allows analysts to discover and investigate the packets in depth. It also doesn't modify the packets; it reads them. Hence, detecting any anomaly or network problem with the networks highly depends on the knowledge and skill of the analyst.
> 

#### GUI and Data
Wireshark GUI runs with a single all-in-one page, which helps users investigate the traffic in multiple ways. At first glance, five sections stand out:

- **Toolbar**: The main toolbar contains multiple menus and shortcuts for packet sniffing and processing, including filtering, sorting, summarising, exporting and merging.
- **Display Filter Bar**: The main query and filtering section.
- **Recent Files**: List of the recently investigated files. Listed files can be recalled with a double click.
- **Capture Filter and Interfaces**: Capture filters and available sniffing points (network interfaces). The network interface is the connection point between a computer and a network. The software connection (e.g. lo, eth0 and ens33) enables networking hardware.
- **Status Bar**: Tool status, profile and numeric packet information.

##### Loading PCAP files
