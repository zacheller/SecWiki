---
description: A network is simply a way for machines / computers to communicate.
---

# Network Basics

At the physical level, it consists of all the machines you want to connect and the devices you use to connect them. Individual machines are connected either with a physical connection \(a category 5 cable going into a network interface card, or NIC\) or wirelessly. To connect multiple machines together, each machine must connect to a hub or switch, and then those hubs / switches must connect together. In larger networks, each subnetwork is connected to the others by a router.

### Basic Network Structure

Some connection point\(s\) must exist between your network and the outside world. A barrier is set up between that network and the Internet, usually in the form of a firewall. The real essence of networks is communication allowing one machine to communicate with another.

### Data Packets

After you have established a connection with the network \(whether it is physical or wireless\), you need to send data.

The first part is to identify where you want to send it. All computers \(as well as routers and switches\), have an IP address.

The second part is to format the data for transmission. All data is in binary form \(1s and 0s\). This binary data is put into packets, all less than about 65,000 bytes. The first few bytes are the header. That header tells where the packet is going, where it came from, and how many more packets are coming as part of this transmission.

A packet can have multiple headers. In fact, most packets will have at least three headers. The IP header has information such as IP addresses for the source and destination, as well as what protocol the packet is. The TCP header has information such as port number. The Ethernet header has information such as the MAC address for the source and destination. If a packet is encrypted with Transport Layer Security \(TLS\), it will also have a TLS header.

### IP Addresses

1 byte is 8 bits \(1s and 0s\), and an 8-bit binary number converted to decimal format will be between 0 and 255. The total of 32 bits means that approximately 4.2 billion possible IP version 4 addresses exist.

The first byte \(or the first decimal number\) in an address reveals what network class that machine belongs to. The IP address 127.0.0.1 designates the machine you are on, regardless the IP address assigned to your machine. This address is referred as the loopback address. That address is used in testing the machine and the NIC card.

|  **Class** | IP Range |  **Use** |
| :--- | :--- | :--- |
| A | 0-126 | large networks |
| B | 128-191 | large corporate and govt networks |
| C | 192-223 | most common croup |
| D | 224-247 | reserved for multicasting |
| E | 248-255 | reserved for experimental use |

These particular classes are important as they tell you what part of the address represents the network and what part represents the node. For example, in a Class A address, the first octet represents the network, and the remaining three represent the node. In a Class B address, the first two octets represent the network, and the second two represent the node. And finally, in a Class C address, the first three octets represent the network, and the last represents the node.

Designated ranges that cannot be used as public IP addresses:

* **10.0.0.10 to 10.255.255.255**
* **172.16.0.0 to 172.31.255.255**
* **192.168.0.0 to 192.168.255.255**

**NAT:** One of the roles of a gateway router is to perform what is called network address translation \(NAT\). Using NAT, a router takes the private IP address on outgoing packets and replaces it with the public IP address of the gateway router so that the packet can be routed through the Internet.

**Subnetting** is simply splitting up a network into smaller portions. The **subnet mask** is a 32-bit number that is assigned to each host to divide the 32-bit binary IP address into network and node portions. You also cannot just put in any number you want. The first value of a subnet mask must be 255; the remaining three values can be 255, 254, 252, 248, 240, 224, or 128. Your computer will take your network IP address and the subnet mask and use a binary AND operation to combine them.

* If you have a Class C IP address, then your network subnet mask is 255.255.255.0. If you have a Class B IP address, then your subnet mask is 255.255.0.0. And finally, if it is Class A, your subnet mask is 255.0.0.0.
* Now if you want fewer than 255 nodes in your subnet, then you need something like 255.255.255.240 for your subnet. If you convert 240 to binary, it is 11110000. That means the first three octets and the first 4 bits of the last octet define the network. The last 4 bits of the last octet define the node. That means you could have as many as 1111 \(in binary\) or 15 \(in decimal\) nodes on this subnetwork.

**CIDR**: classless interdomain routing \(replaces the old system based on classes A, B, and C; extend the life of IPv4 as well as slow the growth of routing tables\) based on **VLSM: variable-length subnet masking**

* Rather to define a subnet mask, you have the IP address followed by a slash and a number. That number can be any number between 0 and 32.  The second part is the suffix which indicates how many bits are in the entire address \(e.g. `/12`\).
  * 192.168.1.10/24 \(basically a Class C IP address\)
  * 192.168.1.10/31 \(much like a Class C IP address with a subnet mask\)

Note that an ISP often will buy a pool of public IP addresses and assign them to you when you log on. Therefore, an ISP might own 1,000 public IP addresses and have 10,000 customers. Because all 10,000 customers will not be online at the same time, the ISP simply assigns an IP address to a customer when he or she logs on, and the ISP un-assigns the IP address when the customer logs off.

**IPv6**: utilizes a 128-bit address \(instead of 32\) and utilizes a hex numbering method in order to avoid long addresses

* only CIDR, no subnetting
* There is a loopback address for IPv6, and it can be written as `::/128`.

Differences between IPv4 and IPv6:

