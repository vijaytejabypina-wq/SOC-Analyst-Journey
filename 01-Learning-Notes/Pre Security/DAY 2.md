# Module 2
## Network fundamentals
### What is Networking?
It means connection between devices

What is the Internet?
It is a giant network consists of many many small networks, the first iteration of the Internet was within the ARPANET project in the late 1960s. This project was funded by the United States Defence Department and was the first documented network in action. However, it wasn't until 1989 when the Internet as we know it was invented by Tim Berners-Lee by the creation of the World Wide Web (WWW). It wasn't until this point that the Internet started to be used as a repository for storing and sharing information

Identifying devices on a network
To communicate and maintain order, devices must be both identifying and identifiable on a network. 
Devices can be identified with two means of identification, with one being permeable. These are:

    An IP Address
    A Media Access Control (MAC) Address -- think of this as being similar to a serial number.
IP address (or Internet Protocol) address can be used as a way of identifying a host on a network for a period of time, where that IP address can then be associated with another device without the IP address changing. 
Ex: 192.168.1.1
Devices on a network will all have a physical network interface, which is a microchip board found on the device's motherboard. This network interface is assigned a unique address at the factory it was built at, called a MAC (Media Access Control ) address.
Ex: a4:c3:b1:p2:o0:s9

Ping
Ping is one of the most fundamental network tools available to us. Ping uses ICMP (Internet Control Message Protocol) packets to determine the performance of a connection between devices

### Intro to LAN
A Local Area Network (LAN) is a computer network that interconnects devices within a limited area, such as a home, office, or school building.

LAN topologies

Star Topology
The main premise of a star topology is that devices are individually connected via a central networking device such as a switch or hub. This topology is the most commonly found today because of its reliability and scalability - despite the cost.

Bus Topology
This type of connection relies upon a single connection which is known as a backbone cable. This type of topology is similar to the leaf off of a tree in the sense that devices (leaves) stem from where the branches are on this cable.

Ring Topology
The ring topology (also known as token topology) boasts some similarities. Devices such as computers are connected directly to each other to form a loop, meaning that there is little cabling required and less dependence on dedicated hardware such as within a star topology.

What is a Switch?
Switches are dedicated devices within a network that are designed to aggregate multiple other devices such as computers, printers, or any other networking-capable device using ethernet. 

What is a Router?
It's a router's job to connect networks and pass data between them. It does this by using routing

Subnetting
Subnetting is the term given to splitting up a network into smaller, miniature networks within itself.

Address Resolution Protocol or for short ARP, is the technology that is responsible for allowing devices to identify themselves on a network.
Simply, ARP allows a device to associate its MAC address with an IP address on the network. Each device on a network will keep a log of the MAC addresses associated with other devices.

How does ARP Work?

Each device within a network has a ledger to store information on, which is called a cache. In the context of ARP, this cache stores the identifiers of other devices on the network.

In order to map these two identifiers together (IP address and MAC address), ARP sends two types of messages:

    ARP Request
    ARP Reply

When an ARP request is sent, a message is broadcasted on the network to other devices asking, "What is the mac address that owns this IP address?" When the other devices receive that message, they will only respond if they own that IP address and will send an ARP reply with its MAC address. The requesting device can now remember this mapping and store it in its ARP cache for future use.

DHCP

IP addresses can be assigned either manually, by entering them physically into a device, or automatically and most commonly by using a DHCP (Dynamic Host Configuration Protocol) server. When a device connects to a network, if it has not already been manually assigned an IP address, it sends out a request (DHCP Discover) to see if any DHCP servers are on the network. The DHCP server then replies back with an IP address the device could use (DHCP Offer). The device then sends a reply confirming it wants the offered IP Address (DHCP Request), and then lastly, the DHCP server sends a reply acknowledging this has been completed, and the device can start using the IP Address (DHCP ACK).

