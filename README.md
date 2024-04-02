<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create our Resources in Azure
- Observe ICMP Traffic
  

<h2>Actions and Observations</h2>

<h4>Create our Resources in Azure</h4>

- Create a Resource Group
- Create a Windows 10 Virtual Machine (VM), select the previously created Resource Group

  ![vm1](https://github.com/edem4963/azure-network-protocols/assets/112492837/77598df3-0458-4eb7-9b6b-43b2785c0174)

  ![vm2](https://github.com/edem4963/azure-network-protocols/assets/112492837/6ba76e2f-d051-4604-98e1-a6a64b570a2c)


- While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet

  ![vm3](https://github.com/edem4963/azure-network-protocols/assets/112492837/365acbad-9e9e-4636-9cba-3c91d443b04f)

- Create a Linux (Ubuntu) VM, select the previously created Resource Group and Vnet
  ![vm5](https://github.com/edem4963/azure-network-protocols/assets/112492837/40cf29fc-5b5d-42fd-b5dc-2d8c580edf46)

  ![vm4](https://github.com/edem4963/azure-network-protocols/assets/112492837/24a869ee-9d3b-4d1a-8f7a-62b1e2863f3b)

- Observe Your Virtual Network within Network Watcher

<h4>Observe ICMP Traffic</h4>

- Use Remote Desktop to connect to your Windows 10 Virtual Machine

![vm6](https://github.com/edem4963/azure-network-protocols/assets/112492837/d5501ca5-c49e-47cf-9ecc-f3dad1402e7d)

- Within your Windows 10 Virtual Machine, Install Wireshark
- Open Wireshark and filter for ICMP traffic only

  ![vm7](https://github.com/edem4963/azure-network-protocols/assets/112492837/c911907f-7d5d-44d6-b7e8-4ac680a6fae4)

- Retrieve the private IP address of the Ubuntu VM from azure portal and attempt to ping it from within the Windows 10 VM
- Observe ping requests and replies within WireShark
- From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
- Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM

  ![vm8](https://github.com/edem4963/azure-network-protocols/assets/112492837/a88adcb0-f61a-4294-be49-da7cbcb8546b)

- Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic

  ![vm9](https://github.com/edem4963/azure-network-protocols/assets/112492837/771b84c1-310d-4df0-b520-cc52f7b6f1df)

- Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
- Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
- Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
- Stop the ping activity


<br />

<h2>Congrats!! You have a basic understanding of using wireshark for network traffic monitoring.</h2>
