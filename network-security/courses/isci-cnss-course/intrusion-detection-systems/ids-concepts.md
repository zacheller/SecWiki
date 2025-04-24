# IDS Concepts

### Pre-emptive Blocking

Pre-emptive blocking seeks to prevent intrusions before they occur. This is done by observing any danger signs of imminent threats and then blocking the user or IP address from which these signs originate. Examples of this technique include attempts to detect the early Footprinting stages of an imminent intrusion, then blocking the IP or user that is the source of the Footprinting activity. If you find that a particular IP address is the source of frequent port scans and other scans of your system, then you would block that IP address at the firewall.

The complexity arises from distinguishing legitimate traffic from that indicative of an impending attack. Usually, a software system will simply alert the administrator that suspicious activity has taken place. A human administrator will then make the decision whether or not to block the traffic.

### Anomaly Detection

Any activity that does not match the pattern of normal user access is noted and logged. The software compares observed activity against expected normal usage profiles. Profiles are usually developed for specific users, groups of users, or applications. Any activity that does not match the definition of normal behaviour is considered an anomaly and is logged. Sometimes we refer to this as “trace back” detection or process. We are able to establish from where this packet was delivered. The specific ways in which an anomaly is detected include:

* Threshold monitoring
* Resource profiling
* User/group work profiling
* Executable profiling

#### Threshold Monitoring

Threshold monitoring pre-sets acceptable behaviour levels and observes whether these levels are exceeded. This could include something as simple as a finite number of failed login attempts or something as complex as monitoring the time a user is connected and the amount of data that user downloads. _Proper threshold values and the time frames at which to check those values are hard to calibrate--can generate false positives._

#### **Resource Profiling**

Resource profiling measures system-wide use of resources and develops a historic usage profile. Looking at how a user normally utilizes system resources enables the system to identify usage levels that are outside normal parameters. Such abnormal readings can be indicative of illicit activity underway. However, it may be difficult to interpret the meaning of changes in overall system usage. An increase in usage might simply indicate something benign like increased workflow rather than an attempt to breach security.

#### **User/Group Work Profiling**

In user/group work profiling, the IDS maintains individual work profiles about users and groups. These users and groups are expected to obey to these profiles. As the user changes his activities, his expected work profile is updated to reflect those changes. Some systems attempt to monitor the interaction of short-term versus long-term profiles. The short-term profiles capture recent changing work patterns, whereas the long-term profiles provide a view of usage over an extended period of time. However, it can be difficult to profile an irregular or dynamic user base. Profiles that are defined too broadly enable any activity to pass review, whereas profiles that are defined too narrowly may inhibit user work.

#### **Executable Profiling**

Executable profiling seeks to measure and monitor how programs use system resources with particular attention to those whose activity cannot always be traced to a specific originating user. For example, system services usually cannot be traced to a specific user launching them. Viruses, Trojan horses, worms, trapdoors, and other software attacks are addressed by profiling how system objects such as files and printers are normally used not only by users, but also by other system subjects on the part of users. In most conventional systems, for example, any program, including a virus, inherits all of the privileges of the user executing the software. The software is not limited by the principle of least privilege to only those privileges needed to properly execute. This openness in the architecture permits viruses to covertly change and infect totally unrelated parts of the system.

Executable profiling enables the IDS to identify activity that might indicate an attack. Once a potential danger is identified, the method of notifying the administrator, such as by network message or e-mail, is specific to the individual IDS.