### OSI Model
The OSI model (or Open Systems Interconnection Model) is an essential model used in networking.  This critical model provides a framework dictating how all networked devices will send, receive and interpret data.

One of the main benefits of the OSI model is that devices can have different functions and designs on a network while communicating with other devices. Data sent across a network that follows the uniformity of the OSI model can be understood by other devices.

Application

Presentation

Session

Transport

Network

Data link

1. Physical
   This layer is one of the easiest layers to grasp. Put simply, this layer references the physical components of the hardware used in networking and is the lowest layer that you will find. Devices use electrical signals to transfer data between each other in a binary numbering system (1's and 0's).

For example, ethernet cables connecting devices

2. Data Link
   The data link layer focuses on the physical addressing of the transmission. It receives a packet from the network layer (including the IP address for the remote computer) and adds in the physical MAC (Media Access Control) address of the receiving endpoint. Inside every network-enabled computer is a Network Interface Card (NIC) which comes with a unique MAC address to identify it.

3. Network
   The third layer of the OSI model (network layer) is where the magic of routing & re-assembly of data takes place (from these small chunks to the larger chunk). Firstly, routing simply determines the most optimal path in which these chunks of data should be sent.

Whilst some protocols at this layer determine exactly what is the "optimal" path that data should take to reach a device, we should only know about their existence at this stage of the networking module. Briefly, these protocols include OSPF (Open Shortest Path First) and RIP (Routing Information Protocol). The factors that decide what route is taken is decided by the following:

    What path is the shortest? I.e. has the least amount of devices that the packet needs to travel across.
    What path is the most reliable? I.e. have packets been lost on that path before?
    Which path has the faster physical connection? I.e. is one path using a copper connection (slower) or a fibre (considerably faster)?

At this layer, everything is dealt with via IP addresses such as 192.168.1.100. Devices such as routers capable of delivering packets using IP addresses are known as Layer 3 devices — because they are capable of working at the third layer of the OSI model.

4. Transport
   Layer 4 of the OSI model plays a vital part in transmitting data across a network and can be a little bit difficult to grasp. When data is sent between devices, it follows one of two different protocols that are decided based upon several factors:

   TCP
   UDP
Let's begin with TCP. The Transmission Control Protocol (TCP). Potentially hinted by the name, this protocol is designed with reliability and guarantee in mind. This protocol reserves a constant connection between the two devices for the amount of time it takes for the data to be sent and received.

TCP make sure that data is sent and recieved

TCP is used for situations such as file sharing, internet browsing or sending an email. This usage is because these services require the data to be accurate and complete

 User Datagram Protocol (or UDP for short). This protocol is not nearly as advanced as its brother - the TCP protocol. It doesn't boast the many features offered by TCP, such as error checking and reliability. In fact, any data that gets sent via uDP is sent to the computer whether it gets there or not. There is no synchronisation between the two devices or guarantee; just hope for the best, and fingers crossed.

 5. Session
    Once data has been correctly translated or formatted from the presentation layer (layer 6), the session layer (layer 5) will begin to create and maintain the connection to other computer for which the data is destined. When a connection is established, a session is created. Whilst this connection is active, so is the session.

The session layer is also responsible for closing the connection if it hasn't been used in a while or if it is lost. Additionally, a session can contain "checkpoints," where if the data is lost, only the newest pieces of data are required to be sent, saving bandwidth. 

6. Presentation
   
Layer 6 of the OSI model is the layer in which standardisation starts to take place. Because software developers can develop any software such as an email client differently, the data still needs to be handled in the same way — no matter how the software works.

This layer acts as a translator for data to and from the application layer (layer 7). The receiving computer will also understand data sent to a computer in one format destined for in another format. For example, when you send an email, the other user may have another email client to you, but the contents of the email will still need to display the same.

7. Application
   The application layer of the OSI model is the layer that you will be most familiar with. This familiarity is because the application layer is the layer in which protocols and rules are in place to determine how the user should interact with data sent or received.

