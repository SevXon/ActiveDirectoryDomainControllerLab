\# Active Directory Domain Controller Lab



\## Project Overview



This project documents the installation and configuration of Active Directory Domain Services (AD DS) using Windows Server 2025 and Windows 11 Pro in a virtual lab environment.



The purpose of this project was to understand how organizations use Active Directory to centrally manage computers, authenticate users, control access to network resources, and improve network administration.



This project was completed as part of my IT and cybersecurity education at Full Sail University and is included in my personal cybersecurity portfolio.



\## Project Objectives



1\. Install Active Directory Domain Services on Windows Server 2025.

2\. Promote Windows Server to a Domain Controller.

3\. Create and configure a new Active Directory forest.

4\. Configure static IP addressing and DNS settings.

5\. Configure Windows Firewall settings for the lab environment.

6\. Establish network connectivity between Windows Server and Windows 11.

7\. Join Windows 11 Pro to the Active Directory domain.

8\. Verify successful domain communication and create virtual machine snapshots.



\## Technologies Used



\* Windows Server 2025

\* Windows 11 Pro

\* Active Directory Domain Services

\* Domain Name System (DNS)

\* Windows Defender Firewall

\* Proxmox Virtual Environment

\* PowerShell

\* Command Prompt



\## Lab Configuration



\*\*Domain:\*\* fsitbs.local



\*\*NetBIOS Domain Name:\*\* FSITBS



\*\*Domain Controller IP:\*\* 192.168.30.5



\*\*Default Gateway:\*\* 192.168.30.1



\*\*Subnet Mask:\*\* 255.255.255.0



\*\*Windows Client DNS:\*\* 192.168.30.5



The lab consisted of a Windows Server 2025 virtual machine, a Windows 11 Pro virtual machine, and a firewall virtual machine.



\## Implementation Summary



\### 1. Active Directory Installation



Installed the Active Directory Domain Services role using Windows Server Manager.



\### 2. Domain Controller Configuration



Promoted Windows Server 2025 to a Domain Controller and created a new Active Directory forest named fsitbs.local.



\### 3. Network Configuration



Configured static IP addressing and DNS settings to support communication between the Domain Controller and Windows client.



\### 4. Firewall Configuration



Adjusted Windows Defender Firewall settings according to the isolated classroom lab requirements.



Disabling firewall profiles was performed only for the educational lab. Production environments should maintain appropriate firewall protections.



\### 5. Windows Client Domain Join



Configured Windows 11 Pro to use the Domain Controller for DNS resolution and successfully joined the client computer to the fsitbs.local domain.



\### 6. Verification



Verified network connectivity using the ping command and received four successful responses with zero packet loss.



Confirmed Active Directory and DNS appeared in Windows Server Manager.



Captured screenshots documenting the configuration process and created virtual machine snapshots.



\## Troubleshooting Experience



During the initial Active Directory installation, Windows Server encountered error 0x800F0819.



Additional problems included Server Manager failing to retrieve available roles and features, installation wizard navigation issues, and Windows Server becoming unresponsive during troubleshooting.



After restarting and retrying the installation, Active Directory Domain Services installed successfully.



Another issue occurred during static IP configuration when an incorrect IP address caused Windows to display a gateway warning. Correcting the IP address resolved the warning.



These experiences reinforced the importance of verifying configuration settings, interpreting error messages, and troubleshooting systematically.



\## Security Considerations



Active Directory improves centralized administration but can become a valuable target for attackers.



If an attacker compromises a highly privileged domain account, they may gain extensive control over connected systems.



Important security practices include:



\* Applying the principle of least privilege.

\* Using strong authentication and appropriate password policies.

\* Monitoring authentication events and administrative activity.

\* Maintaining secure backups.

\* Restricting privileged account access.

\* Keeping systems updated.

\* Using network segmentation where appropriate.



\## What I Learned



This project helped me understand how Active Directory supports centralized network administration and how Domain Controllers manage authentication and access to resources.



I also gained practical experience configuring Windows Server, managing DNS settings, troubleshooting network configuration problems, and connecting Windows clients to a domain.



The project strengthened my understanding of enterprise network administration and provided foundational knowledge for future Active Directory security assessments and penetration testing labs.



\## Project Status



\*\*Completed:\*\* November 2, 2026



Active Directory installation, Domain Controller promotion, Windows client domain join, and initial connectivity verification completed.



Future improvements may include configuring organizational units, user accounts, security groups, Group Policy, and additional Active Directory security testing.



\## Author



SevXon



Cybersecurity Student | IT Infrastructure | Offensive Security



