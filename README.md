![image](https://github.com/user-attachments/assets/b4900d81-e9f7-4e26-8e1e-c3746a3a213b)2<p align="center">
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
<br />

### Within the Networking section, ensure that the vnet is set to `claborde-vnet`, this will allow us to communcate with the `windows-vm` Virtual Machine
<p>
<img src="https://github.com/user-attachments/assets/0b63e004-9b67-43ae-80b0-52c221f2ad8f" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Review the following VM validation, once the validation passed create the VM
<p>
<img src="https://github.com/user-attachments/assets/f7d53541-e1b9-4263-b614-599462a1f7cc" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/96d90c76-0190-4452-a6fa-f4992bfae97e" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### End Results
<p>
<img src="https://github.com/user-attachments/assets/2a76a7f1-78cb-4e14-b989-339ff47ebde3" width="550" alt="Disk Sanitization Steps" />
</p>
<br />


## Observing ICMP Traffic
### Connect to the Windows 10 VM with RDP (Remote Desktop Connection)
<p>
<img src="https://github.com/user-attachments/assets/01e0a7db-ddea-4b54-978c-e24d22f9201e" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/86f4d355-b17a-4f67-a559-a45d2d7bb2b6" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/9561db0e-a525-4c3c-a1b0-f630b5d89fcc" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/bf3951e9-f5bf-4e18-95e2-43c2099cf5b8" width="550" alt="Disk Sanitization Steps" />
</p>

### Login to the VM 
<p>
<img src="https://github.com/user-attachments/assets/bf3951e9-f5bf-4e18-95e2-43c2099cf5b8" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/666d9289-4a9b-4255-8c6f-df500360be0c" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Accept the terms for the newly created VM
<p>
<img src="https://github.com/user-attachments/assets/3289a9aa-cdde-4914-8296-ccdc0507f6ea" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### End Results
<p>
<img src="https://github.com/user-attachments/assets/688b9539-0a58-4ede-b444-247c756b845b" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

