\# Active Directory Lab Troubleshooting



\*\*Project:\*\* Active Directory Domain Controller Lab

\*\*Author:\*\* SevXon

\*\*Date:\*\* November 2, 2026

\*\*Environment:\*\* Windows Server 2025 and Windows 11 Pro



\## 1. Active Directory Installation Failure



\### Problem



During the initial installation of Active Directory Domain Services, Windows Server displayed error `0x800F0819`.



The installation did not complete successfully.



\### Symptoms



The following problems occurred:



1\. Active Directory Domain Services failed to install.

2\. Server Manager reported an installation failure.

3\. The Add Roles and Features Wizard would not allow me to continue.

4\. The Next button remained unavailable.

5\. Server Manager could not retrieve the available server roles and features.



\### Troubleshooting



I attempted to install Active Directory again, but the installation wizard continued experiencing problems.



I restarted Windows Server to see whether the issue would clear.



During troubleshooting, Windows Server also became unresponsive, requiring me to stop and restart the virtual machine through the virtual lab interface.



I attempted to use DISM to investigate possible Windows component problems, but the command returned Error 87.



No component store corruption was confirmed.



\### Resolution



After restarting Windows Server and retrying the installation, Active Directory Domain Services installed successfully.



The exact underlying cause of the original installation failure was not confirmed.



\### What I Learned



Installation errors should be investigated carefully before repeatedly attempting the same procedure.



I also learned that troubleshooting requires checking error messages and verifying system behavior rather than assuming that restarting will resolve every problem.



\## 2. Server Manager Unable to Retrieve Features



\### Problem



After the initial Active Directory installation failed, Server Manager could not retrieve the list of available server roles and features.



\### Symptoms



The installation wizard displayed an error indicating that the request to list available features on the specified server had failed.



The Next button remained disabled.



\### Troubleshooting



I verified that the correct Windows Server was selected from the server pool.



I also checked Server Manager and restarted the virtual machine.



The problem continued during the initial troubleshooting attempts.



\### Resolution



The issue was no longer present when Active Directory Domain Services was successfully installed during a later attempt.



The specific cause was not identified.



\## 3. Incorrect Static IP Address



\### Problem



While configuring the Domain Controller's network settings, Windows displayed a warning that the default gateway was not on the same network segment as the configured IP address.



\### Cause



I accidentally entered an IP address beginning with `169` instead of `192`.



This placed the server's configured address outside the intended network.



\### Resolution



I corrected the server's IP address to:



`192.168.30.5`



The remaining network settings were:



| Setting         | Value         |

| --------------- | ------------- |

| Subnet Mask     | 255.255.255.0 |

| Default Gateway | 192.168.30.1  |

| Preferred DNS   | 192.168.30.1  |



After correcting the IP address, Windows accepted the configuration.



\### What I Learned



Even a small mistake in an IP address can prevent proper network communication.



Checking the IP address, subnet mask, and default gateway together is important when troubleshooting network configuration problems.



\## 4. Active Directory Not Appearing in Server Manager



\### Problem



After successfully promoting Windows Server 2025 to a Domain Controller and restarting, Active Directory Domain Services and DNS did not immediately appear in Server Manager.



\### Troubleshooting



I opened Server Manager and reviewed the available server roles.



The AD DS and DNS options were initially missing from the navigation panel.



I used the Refresh option and allowed Server Manager to complete its update.



\### Resolution



After refreshing, AD DS and DNS appeared in Server Manager.



\### What I Learned



Server Manager may take time to refresh its information after major configuration changes.



A missing role in the interface does not automatically mean the installation failed.



\## 5. Network Connectivity Verification



\### Objective



Verify that Windows 11 could communicate with the lab network before joining Active Directory.



\### Command Used



```cmd

ping 192.168.30.1

```



\### Results



Packets sent: 4

Packets received: 4

Packets lost: 0

Packet loss: 0%



\### Conclusion



The successful ping confirmed that Windows 11 could reach the specified network address.



This test verified basic IP connectivity but did not independently confirm that DNS or Active Directory authentication was functioning.



The subsequent successful domain join provided additional evidence that the client could communicate with the domain infrastructure.



\## 6. Lessons Learned



This lab reinforced several important troubleshooting principles.



First, configuration settings should always be verified before saving changes.



Second, error messages provide useful information that can help narrow down potential causes.



Third, restarting a system may resolve some temporary issues, but it does not identify the underlying cause.



Fourth, network connectivity should be tested before attempting operations that depend on communication between multiple systems.



Finally, documenting troubleshooting steps makes it easier to understand what happened and provides useful references for future projects.



\## 7. Final Outcome



Despite the initial installation failures and configuration problems, the Active Directory lab was completed successfully.



The final environment included:



1\. Windows Server 2025 with Active Directory Domain Services installed.

2\. A Domain Controller configured for `fsitbs.local`.

3\. DNS services enabled.

4\. Static IPv4 configuration on Windows Server.

5\. Windows 11 Pro joined to the Active Directory domain.

6\. Successful network connectivity testing.

7\. Virtual machine snapshots for recovery.



This troubleshooting experience helped strengthen my practical understanding of Windows Server administration, network configuration, and systematic problem solving.