Everyday applications such as email clients, browsers, or file server browsing software such as FileZilla provide a friendly, Graphical User Interface (GUI) for users to interact with data sent or received. Other protocols include DNS(Domain Name System), which is how website addresses are translated into IP addresses.

### Packets and frames

What are packets and frames?
Packets and frames are small pieces of data that, when forming together, make a larger piece of information or message. However, they are two different things in the OSI model. 

A packet is a piece of data from Layer 3 (Network Layer) of the OSI model, containing information such as an IP header and payload. A frame, however, is used at Layer 2 (Data Link) of the OSI model, which, encapsulates the packet and adds additional information such as MAC addresses.

Simply packet has an IP address and Frame does not have an IP address

TCP/IP

TCP (or Transmission Control Protocol for short) is another one of these rules used in networking.

This protocol is very similar to the OSI model that we have previously discussed in room three of this module so far. The TCP/IP protocol consists of four layers and is arguably just a
summarised version of the OSI model. These layers are:
. Application
. Transport
· Internet
. Network Interface

Very similar to how the OSI model works, information is added to each layer of the TCP model as the piece of data (or packet) traverses it. As you may recall, this process is known as
encapsulation - where the reverse of this process is decapsulation.

One defining feature of TCP is that it is connection-based, which means that TCP must establish a connection between both a client and a device acting as a server before data is sent.
Next, we'll come on to discuss the Three-way handshake - the term given for the process used to establish a connection between two devices. The Three-way handshake communicates
using a few special messages:

1. SYN

