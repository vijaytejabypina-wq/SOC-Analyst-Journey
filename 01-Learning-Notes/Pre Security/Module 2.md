# Module 2 – Network Fundamentals
 
## What is Networking?
 
At its core, networking is just about getting devices to talk to each other. The internet is the biggest example of this- it's essentially a massive web of smaller networks all connected together.
 
It started back in the late 1960s with a US Defence project called ARPANET, which was the first real working network. But the internet as most people know it- where you browse, share files, and send emails- only really took shape in 1989 when Tim Berners-Lee invented the World Wide Web.
 

 
## How Devices Are Identified on a Network
 
For devices to communicate, they need some form of identity. There are two main identifiers:
 
IP Address- This is a logical address assigned to a device on a network. It can change over time or be reassigned to a different device. Think of it like a mailing address.  
Example: `192.168.1.1`
 
MAC Address- This is a physical identifier burned into a device's network card at the factory. Unlike an IP, it doesn't change. Think of it like a serial number on a product.  
Example: `a4:c3:b1:p2:o0:s9`
 
Ping uses ICMP packets to test whether two devices can reach each other and how well the connection is performing.

 
## LAN and Network Topologies
 
A LAN (Local Area Network) connects devices within a limited physical space- like a home, office, or school.
 
Networks can be laid out in different ways (called topologies):
 
 Star Topology- Every device connects individually to a central switch or hub. Most common today because it's reliable and easy to scale, though it costs more.
 Bus Topology- All devices share a single backbone cable. Simple but a single fault can bring everything down.
 Ring Topology- Devices connect in a loop, each to the next. Uses less cabling but a break anywhere affects the whole network.
Switches connect multiple devices within the same network.  
Routers connect different networks together and direct traffic between them.
 
Subnetting is the practice of dividing a larger network into smaller sub-networks- useful for organization and security.
 

 
## ARP (Address Resolution Protocol)
 
Every device on a network needs to know how to reach others. ARP bridges the gap between IP addresses (logical) and MAC addresses (physical).
 
When a device wants to communicate with another IP on the same network, it broadcasts an ARP Request asking "who owns this IP?" The device with that IP responds with an ARP Reply containing its MAC address. This mapping is then cached locally to avoid asking again.
 

 
## DHCP (Dynamic Host Configuration Protocol)
 
IP addresses can be assigned manually, but in most networks a DHCP server handles this automatically. The process goes like this:
 
1. Device connects and sends a DHCP Discover broadcast
2. DHCP server responds with a DHCP Offer (here's an available IP)
3. Device sends a DHCP Request (I'll take it)
4. Server sends a DHCP ACK confirming the lease

 
## The OSI Model
 
The OSI model is a 7-layer framework that standardizes how data moves across a network. It ensures that devices from different manufacturers can still communicate with each other.
 
| Layer | Name | What It Does |
|-------|------|--------------|
| 7 | Application | User-facing protocols- HTTP, DNS, email clients |
| 6 | Presentation | Data formatting and translation between systems |
| 5 | Session | Opens, manages, and closes communication sessions |
| 4 | Transport | Reliable (TCP) or fast (UDP) delivery of data |
| 3 | Network | Routing via IP addresses (where routers live) |
| 2 | Data Link | Physical MAC addressing, frames |
| 1 | Physical | Raw electrical signals over cables |
 
Key things to remember:
 
 Layer 3 is where routers operate (IP addresses)
 Layer 2 is where switches operate (MAC addresses)
 Layer 4 decides between TCP (reliable) and UDP (fast but no guarantees)
 At Layer 3, protocols like OSPF and RIP help find the best path for data

 
## Packets and Frames
 
Data traveling across a network is broken into smaller chunks:
 
 A Packet lives at Layer 3- it carries an IP address along with the actual data
 A Frame lives at Layer 2- it wraps the packet and adds MAC addresses for local delivery
Simple rule: packets have IPs, frames don't.
 
 
## TCP vs UDP
 
TCP (Transmission Control Protocol)- Reliable, connection-based. Before any data is sent, both sides go through a Three-Way Handshake:
 
1. SYN- Client says "I want to connect"
2. SYN/ACK- Server acknowledges and agrees
3. ACK- Client confirms, connection established
After that, data flows. When done, a FIN packet cleanly closes the connection. If something goes wrong, RST abruptly terminates it. TCP is used where accuracy matters- file transfers, web browsing, email.
 
UDP (User Datagram Protocol)- No handshake, no guarantees, just send and hope. Faster and lighter than TCP, which makes it suitable for video streaming, voice calls, or online gaming where speed matters more than perfect accuracy.
 

 
## Ports
 
Ports are numbered channels (0–65535) that help devices route incoming data to the right application.
 
| Protocol | Port |
|----------|------|
| FTP | 21 |
| SSH | 22 |
| HTTP | 80 |
| HTTPS | 443 |
| SMB | 445 |
| RDP | 3389 |
 

 
## Extending a Network
 
Port Forwarding makes a service on a local network accessible from the internet by mapping external traffic on a specific port to an internal device.
 
Firewalls control what traffic is allowed in and out of a network. They can filter based on source/destination IP, port, or protocol.
 
 Stateful Firewall- Tracks the full context of a connection and makes decisions based on behavior over time. More resource-intensive but smarter.
 Stateless Firewall- Checks each packet against fixed rules. Faster and lighter, good for handling high-volume attacks like DDoS, but less adaptive.
VPNs (Virtual Private Networks) create an encrypted tunnel between devices over the internet, allowing them to communicate as if they're on the same local network.
 
Common VPN technologies:
 PPP- Handles authentication and encryption but can't route on its own
 PPTP- Lets PPP traffic travel across networks; easy to set up but older encryption
 IPSec- Stronger encryption, harder to configure, widely supported
Switches can also operate at Layer 3, not just Layer 2. A VLAN (Virtual LAN) lets you logically segment a network- devices can share the same physical switch but remain isolated from each other.
 
