<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: Create the Virtual machines needed for the task
- Step 2: Install Wireshark on Main Machine
- Step 3: Monitor DHCP, RDP, DNS, and ICMP traffic

<h2>Actions and Monitoring</h2>

<p>
<img src="https://i.imgur.com/HWK9zrh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Let's start by creating our virtual machines. Go to Azure and create two VMs, naming them VM-1 and VM-2 for ease of reference. Here i configured VM-2 to run Linux, just to show we can communicate with other machines regardless of Operating System.
</p>
<br />

<p>
<img src="https://i.imgur.com/PhMC4jq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Remote Desktop into VM-1 and install Wireshark using the brower provided. Open Wireshark and Install using the Wizard's default settings. Now on Wireshark, filter for ICMP traffic as our first protocol to monitor.
</p>
<br />

<p>
<img src="https://i.imgur.com/k6Ze5kV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now using command line we will perpetually ping VM-2's Private IP Address located in VM-2 overview settings on Azure using a command ping 'enter private-ip' -t. If successful we can now see Wireshark populate with ICMP traffic since ping uses that protocol.
</p>
<br />

<p>
<img src="https://i.imgur.com/4lR3pew.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, update VM-2's firewall settings to observe the changes via Wireshark. In Azure, search for Network Security Groups, and in VM-2's inbound security rules, add a rule to deny all ICMP traffic. Back in Wireshark, you should now see that ping requests are no longer receiving a response. This change is due to the firewall rule we applied. We can reverse that by re-opening the rule and allowing ICMP traffic once more.
</p>
<br />

<p>
<img src="https://i.imgur.com/nAA9SOI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark, filter for SSH traffic. SSH into your Ubuntu virtual machine (VM-2), log in using the prompts and execute various commands (touch hi.txt, ls lasth). You should see the traffic changes reflected via the SSH filter on Wireshark. Type exit in command line to close your SSH connection.
</p>
<br />

<p>
<img src="https://i.imgur.com/T5RuycA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Change Wireshark's filter to DHCP and we'll observe changes by attempting to change VM-1's ip address. Run commands 'ipconfig' and 'ipconfig /renew', we can view the dhcp traffic.
<br />

<p>
<img src="https/k6Ze5kV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
AFASFAASFADSFDSAFDSAFASFASDFASDGAEGASDGASDDGASDGASDGASDG
<br />
