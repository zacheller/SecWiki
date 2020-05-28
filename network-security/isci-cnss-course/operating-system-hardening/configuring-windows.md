# Configuring Windows

Properly configuring Windows \(Windows 7, 8, 10 and Server Editions\) consists of many facets. You must disable unnecessary services, properly configure the registry, enable the firewall, properly configure the browser, and more.

### Accounts, Users, Groups and Passwords

Any Windows system comes with certain default user accounts and groups. These can frequently be a starting point for intruders who want to crack passwords for those accounts and gain entrance onto a server or network. Simply renaming or disabling some of these default accounts can improve your security

#### Administrator Accounts

The default administrator account has administrative privileges, and hackers frequently seek to obtain logon information for an administrator account. Guessing a logon is a two-step process of first identifying the username, and then the password. Default accounts allow the hacker to bypass the first half of this process. Administrators should disable this account.

Having an account with administrative privileges is necessary for maintaining your server. The next step is adding a new account, one with an innocuous name and giving that account administrative privileges. Doing so makes a hacker’s task more difficult, as he must first discover what account actually has administrative privileges before he can even attempt to compromise that account.

Some experts suggest simply renaming the administrator account, or using an administrator account that has a username that indicates its purpose. That is not a recommendation for the following reasons:

* The whole point is that a hacker should not be able to identify which username has administrative privileges.
* Simply renaming the administrator account to a different name, but one that still indicates its administrative rights will not help this situation.

#### Other Accounts

The administrator account is the one most often targeted by hackers, but Windows also includes other default user accounts. Applying an equally demanding behaviour to all default accounts is a good idea. Any default account can be a gateway for a hacker to compromise a system. A few accounts that you should pay particular attention are:

* **IUSR\_Machine name:** When you are running IIS, a default user account is created for IIS. Its name is IUSR\_ and the name of your machine. This is a common account for a hacker to attempt to compromise. Altering this one in the manner suggested for the administrator account is advisable.
* **ASP.NET:** If your machine is running ASP.NET, a default account is created for web applications. A hacker that is familiar with .NET could target this account.
* **Database accounts:** Many relational database management systems, such as SQL Server, create default user accounts. An intruder, particularly one who wants to get at your data, could target these accounts.

When adding any new account, always give the new account’s user or group the least number and type of privileges needed to perform their job, even accounts for IT staff members. Below are some examples:

* A PC technician does not need administrative rights on the database server. Even though belongs to the IT department, does not need access to everything in that department.
* Managers may use applications that reside on a web server, but they certainly should not have rights on that server.
* Just because a programmer develops applications that run on a server does not mean that should have full rights on that server.

### Setting Security Policies

The first matter of concern is setting secure password policies. The default settings for Windows passwords are not secure. The table below shows the default password policies. Maximum password age refers to how long a password is effective before the user is forced to change that password. 

Enforce password history refers to how many previous passwords the system remembers, thus preventing the user from reusing passwords. Minimum password length defines the minimum number of characters allowed in a password. 

Password complexity means that the user must use a password that combines numbers, letters, and other characters. These are the default security settings for all Windows versions from Windows NT 4.0 forward. If your system is protected within a business environment, the settings at Local Security will be greyed out, indicating you do not have permissions to make changes.

| **Policy** | **Recommendation** |
| :--- | :--- |
| **Enforce password history** | **1 password remembered** |
| **Maximum password age** | **42 days** |
| **Minimum password age** | **0 days** |
| **Minimum password length** | **0 characters** |
| **Passwords must meet complexity requirements** | **Disabled** |
| **Store password using reversible encryption for all users in the domain** | **Disabled** |

The default password policies are not secure enough, but what policies should you use instead? Different experts answer that question differently. The table below shows the recommendations of Microsoft and the National Security Agency.

| **Policy** | **Microsoft** | **NSA** |
| :--- | :--- | :--- |
| **Enforce password history** | **3 passwords** | **5 passwords** |
| **Maximum password age** | **42 days** | **42 days** |
| **Minimum password age** | **2 days** | **2 days** |
| **Minimum password length** | **8 characters** | **12 characters** |
| **Passwords must meet complexity requirements** | **No recommendation** | **Yes** |
| **Store password using reversible encryption for all users in the domain** | **No recommendation** | **No recommendation** |

