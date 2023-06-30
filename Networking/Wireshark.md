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
We can use `file` menu or drag and drop the file or double-click on the file to load a pcap.

Now we can see the processed file name, detailed number of packets and packet details. Packet details are shown in three different panes, which allow us to discover them in different formats:

- **Packet List Pane**: Summary of each packet (source and destination address, protocol, and packet info). You can click on the list to choose a packet for further investigation. Once you select a packet, the details will appear in the other panels.
- **Packet Details Pane**: Detailed protocol breakdown of the selected packet.
- **Packet Bytes Pane**: Hex and decoded ASCII representation of the selected packet field depending on the clicked section in the details pane.

##### Colouring Packets
- Along with quick packet information, Wireshark also colour packets in order of different conditions and the protocol to spot anomalies and protocols in captures quickly. 
- At a glance packet information can help track down exactly what we are looking for during analysis. We can even create custom colour tools to spot events of interest by using display filters.

Wireshark also has two types of colouring methods:
- temporary rules which are only available during the analysis of that certain program session.
- permanent rules that are saved under the preference file (profile) and available for the next program session.

##### Traffic Sniffing
We can use the blue "shark button" to start network sniffing (capturing traffic), the red button will stop sniffing, and green button will restart the sniffing process. The status bar will also provide the used sniffing interface and the number of collected packets.

##### Merge PCAP files
Wireshark can combine two PCAP files into one single file. We can either use the "File -> Merge" menu path to merge a pcap with the processed one. Note that we need to save the merged the file before working with it.
