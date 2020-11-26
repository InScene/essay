# OSI Model

 - [OSI Layers](#layers)

## <a name="layers"></a> OSI Layers
Inspired by:
 - [wikipedia-en](https://en.wikipedia.org/wiki/OSI_model)
 - [wikipedia-de](https://de.wikipedia.org/wiki/OSI-Modell)

The recommendation X.200 describes seven layers, labelled 1 to 7. Layer 1 is the lowest layer in this model.

|   Layer  |    Protocol Data Unit (PDU)  | Description | Example |
|:-------------:|:------:|:----------:|:----------:|
| 7. Application | Data | 	High-level APIs, including resource sharing, remote file access. | Webbrowser, Instant Messaging |
| 6. Presentation | Data | Translation of data between a networking service and an application; including character encoding, data compression and encryption/decryption. | ISO 8822 / X.216 (Presentation Service) |
| 5. Session | Data | Managing communication sessions, i.e., continuous exchange of information in the form of multiple back-and-forth transmissions between two nodes. | ISO 8326 / X.215 (Session Service) |
| 4. Transport | TCP (Segment), UDP (Datagram) | Reliable transmission of data segments between points on a network, including segmentation, acknowledgement and multiplexing. | TCP, UDP, SCTP, DCCP |
| 3. Network | Packet | Structuring and managing a multi-node network, including addressing, routing and traffic control. | IP, IPsec, ICMP |
| 2. Data link  | Frame | Reliable transmission of data frames between two nodes connected by a physical layer. | IEEE 802.11 (WLAN), IEEE 802.4 (Token Bus), IEEE 802.5 (Token Ring), FDDI |
| 1. Physical | Bit, Symbol | Transmission and reception of raw bit streams over a physical medium. | RS 232, RS 422, RS 423, RS 499 |
