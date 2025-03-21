2<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [Project Walkthrough](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 22.04

<h2>High-Level Steps</h2>

- Create the Virtual Machines (vMs)
- Observe ICMP traffic
- Configure a Firewall Network Security Group
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<br />

<h1>Actions and Observations</h1>

<br />

## Virtual Machine Creations
### Create the Windows 10 Virtual Machine
<p>
<img src="https://github.com/user-attachments/assets/670e1774-2245-4c14-a5d9-732faa640870" width="550" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/user-attachments/assets/b91cdadf-339b-44ff-af63-64c4c4065a1a" width="550" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/user-attachments/assets/4abee16f-d5c8-452e-b1cd-fb0766c6d68d" width="550" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/user-attachments/assets/4abee16f-d5c8-452e-b1cd-fb0766c6d68d" width="550" alt="Disk Sanitization Steps"/>
</p>
<br />

### Set the username and password: `claborde-windows` as the username, and `AdminSecurePassword123!!!` as the password
<p>
<img src="https://github.com/user-attachments/assets/97ca7002-ca9c-410d-9629-91c89d427702" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Confirm the Licensing to avoid any errors
<p>
<img src="https://github.com/user-attachments/assets/74d11869-b445-45c5-95e2-e43d1a113b25" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Create a new Virtual Network
<p>
<img src="https://github.com/user-attachments/assets/99817edb-20f8-47cc-8fc5-c333e5e45450" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Review the following VM validation, once the validation passed create the VM
<p>
<img src="https://github.com/user-attachments/assets/1b05f267-f402-48b8-8196-847a49ba6444" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<<img src="https://github.com/user-attachments/assets/8f1d7082-774f-4da7-86d9-eff284e883e4" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Creating the Linux (Ubuntu) VM
<p>
<img src="https://github.com/user-attachments/assets/670e1774-2245-4c14-a5d9-732faa640870" width="550" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/user-attachments/assets/cfe66616-8ac5-4011-860f-d064a8658436" width="550" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/user-attachments/assets/040582b9-6bc2-4a5d-bd18-09a09c8636e0" width="550" alt="Disk Sanitization Steps"/>
</p>

### Change the authentication type as Password, then set the username to be `claborde-linux` and the password as `AdminSecurePassword123!!!`
<p>
<img src="https://github.com/user-attachments/assets/c0304833-3484-4260-8117-cad71a8d2b03" width="550" alt="Disk Sanitization Steps" />
</p>
