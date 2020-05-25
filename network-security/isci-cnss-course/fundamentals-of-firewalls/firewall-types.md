# Firewall Types

### Packet Filtering Firewall

In a packet filtering firewall, each incoming packet is examined. Only those packets that match the criteria you set are allowed through.

There are a few disadvantages of packet filtering firewalls. One disadvantage is that they do not actually examine the packet or compare it to previous packets; therefore, they are quite susceptible to either a ping flood or SYN flood. They also do not offer any user authentication. Because this type of firewall looks only at the packet header for information, it has no information about the packet contents. 

It also does not track packets, so it has no information about the preceding packets. Therefore, if thousands of packets came from the same IP address in a short period of time, a host would not notice that this pattern is unusual. Such a pattern often indicates that the IP address in question is attempting to perform a DoS attack on the network.

A set of rules for a given firewall would need to cover the following:

* What types of protocols to allow \(FTP, SMTP, POP3, etc.\)
* What source ports to allow
* What destination ports to allow
* What source IP addresses to allow \(you can block certain IP addresses if you wish\)

### Stateful Packet Inspection

This type of firewall will examine each packet, denying or permitting access based not only on the examination of the current packet, but also on data derived from previous packets in the conversation.  Less susceptible to ping and SYN floods, and spoofing.

* They can tell whether the packet is part of an abnormally large stream of packets from a particular IP address, thus indicating a possible DoS attack in progress.
* They can tell whether the packet has a source IP address that appears to come from inside the firewall, thus indicating IP spoofing is in progress.
* They can also look at the actual contents of the packet, allowing for some very advanced filtering capabilities.

### Application Gateway

An application gateway \(also known as application proxy or application-level proxy\) is a program that runs on a firewall. This type of firewall derives its name from the fact that it works by negotiating with various types of applications to allow their traffic to pass the firewall. In networking terminology, negotiation is a term used to refer to the process of authentication and verification. In other words, rather than looking at the protocol and port the packet is using, an application gateway will examine the client application and the server-side application to which it is trying to connect.

This is significantly different from a packet filtering firewall, which examines the packets and has no knowledge of what sort of application sent them. Application gateways enable the administrator to allow access only to certain specified types of applications, such as web browsers or FTP clients.

When a client program, such as a web browser, establishes a connection to a destination service, such as a web server, it connects to an application gateway, or proxy. The client then negotiates with the proxy server in order to gain access to the destination service.

In effect, the proxy establishes the connection with the destination behind the firewall and acts on behalf of the client, hiding and protecting individual computers on the network behind the firewall. This process actually creates two connections. There is one connection between the client and the proxy server and another connection between the proxy server and the destination.

Once a connection is established, the application gateway makes all decisions about which packets to forward. Since all communication is conducted through the proxy server, computers behind the firewall are protected.

With an application gateway, each supported client program requires a unique program to accept client application data. This sort of firewall allows for individual user authentication, which makes them quite effective at blocking unwanted traffic. However, a disadvantage is that these firewalls use a lot of system resources. The process of authenticating client applications uses more memory and CPU time than simple packet filtering.

Application gateways are also susceptible to various flooding attacks \(SYN flood, ping flood, etc.\) for two reasons. The first potential cause of a flooding attack may be the additional time it takes for an application to negotiate authenticating a request. Remember that both the client application and the user may need to be authenticated. This takes more time than simply filtering packets based on certain parameters.

Application gateways may also be more susceptible to flooding attacks because once a connection is made, packets are not checked.

This vulnerability is mitigated somewhat by authenticating users. Provided the user logon method is secure \(appropriate passwords, encrypted transmission, etc.\), the likelihood that someone can use a legitimate connection through an application gateway for a flooding attack is reduced.

### Circuit Level Gateway

Circuit level gateway firewalls are similar to application gateways but are more secure and generally implemented on high-end equipment.

With an application gateway, first the client application is checked to see if access should be granted, and then the user is authenticated. With circuit level gateways, authenticating the user is the first step. The user’s logon ID and password are checked, and the user is granted access before the connection to the router is established. This means that each individual, either by username or IP address, must be verified before any further communication can take place.

Once this verification takes place and the connection between the source and destination is established, the firewall simply passes bytes between the systems. A virtual “circuit” exists between the internal client and the proxy server. Internet requests go through this circuit to the proxy server, and the proxy server delivers those requests to the Internet after changing the IP address. External users only see the IP address of the proxy server. 

Responses are then received by the proxy server and sent back through the circuit to the client. It is this virtual circuit that makes the circuit level gateway secure. The private secure connection between the client application and the firewall is a more secure solution than some other options, such as the simple packet filtering firewall and the application gateway.

While traffic is allowed through, external systems never see the internal systems.

