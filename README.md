<p align="center">
<img src="https://i.imgur.com/tXZhtKv.png" alt="osTicket logo"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>

In this tutorial, I will observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Command-Line Tools
- Network Protocols (ICMP, SSH, DHCP, DNS, RDP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>List of Steps</h2>

- Create a Resource Group
- Create a Virtual Machine
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Installation Steps</h2>

In Step 1: We create a Resource Group inside Azure.

<p>
<img src="https://i.imgur.com/C1atwQb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In step 2, create your Windows virtual machine. I typically create the VM in (US) East US.

While creating the VM, select the previously created Resource Group and allow it to create a new Virtual Network (Vnet) and Subnet. Make sure to use the password option under the Administrator Account section:
</p>
<br />

<p>
<img src="https://i.imgur.com/0wyRzfF.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In step 3, Create an Ubuntu virtual machine.

While creating the VM, select the previously created Resource Group and allow it to create a new Virtual Network (Vnet) and Subnet.
</p>
<br />

<p>
<img src="https://i.imgur.com/FqzmddI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

In step 4, Observe Your Virtual Network within Network Watcher:
</p>
<img src="https://i.imgur.com/lRSvHZY.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
In Step 5: Remote into your Windows 10 Virtual Machine, install Wireshark, open it and filter for ICMP traffic only.
</p>
</p>
<img src="https://i.imgur.com/3sJoaLr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/xSwoXK9.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Step 6, Retrieve the private IP address of the Ubuntu VM (VM2) and attempt to ping it from within the Windows 10 VM. Observe ping requests and replies within WireShark:
</p>
</p>
<img src="https://i.imgur.com/Eul54Ri.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/LGTlxLs.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark:
</p>
</p>
<img src="https://i.imgur.com/NPpsUrK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM:
</p>
</p>
<img src="https://i.imgur.com/LGTlxLs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
In Step 7, Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic, while back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity:
</p>
</p>
<img src="https://i.imgur.com/Z0UqSNi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
<img src="https://i.imgur.com/qe4OxFX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
<img src="https://i.imgur.com/FsSleSk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
In step 8, Re-enable ICMP traffic for the Network Security Group in your Ubuntu VM and back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line ping activity (should start working again).Finally, stop the ping activity:
</p>
</p>
</p>
<img src="https://i.imgur.com/8R4MmrS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
<img src="https://i.imgur.com/vrXbkyE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
<img src="https://i.imgur.com/MuLikZy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
In step 9,Time to observe SSH traffic

Back in Wireshark, filter for SSH traffic only and from your Windows 10 VM, “SSH into” your Ubuntu virtual machine (via its private IP address). Type commands (ls, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark.

Exit the SSH connection by typing ‘exit’ and pressing [return]:
</p>
</p>
</p>
<img src="https://i.imgur.com/8e3GZ1C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
<img src="https://i.imgur.com/TzpN9aB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
In Step 10, Next, we're going to observe DHCP Traffic

Back in Wireshark, filter for DHCP traffic only. From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)

Observe the DHCP traffic appearing in WireShark:
</p>
</p>
</p>
<img src="https://i.imgur.com/Pqx4Hq4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
In Step 11, we now observe our DNS traffic 

Back in Wireshark, filter for DNS traffic only.

From our Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are and observe the DNS traffic being shown in WireShark:
</p>
</p>
</p>
<img src="https://i.imgur.com/K7vBc2P.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
</p>
<img src="https://i.imgur.com/DPlxOXh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>
In Step 11 we will observe RDP traffic to finish up this tutorial

Back in Wireshark, filter for RDP traffic only using "tcp.port==3389".

We will be obseving a non-stop stream of traffic. Do you know why there is constant traffic in our tcp.port==3389?

The answer is because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted:
</p>
</p>
</p>
<img src="https://i.imgur.com/qvuMBz1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Now that we're finished observing the network, we clean up our azure environment. This will prevent us from incurring additional charges.

Close Remote Desktop connection, delete the Resource Group(s) created at the beginning of this tutorial, and verify Resource Group deletion. We will typically be notified or can click unde the bell notification just to make sure.




