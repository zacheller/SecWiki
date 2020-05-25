# Honeypots

A honeypot is a single machine set up to simulate a valuable server or even an entire subnetwork. The idea is to make the honeypot so attractive that if a hacker breaches the network’s security, to be attracted to the honeypot rather than to the real system. Software can closely monitor everything that happens on that system, enabling tracking and perhaps identification of the intruder. Because the honeypot is not a real machine, no legitimate users should have a reason to connect to it.

### Specter

Specter works by appearing to run a number of services common to network servers. In fact, in addition to simulating multiple operating systems, it can also simulate the following services:

* SMTP
* FTP
* TELNET
* FINGER
* POP3
* IMAP4
* HTTP
* SSH
* DNS
* SUN-RPC

Users can set it up in one of five modes:

* Open: In this mode, the system behaves like a badly configured server in terms of security. The downside of this mode is that you are most likely to attract and catch the least skilful hackers.
* Secure: This mode has the system behaving like a secure server.
* Failing: This mode is interesting in that it causes the system to behave like a server with various hardware and software problems. This might attract some hackers because such a system is likely to be vulnerable.
* Strange: In this mode, the system behaves in unpredictable ways. This sort of behaviour is likely to attract the attention of a more talented hacker and perhaps cause him to stay online longer trying to figure out what is going on. The longer the hacker stays connected, the better the chance of tracing him.
* Aggressive: This mode causes the system to actively try to trace back the intruder and derive his identity. This mode is most useful for catching the intruder.

In all modes, Specter logs the activity, including all information it can derive from the incoming packets. It also attempts to leave traces on the attacker’s machine, which can provide clear evidence for any criminal action. Users can also configure a fake password file in all modes.

There are multiple ways to configure this fake password file:

* **Easy:** In this mode the passwords are easy to crack, leading an intruder to believe that she has actually found legitimate passwords and usernames. Often a hacker with a legitimate logon will be less careful covering her tracks. If you know that logon is fake and the system is set up to monitor it, you can track it back to the hacker.
* **Normal:** This mode has slightly more difficult passwords than the easy mode.
* **Hard:** This mode has even harder passwords to crack. There is even a tougher version of this mode called mean, in which the passwords are very difficult to break so that the hacker can be traced while he is taking time to crack the passwords.
* **Fun:** This mode uses famous names as usernames. 
* **Warning:** In this mode the hacker gets a warning telling him he has been detected if he is able to crack the password file. The theory behind this mode is that most hackers are simply trying to see if they can crack a system and do not have a specific objective. Letting this sort of hacker know he has been detected is often enough to scare him off.

### Symantec Decoy Server

As the Decoy Server works as a honeypot, it also works as an IDS monitoring the network for signs of intrusion. If an attack is detected, all traffic related to that attack is recorded for use later in whatever investigative, criminal, or civil procedures that may arise.

Decoy Server is designed to be part of a suite of enterprise security solutions that work together, including enterprise versions of Symantec’s antivirus software, firewall software, and antispyware.

