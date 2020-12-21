# Denial of Service Attacks

Many experts feel that it is so common because most forms of denial of service attacks are fairly easy to execute. The concept underlying the denial of service attack is based on the fact that any device has operational limits. A workload for a computer system might be defined in a number of different ways, including the number of simultaneous users, the size of files, the speed of data transmission, or the amount of data stored. Exceeding any of these limits will stop the system from responding. For example, if you can flood a web server with more requests than it can process, it will be overloaded and will no longer be able to respond to further requests.

### SYN Flood

Simply sending a flood of pings is the most primitive method of performing a DoS. The SYN flood attack depends on the hacker’s knowledge of how connections are made to a server. When a session is initiated between the client and server in a network using the TCP protocol, a small buffer space in memory is set aside on the server to handle the “hand-shaking” exchange of messages that sets up the session. The session-establishing packets include a SYN field that identifies the sequence in the message exchange. In this attack, an attacker sends a number of connection requests very rapidly and then fails to respond to the reply that is sent back by the server. In other words, the attacker requests connections, and then never follows through with the rest of the connection sequence. This has the effect of leaving connections on the server half open, and the buffer memory allocated for them is reserved and not available to other applications. Although the packet in the buffer is dropped after a certain period of time \(usually about three minutes\) without a reply, the effect of many of these false connection requests is to make it difficult for legitimate requests for a session to be established.

### Smurf Attack

In the Smurf attack, an ICMP packet is sent out to the broadcast address of a network, but its return address has been altered to match one of the computers on that network, most likely a key server. All the computers on the network will then respond by pinging the target computer.

ICMP packets use the Internet Control Message Protocol to send error messages on the Internet. Because the address of packets are sent to is a broadcast address, that address responds by echoing the packet out to all hosts on the network, who then send it to the spoofed source address. 

Continually sending such packets will cause the network itself to perform a DoS attack on one or more of its member servers. This attack is both clever and simple. The greatest difficulty is getting the packets started on the target network. This can be accomplished via some software such as a virus or Trojan horse that will begin sending the packets.

### Ping of Death

The PoD works to compromise systems that cannot deal with extremely large packet sizes. If successful, the server will actually shut down. It can, of course, be rebooted.

The only real safeguard against this type of attack is to ensure that all operating systems and software are routinely patched. This attack relies on vulnerabilities in the way a particular operating system or application handles abnormally large TCP packets.

If the operating system is properly designed, it will drop any oversized packets, thus negating any possible negative effects a PoD attack might have.

### UDP Flood

A UDP flood attack occurs when an attacker sends a UDP packet to a random port on the victim system. When the victim system receives a UDP packet, it will determine what application is waiting on the destination port. When it realizes that no application is waiting on the port, it will generate an ICMP packet of destination unreachable to the forged source address. If enough UDP packets are delivered to ports on the victim, the system goes down.

### DoS Tools

**Low Orbit Ion Cannon \(LOIC\)** and  **High Orbit Ion Cannon \(HOIC\)** are some widely available tools. They can be useful to test your own anti-DoS security measures.

