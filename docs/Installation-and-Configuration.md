\# Active Directory Installation and Configuration



\*\*Project:\*\* Active Directory Domain Controller Lab

\*\*Author:\*\* SevXon

\*\*Date:\*\* November 2, 2026

\*\*Environment:\*\* Full Sail University Virtual Lab



\## 1. Project Overview



This project involved installing and configuring Active Directory Domain Services on Windows Server 2025 and connecting a Windows 11 Pro client to the newly created domain.



The goal was to gain practical experience with centralized network administration, authentication, DNS configuration, and domain management.



\## 2. Virtual Lab Environment



The project used three virtual machines hosted in a Proxmox environment.



\*\*Windows Server 2025:\*\* Used as the Domain Controller.



\*\*Windows 11 Pro:\*\* Used as the client computer joining the domain.



\*\*Firewall VM:\*\* Provided network connectivity and isolation for the virtual environment.



\### Network Configuration



| Setting                  | Configuration |

| ------------------------ | ------------- |

| Domain Name              | fsitbs.local  |

| NetBIOS Name             | FSITBS        |

| Domain Controller IP     | 192.168.30.5  |

| Subnet Mask              | 255.255.255.0 |

| Default Gateway          | 192.168.30.1  |

| Server Preferred DNS     | 192.168.30.1  |

| Windows 11 Preferred DNS | 192.168.30.5  |



\## 3. Installing Active Directory Domain Services



I opened Server Manager on Windows Server 2025 and selected Add Roles and Features.



I selected the role based installation option and chose the Windows Server virtual machine from the server pool.



Under Server Roles, I selected Active Directory Domain Services and added the required features.



After completing the installation wizard, Windows Server successfully installed the AD DS role.



\## 4. Promoting the Domain Controller



After installing Active Directory, I selected the option to promote the server to a Domain Controller.



I created a new Active Directory forest using the domain name `fsitbs.local`.



The NetBIOS domain name was automatically configured as `FSITBS`.



The DNS Server and Global Catalog options remained enabled.



I kept the default database, log file, and SYSVOL directory locations.



After reviewing the configuration, I ran the prerequisites check.



The server passed the required checks, allowing the Domain Controller installation to proceed.



Windows Server restarted automatically after completing the promotion.



\## 5. Configuring Network Settings



After logging back into Windows Server, I verified that Active Directory Domain Services and DNS appeared in Server Manager.



I opened the Ethernet adapter settings and configured a static IPv4 address.



The Domain Controller was assigned `192.168.30.5` with a subnet mask of `255.255.255.0`.



The default gateway and preferred DNS server were configured as `192.168.30.1`, following the classroom instructions.



These settings allowed the server to communicate with other virtual machines on the lab network.



\## 6. Windows Firewall Configuration



I opened Windows Defender Firewall with Advanced Security and reviewed the available firewall profiles.



Following the classroom instructions, I disabled the Domain and Private firewall profiles while leaving the Public profile enabled.



These changes were made specifically for the isolated educational environment.



In a production network, firewall protections should remain enabled and properly configured to allow only necessary traffic.



After applying the changes, I restarted Windows Server.



\## 7. Testing Network Connectivity



I started the Windows 11 Pro virtual machine and opened Command Prompt.



I tested network connectivity using the following command:



```cmd

ping 192.168.30.1

```



The test returned four successful responses with zero packet loss.



This confirmed that the Windows 11 client could reach the specified network address.



\## 8. Configuring Windows 11 DNS



I opened Windows 11 network settings and located the DNS server assignment.



I changed the DNS configuration to manual and enabled IPv4.



The preferred DNS server was configured as `192.168.30.5`, directing the Windows 11 client to the Domain Controller for DNS services.



\## 9. Joining Windows 11 to the Domain



I opened the Windows 11 system properties and accessed the computer name and domain settings.



I configured the Windows 11 computer name and selected the option to join a domain.



The domain name entered was:



`fsitbs.local`



When prompted, I entered the Domain Controller administrator credentials.



Windows displayed a welcome message confirming that the computer successfully joined the domain.



I captured the confirmation screenshot and restarted Windows 11 to complete the process.



\## 10. Virtual Machine Snapshots



After configuring the Domain Controller, I created a snapshot of the Windows Server virtual machine.



I also created a snapshot of Windows 11 after successfully joining the domain.



These snapshots provide recovery points that can be used if future configuration changes cause problems.



\## 11. Troubleshooting



\### Active Directory Installation Failure



During the initial installation, Windows Server displayed error `0x800F0819`.



Server Manager also experienced problems retrieving the available server roles and features.



The installation wizard became unresponsive, preventing the installation from continuing.



I restarted the virtual machine and attempted the installation again.



After additional troubleshooting and another installation attempt, Active Directory Domain Services installed successfully.



\### Incorrect Static IP Address



During network configuration, I accidentally entered an incorrect IP address.



Windows displayed a warning indicating that the default gateway was not on the same network segment as the configured IP address.



I reviewed the network settings and discovered that the address started with `169` instead of `192`.



After correcting the address to `192.168.30.5`, Windows accepted the configuration.



\### Server Manager Refresh Delay



After promoting the server to a Domain Controller, Active Directory and DNS did not immediately appear in Server Manager.



I refreshed Server Manager and allowed it to finish loading.



The AD DS and DNS roles then appeared in the navigation panel.



\## 12. Security Considerations



Active Directory provides centralized authentication and access management, but it also introduces security risks if administrative accounts or Domain Controllers become compromised.



A compromised privileged account could potentially allow an attacker to access multiple systems within the domain.



Organizations should implement least privilege, strong authentication, monitoring, regular backups, and appropriate firewall rules.



This project provided an introduction to the security considerations involved in managing enterprise Active Directory environments.



\## 13. Project Results



The project successfully demonstrated the following:



1\. Installation of Active Directory Domain Services.

2\. Promotion of Windows Server 2025 to a Domain Controller.

3\. Creation of the `fsitbs.local` domain.

4\. Configuration of static IP addressing and DNS.

5\. Verification of network connectivity.

6\. Successful Windows 11 domain join.

7\. Creation of virtual machine snapshots.

8\. Documentation of configuration and troubleshooting procedures.



\## 14. Conclusion



This project helped me understand how Active Directory works in a business environment and how IT administrators use Domain Controllers to manage connected systems.



I gained experience configuring Windows Server, troubleshooting installation problems, assigning network addresses, managing DNS settings, and joining a Windows client to a domain.



The experience also helped me understand why Active Directory security is important and how compromising privileged accounts could create risks across an organization's network.



This lab serves as a foundation for future projects involving Active Directory administration, Group Policy, user permissions, and offensive security testing.