Developing appropriate password policies depends largely on the requirements of your network environment. If your network stores and processes highly sensitive data and is an attractive target to hackers, you must always skew your policies and settings toward greater security. However, bear in mind that if security measures are too complex, your users will find complying difficult. For example, very long, complex passwords \(such as $%Tbx38T@\_FgR$$\) make your network quite secure, but such passwords are virtually impossible for users to remember.

### Account Lockout Policies

When you open the Local Security Settings dialog, your options are not limited to setting password policies. You can also set account lockout policies. These policies determine how many times a user can attempt to log in before being locked out, and for how long to lock them out. The default Windows settings are shown in the table below.

| **Policy** | **Default Settings** |
| :--- | :--- |
| **Account lockout duration** | **Not defined** |
| **Account lockout threshold** | **0 invalid logon attempts** |
| **Reset account lockout counter after** | **Not defined** |

These default policies are not secure. Essentially, they allow for an infinite number of log-in attempts, making the use of password crackers very easy and virtually guaranteeing that someone will eventually crack one or more passwords and gain access to your system. The table below provides the recommendations from Microsoft and National Security Agency.

| **Policy** | **Microsoft** | **NSA** |
| :--- | :--- | :--- |
| **Account lockout duration** | **0, indefinite** | **15 hours** |
| **Account lockout threshold** | **5 attempts** | **3 attempts** |
| **Reset account after** | **15 minutes** | **30 minutes** |

### Registry Settings

The Windows Registry is a database used to store settings and options for Microsoft Windows operating systems. This database contains critical information and settings for all the hardware, software, users, and preferences on a particular computer. Whenever users are added, software is installed or any other change is made to the system \(including security policies\), that information is stored in the registry.

Secure registry settings are critical to securing a network. Unfortunately, that area is often overlooked. One thing to keep in mind is that if you do not know what you are doing in the registry, you can cause serious problems. So, if you are not very comfortable with the registry, do not touch it. Even if you are comfortable making registry changes, always back up the registry before any change.

### Registry Basics

The physical files that make up the registry are stored differently depending on which version of Windows you are using. Older versions of Windows \(that is, Windows 95 and 98\) kept the registry in two hidden files in your Windows directory, called USER.DAT and SYSTEM.DAT. In all versions of Windows since XP, the physical files that make up the registry are stored in %SystemRoot%\System32\Config. Since Windows 8, the file has been named ntuser.dat. 

Regardless of the version of Windows you are using, you cannot edit the registry directly by opening and editing these files. Instead you must use a tool, regedit.exe, to make any changes. There are newer tools like regedit32. However, many users find that the older regedit has a more user friendly “find” option for searching the registry. Either one will work.

Although the registry is referred to as a “database,” it does not actually have a relational database structure \(like a table in MS SQL Server or Oracle\). The registry has a hierarchical structure similar to the directory structure on the hard disk. In fact, when you use regedit, you will note it is organized like Windows Explorer.

Each of the main branches of the registry is briefly described in the following list. These five main folders are the core registry folders. A system might have additions, but these are the primary folders containing information necessary for your system to run.

* **HKEY\_CLASSES\_ROOT:** This branch contains all of your file association types, OLE information, and shortcut data.
* **HKEY\_CURRENT\_USER:** This branch links to the section of HKEY\_USERS appropriate for the user currently logged on to the PC.
* **HKEY\_LOCAL\_MACHINE:** This branch contains computer-specific information about the type of hardware, software, and other preferences on a given PC.
* **HKEY\_USERS:** This branch contains individual preferences for each user of the computer.
* **HKEY\_CURRENT\_CONFIG:** This branch links to the section of HKEY\_LOCAL\_MACHINE appropriate for the current hardware configuration.

A specific entry in the Windows Registry is referred to as a key. A key is an entry that contains settings for some particular aspect of your system. If you alter the registry, you are actually changing the settings of particular keys.

### Restrict Null Session Access

