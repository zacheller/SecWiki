# Basic Network Utilities

### ipconfi&#x67;**/ifconfig**

This command gives you information about your connection to a network (or to the Internet). Most importantly, you find out your own IP address. The command also has the IP address for your default gateway, which is your connection to the outside world. Running the ipconfig command is a first step in determining your system’s network configuration. There are many flags, but a common method is to use `ipconfig /all`.

### ping

Ping is used to send a test packet, or echo packet, to a machine to find out whether the machine is reachable and how long the packet takes to reach the machine.

**TTL** means “time to live.” That time unit is how many intermediary steps, or hops, the packet should take to the destination before giving up.

### **tracert/traceroute**

Tracert not only tells you whether the packet got there and how long it took, but it also tells you all the intermediate hops it took to get there.

### netstat

Essentially, this command tells you what connections your computer currently has. If you see many private IP addresses, your network has internal communication going on.
