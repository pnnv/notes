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


#### Packet Dissection
You can click on a packet in the packet list pane to open  its details (double click will open the details in the new window). Packets consist of 5 to 7 layers based on the OSI model. 

- Each time we click a detail, it will highlight the corresponding part of the packet in the bytes pane.
Looking at this pane, we can see seven  distinct layers to the packet: frame/packet, source \[MAC\], source \[IP\], protocol, protocol errors, application protocol, and application data. 

- **The frame (Layer 1)**: This will show you what frame/packet you are looking at and details  specific to the physical layer of the OSI model.
- **Source [MAC] (layer 2)**: This will show you the source and destination MAC address; from Data Link layer of the OSI model.
- **Source [IP] (Layer 3)**: This will show us the source and destination of the IPv4 addresses; from the network layer and the OSI model.
- **Protocol (Layer 4)**: This will show us the details of protocol used (TCP/UDP) and source & destination ports; from the Transport layer of the OSI model.
- **Protocol Errors**: This continuation of the 4th layer shows specific segments from the TCP that needs to be reassembled
- **Application Protocol (Layer 5)**: This will show us the details specific to the protocol used, such as `HTTP` ,`FTP`, and `SMB`. From the application layer of the OSI model.
- **Application Data**: This extension of the 5th layer can show application-specific data.

---

- **Packet Numbers**: Wireshark calculates the number of investigated packets and assigns a unique number for each packet. This helps the analysis process for big captures and makes it easy to go back to a specific point of an event.
- **Go to Packet**: Packet numbers do not only help to count the total number of packets or make it easier to find/investigate specific packets. This feature not only navigates between packets up and down; it also provides in-frame packet tracking and finds the next packet in the particular part of the conversation. You can use the "Go" menu in the toolbar to view specific packets.
- **Find the Packets**: Apart from the packet number, wireshark can also find the packets by content. We can use the "Edit -> Find Packet" menu to make search inside the packets for a particular event of interest.
  There are two crucial points in finding packets:
  - The first is knowing the input type. This functionally accepts four types of inputs (Display Filter, Hex, String and Regex). Searches are case insensitive, but we have an option to change that.
  - The second point is choosing the search field. We can conduct searches in three panes (packet list, packet details, and packet bytes), and it is important to know the available information in each pane to find the  event of interest.
- **Mark Packets**: Marking packets is yet another helpful functionality. We can find/point specific packet for further investigation by marking it. It helps analysts point to an event of interest or export particular packets from the capture.
- Marked packets will be shown in the black regardless of the original colour representing the connection type. Note that marked packet information is renewed every file session, so marked packets will be lost after closing the capture file.
- **Packet Comments**: Similar to packet marking, commenting is another helpful feature for analysts. We can add comments for particular packets that will help the further investigation or remind and point out important/suspicious points for other layer analysts. Unlike packet marking, the comments can stay within the capture file until the operator removes them.
- **Export Packets**: Capture files can contain thousands of packets in a single file.