Null sessions are a significant weakness that can be exploited through the various shares that are on the computer. A null session is Windows’ way of designating anonymous connections. Any time you allow anonymous connections to any server, you are inviting significant security risks. Modify null session access to shares on the computer by adding **RestrictNullSessAccess**, a registry value that toggles null session shares on or off to determine whether the Server service restricts access to clients logged on to the system account without username and password authentication. Setting the value to **“1”** restricts null session access for unauthenticated users to all server pipes and shares except those listed in the **NullSessionPipes** and **NullSessionShares** entries.

**Key Path:** HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer

**Action:** Ensure that it is set to: Value = 1

### Restrict Null Session Access Over Named Pipes

The null session access over named pipes registry setting should be changed for much the same reason as the preceding null session registry setting. Restricting such access helps to prevent unauthorized access over the network. To restrict null session access over named pipes and shared directories, edit the registry and delete the values, as shown below.

**Key Path:** HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer

**Action:** Delete all values

### Restrict Anonymous Access

The anonymous access registry setting allows anonymous users to list domain user names and enumerate share names. It should be shut off. The possible settings for this key are:

* 0—Allow anonymous users
* 1—Restrict anonymous users
* 2—Allow users with explicit anonymous permissions

**Key Path:** HKLM\SYSTEM\CurrentControlSet\Control\Lsa

**Action:** Set Value = 2

### Remote Access to the Registry

Remote access to the registry is another potential opening for hackers. The Windows XP registry editing tools support remote access by default, but only administrators should have remote access to the registry. Fortunately, later versions of Windows turned this off by default. In fact, some experts advise that there should be no remote access to the registry for any person. This point is certainly debatable. If your administrators frequently need to remotely alter registry settings, then completely blocking remote access to them will cause a reduction in productivity of those administrators. However, completely blocking remote access to the registry is certainly more secure. To restrict network access to the registry:

**1**. Add the following key to the registry: HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Control\SecurePipeServers\winreg.

**2.** Select winreg, click the Security menu, and then click Permissions.

**3.** Set the Administrator’s permission to Full Control, make sure no other users or groups are listed, and then click OK.

Recommended Value = 0

### Services

A service is a program that runs without direct intervention by the computer user. In Unix/Linux environments, these are referred to as daemons. Many items on your computer are run as services. Internet Information Services, FTP Service, and many system services are good examples. Any running service is a potential starting point for a hacker. Obviously, you must have some services running for your computer to perform its required functions. However, there are services your machine does not use. If you are not using a service, it should be shut down.

### Encrypting File System

Beginning with Windows 2000, the Windows operating system has offered the Encrypting File System \(EFS\), which is based on public key encryption and takes advantage of the CryptoAPI architecture in Windows 2000. 

This still exists in Windows 7, 8, and 10; however, with the later versions of Windows, EFS is only available in the upper-end editions of Windows such as Windows Professional. With this system, each file is encrypted using a randomly generated file encryption key, which is independent of a user’s public/private key pair; this method makes the encryption resistant to many forms of cryptoanalysis-based attacks. For our purposes the exact details of how EFS encryption works are not as important as the practical aspects of using it.

### Security Templates

We have been discussing a number of ways for making a Windows system more secure, but exploring services, password settings, registry keys, and other tools can be a daunting task for the administrator who is new to security. Applying such settings to a host of machines can be a tedious task for even the most experienced administrator. 

The best way to simplify this aspect of operating system hardening is to use security templates. A security template contains hundreds of possible settings that can control a single or multiple computers. Security templates can control areas such as user rights, permissions, and password policies, and they enable administrators to deploy these settings centrally by means of Group Policy Objects \(GPOs\).

Security templates can be customized to include almost any security setting on a target computer. A number of security templates are built into Windows. These templates are categorized for domain controllers, servers, and workstations. These security templates have default settings designed by Microsoft. All of these templates are located in the C:\Windows\Security\Templates folder. The following is a partial list of the security templates that you will find in this folder:

* **Hisecdc.inf:** This template is designed to increase the security and communications with domain controllers.
* **Hisecws.inf:** This template is designed to increase security and communications for client computers and member servers.
* **Securedc.inf:** This template is designed to increase the security and communications with domain controllers, but not to the level of the High Security DC security template.
* **Securews.inf:** This template is designed to increase security and communications for client computers and member servers.
* **Setup security.inf:** This template is designed to reapply the default security settings of a freshly installed computer. It can also be used to return a system that has been misconfigured to the default configuration.