* Link/machine-local.
* IPv6 version of IPv4’s APIPA or Automatic Private IP Addressing. So if the machine is configured for dynamically assigned addresses and cannot communicate with a DHCP server, it assigns itself a generic IP address. DHCP, or Dynamic Host Configuration Protocol, is used to dynamically assign IP addresses within a network.
* IPv6 link/machine-local IP addresses all start with fe80::. So if your computer has this address, that means it could not get to a DHCP server and therefore made up its own generic IP address.
* Site/network-local.
* IPv6 version of IPv4 private address. In other words, these are real IP addresses, but they only work on this local network. They are not routable on the Internet.
* All site/network-local IP addresses begin with FE and have C to F for the third hexadecimal digit: FEC, FED, FEE, or FEF.
* DHCPv6 uses the Managed Address Configuration Flag \(M flag\).
* When set to 1, the device should use DHCPv6 to obtain a stateful IPv6 address.
* Other stateful configuration flag \(O flag\).
* When set to 1, the device should use DHCPv6 to obtain other TCP/IP configuration settings. In other words, it should use the DHCP server to set things like the IP address of the gateway and DNS servers.

### Uniform Resource Locator \(URL\)

Your computer, or your ISP, must translate the name you typed in \(called a Uniform Resource Locator, or URL\) into an IP address. The DNS \(Domain Name Service\) protocol, which is introduced along with other protocols a bit later, handles this translation process. If that address is found, your browser sends a packet \(using the HTTP protocol\) to TCP port 80. If that target computer has software that listens and responds to such requests \(like web-server software such as Apache or Microsoft Internet Information Services\), then the target computer will respond to your browser’s request and communication will be established.

#### Email

E-mail works the same way as visiting websites. Your e-mail client will seek out the address of your e-mail server. Then your e-mail client will use either **POP3** to retrieve your incoming e-mail, or **SMTP** to send your outgoing e-mail. Your e-mail server \(probably at your ISP or your company\) will then try to resolve the address you are sending to. If you send something to johndoe@gmail.com, your e-mail server will translate that e-mail address into an IP address for the e-mail server at gmail.com, and then your server will send your e-mail there. Note that newer e-mail protocols are out there; however, **POP3** is still the most commonly used.

**IMAP** is now widely used as well. Internet Message Access Protocol operates on port 143. The main advantage of **IMAP** over **POP3** is it allows the client to download only the email headers, and then the user can choose which messages to fully download. This is particularly useful for smart phones.

### MAC Addresses

A **MAC** address is a unique address for a **network interface card** \(**NIC**\). Every **NIC** in the world has a unique address that is represented by a six-byte hexadecimal number. The **Address Resolution Protocol** \(**ARP**\) is used to convert IP addresses to **MAC** addresses. So, when you type in a web address, the **DNS** protocol is used to translate that into an IP address. The **ARP** protocol then translates that IP address into a specific **MAC** address of an individual **NIC**.

IEEE assigns the first three bytes \(24 bits\) of the **MAC** address to a vendor. This part of the address is known as **Organizationally Unique Identifier** \(**OUI**\). The **OUI** helps professionals to determine the **MAC** address manufacturer. The remaining three bytes \(24 bits\) are assigned by the vendor. The **MAC** address is equal to 48 bits.

### Protocols

A protocol is, essentially, an agreed method of communication. In fact, this definition is exactly how the word protocol is used in standard, non-computer usage. Each protocol has a specific purpose and normally operates on a certain port. 

All these protocols are part of a suite of protocols referred to as TCP/IP \(Transmission Control Protocol/Internet Protocol\). Note: not a complete list of protocols.

| Protocol | Purpose | Port |
| :--- | :--- | :--- |
| FTP \(File Transfer Protocol\) | For transferring files between computers | 20,21 |
| SSH \(Secure Shell\) | A secure way to transfer files \(SCP\) and remotely login to a system | 22 |
| Telnet | Remotely login to a system | 23 |
| SMTP \(Simple Mail Transfer Protocol\) | For sending emails | 25 |
| WhoIS | A command to query a target for information | 43 |
| DNS \(Domain Name Service\) | For translating URLs to IP addresses | 53 |
| TFTP \(Trivial File Transfer Protocol\) | Quick but less reliable FTP server | 69 |
| HTTP \(Hypertext Transfer Protocol\) | For displaying web pages | 80 |
| POP3 \(Post Office Protocol v3\) | Retrieves email | 110 |
| NNTP \(Network News Transfer Protocol\) | Used for network news group | 119 |
| NetBIOS | An old Microsoft protocol for naming systems on a local network | 137,138,139 |
| IRC \(Internet Relay Chat\) | Chat Room | 194 |
| HTTPS \(Secure Hypertext Transfer Protocol\) | Encrypted HTTP \(SSL/TLS\) | 443 |
| SMB \(Server message Block\) | Used by Microsoft Active Directory | 445 |
| ICMP \(Internet Control Message Protocol\) | Simple packets containing error messages, informational and control messages | No specific port |

**Ports:** A port in networking terms is a handle, a connection point. It is a numeric designation for a particular pathway of communications. 

All network communication, regardless of the port used, comes into your computer through the connection on your NIC. You might think of a port as a channel on your TV. You probably have one cable coming into your TV but you can view many channels. You have one cable coming into your computer, but you can communicate on many different ports.

