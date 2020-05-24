---
description: The Open Systems Interconnect (OSI) model describes how networks communicate.
---

# The OSI Model

The OSI Model describes the various protocols and activities and states how the protocols and activities relate to each other. This model is divided into seven layers. It was originally developed by the International Organisation for Standardization \(ISO\) in the 1980s.

| **Layer** | **Description** | **Protocols** |
| :--- | :--- | :--- |
| **Application \(7\)** | **This layer interfaces directly to applications and performs common application services for the application processes** | **POP, SMTP, DNS, FTP, Telnet, HTTP** |
| **Presentation \(6\)** | **Relieves the application layer of concern regarding syntactical differences in data representation within the end-user systems.** | **Network Data Representation \(NDR\), Lightweight Presentation Protocol \(LPP\)** |
| **Session \(5\)** | **Provides the mechanism for managing the dialogue between end-user application processes** | **NetBIOS** |
| **Transport \(4\)** | **Provides end-to-end communication control** | **TCP,UDP** |
| **Network \(3\)** | **Routes information in the network** | **IP,ARP,ICMP** |
| **Data Link \(2\)** | **Describes the logical organisation of data bits transmitted on a particular medium. The data link layer is divided in two sublayers: the Media Access Control Layer \(MAC\) and the Logical Link Control Layer \(LLC\)** | **SLIP, PPP** |
| **Physical \(1\)** | **Describes the physical properties of various communication media as well as the electrical properties and interpretation of the exchanged signals. The physical layer is the actual NIC and the Ethernet cable.**  | **IEEE 1394, DSL, ISDN** |

