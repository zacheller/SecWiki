# IP Spoofing

IP spoofing is essentially a technique used by hackers to gain unauthorised access to computers. Although this is the most common reason for IP spoofing, it is occasionally done simply to mask the origins of a DoS attack.

If the intent is to gain unauthorised access, then the spoofed IP address will be that of a system the target considers a trusted host.

IP spoofing attacks are becoming less frequent, primarily because the venues they use are becoming more secure and in some cases are simply no longer used. However, spoofing can still be used, and all security administrators should address it.

* Do not reveal any information regarding your internal IP addresses. This helps prevent those addresses from being “spoofed.”
* Monitor incoming IP packets for signs of IP spoofing using network monitoring software. One popular product is Netlog. This and similar products seek incoming packets to the external interface that have both the source and destination IP addresses in your local domain, which essentially means an incoming packet that claims to be from inside the network, when it is clearly coming from outside your network. Finding one means an attack is underway.

The danger from IP spoofing is that some firewalls do not examine packets that appear to come from an internal IP address. Routing packets through filtering routers is possible if they are not configured to filter incoming packets whose source address is in the local domain.

On Debian, simple as adding `nospoof on` to the `/etc/host.conf` file.

Examples of router configurations that are potentially vulnerable include:

* Routers to external networks that support multiple internal interfaces
* Proxy firewalls where the proxy applications use the source IP address for authentication
* Routers with two interfaces that support subnetting on the internal network
* Routers that do not filter packets whose source address is in the local domain

