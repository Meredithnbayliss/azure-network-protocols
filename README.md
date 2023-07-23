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

While creating the VM, select the previously created Resource Group and allow it to create a new Virtual Network (Vnet) and Subnet. Make sure to use the password option under the Administrator Account section (not seen in image):


</p>
<br />

<p>
<img src="https://i.imgur.com/FqzmddI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

In step 4, Observe Your Virtual Network within Network Watcher:
</p>
<img src="https://i.imgur.com/lRSvHZY.png" width="80%" alt="Disk Sanitization Steps"/>