A SYN message is the initial packet sent by a client during the handshake. This packet is used to initiate a connection and synchronise the two devices
together (we'll explain this further later on).

2. SYN/ACK

This packet is sent by the receiving device (server) to acknowledge the synchronisation attempt from the client.

3. ACK

The acknowledgement packet can be used by either the client or server to acknowledge that a series of messages/packets have been successfully received.

4. DATA

Once a connection has been established, data (such as bytes of a file) is sent via the "DATA" message.

5. FIN

This packet is used to cleanly (properly) close the connection after it has been complete.

6. RST

This packet abruptly ends all communication. This is the last resort and indicates there was some problem during the process. For example, if the service or
application is not working correctly, or the system has faults such as low resources.

TCP Closing a Connection:

Let's quickly explain the process behind TCP closing a connection. First, TCP will close a connection once a device has determined that the other device has successfully
received all of the data.

Because TCP reserves system resources on a device, it is best practice to close TCP connections as soon as possible.

To initiate the closure of a TCP connection, the device will send a "FIN" packet to the other device. Of course, with TCP, the other device will also have to acknowledge this
packet.

UDP/IP

The User Datagram Protocol (UDP) is another protocol that is used to communicate data between devices.

Unlike its brother TCP, UDP is a stateless protocol that doesn't require a constant connection between the two devices for data to be sent. For example, the Three-way handshake does
not occur, nor is there any synchronisation between the two devices.

Recall some of the comparisons made about these two protocols in Room 3: "OSI Model". Namely, UDP is used in situations where applications can tolerate data being lost (such as video
streaming or voice chat) or in scenarios where an unstable connection is not the end-all.

Ports

ports are an essential point in which data can be exchanged. 
Networking devices also use ports to enforce strict rules when communicating with one another. When a connection has been established (recalling from the OSI model's room), any data sent or received by a device will be sent through these ports. In computing, ports are a numerical value between 0 and 65535 (65,535).

File Transfer Protocol (FTP)  21

This protocol is used by a file-sharing application built on a client-server model, meaning you can download files from a
central location.

Secure Shell (SSH) 22

This protocol is used to securely login to systems via a text-based interface for management.

HyperText Transfer Protocol (HTTP) 80

This protocol powers the World Wide Web (WWW)! Your browser uses this to download text, images and videos of web
pages.

HyperText Transfer Protocol Secure
(HTTPS) 443

This protocol does the exact same as above; however, securely using encryption.

Server Message Block (SMB) 445

This protocol is similar to the File Transfer Protocol (FTP); however, as well as files, SMB allows you to share devices like
printers.

Remote Desktop Protocol (RDP) 3389

This protocol is a secure means of logging in to a system using a visual desktop interface (as opposed to the text-based
limitations of the SSH protocol).

### Extending Your Network

Port Forwarding
Port forwarding is an essential component in connecting applications and services to the Internet. Without port forwarding, applications and services such as web servers are only available to devices within the same direct network.

Firewalls
A firewall is a device within a network responsible for determining what traffic is allowed to enter and exit. Think of a firewall as border security for a network. An administrator can
configure a firewall to permit or deny traffic from entering or exiting a network based on numerous factors such as:

. Where the traffic is coming from? (has the firewall been told to accept/deny traffic from a specific network?)
. Where is the traffic going to? (has the firewall been told to accept/deny traffic destined for a specific network?)
. What port is the traffic for? (has the firewall been told to accept/deny traffic destined for port 80 only?)
. What protocol is the traffic using? (has the firewall been told to accept/deny traffic that is UDP, TCP or both?)

Stateful firewall

This type of firewall uses the entire information from a connection; rather than inspecting an individual packet, this firewall determines the behaviour of a
device based upon the entire connection.

This firewall type consumes many resources in comparison to stateless firewalls as the decision making is dynamic. For example, a firewall could allow the first
parts of a TCP handshake that would later fail.

If a connection from a host is bad, it will block the entire device.

Stateless firewall

This firewall type uses a static set of rules to determine whether or not individual packets are acceptable or not. For example, a device sending a bad packet will
not necessarily mean that the entire device is then blocked.

Whilst these firewalls use much fewer resources than alternatives, they are much dumber. For example, these firewalls are only effective as the rules that are
defined within them. If a rule is not exactly matched, it is effectively useless.

However, these firewalls are great when receiving large amounts of traffic from a set of hosts (such as a Distributed Denial-of-Service attack)

VPN basics

A Virtual Private Network (or VPN for short) is a technology that allows devices on separate networks to communicate securely by creating a dedicated path between each other over the
Internet (known as a tunnel). Devices connected within this tunnel form their own private network.

PPP

This technology is used by PPTP (explained below) to allow for authentication and provide encryption of data. VPNs work by using a private key and public
certificate (similar to SSH). A private key & certificate must match for you to connect.

This technology is not capable of leaving a network by itself (non-routable).

PPTP

The Point-to-Point Tunneling Protocol (PPTP) is the technology that allows the data from PPP to travel and leave a network.

PPTP is very easy to set up and is supported by most devices. It is, however, weakly encrypted in comparison to alternatives.

IPSec

Internet Protocol Security (IPsec) encrypts data using the existing Internet Protocol (IP) framework.

IPSec is difficult to set up in comparison to alternatives; however, if successful, it boasts strong encryption and is also supported on many devices.

What is a Router?
It's a router's job to connect networks and pass data between them. It does this by using routing (hence the name router!).

Routing is the label given to the process of data travelling across networks. Routing involves creating a path between networks so that this data can be successfully delivered. Routers
operate at Layer 3 of the OSI model. They often feature an interactive interface (such as a website or a console) that allows an administrator to configure various rules such as port
forwarding or firewalling.

What is a Switch?

A switch is a dedicated networking device responsible for providing a means of connecting to multiple devices. Switches can facilitate many devices (from 3 to 63) using Ethernet cables.

Switches can operate at both layer 2 and layer 3 of the OSI model. However, these are exclusive in the sense that Layer 2 switches cannot operate at layer 3.

A technology called VLAN (Virtual Local Area Network) allows specific devices within a network to be virtually split up. This split means they can all benefit from things such as an Internet connection but are treated separately.
