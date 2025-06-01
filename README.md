<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this project, I will observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<br>


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)


<br>


<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 22.04


<br>


<h2>High-Level Steps</h2>

- Create the Virtual Machines (vMs)
- Observe ICMP traffic
- Configure a Firewall Network Security Group
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<br />

<h2>Actions and Observations</h2>

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
<img src="https://github.com/user-attachments/assets/8f1d7082-774f-4da7-86d9-eff284e883e4" width="550" alt="Disk Sanitization Steps" />
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
<br />

### Change the authentication type as "Password", then set the username to be `claborde-linux` and the password as `AdminSecurePassword123!!!`
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
<br />

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

### Within the VM open Wireshark and begin a packet capture
<p>
<img src="https://github.com/user-attachments/assets/12091b30-e31f-4daa-a4fd-2095cec40f1c" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/3eb9ff00-72ad-4eba-84c8-05bdd9de6087" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Filter for ICMP Traffic
### No traffic will occur because the current VM(windows-vm) is not pinging an address
<p>
<img src="https://github.com/user-attachments/assets/679019eb-a15b-414f-a46a-28dc01b677ee" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Ping the Ubuntu private IP address
<p>
<img src="https://github.com/user-attachments/assets/17e080c0-fede-48ac-8427-6389c1dac8e0" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/82cc1468-46c7-4b78-9344-a7569136d892" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/e20efbbc-22d7-44dd-8a61-bb184eed8f14" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### After pinging the server, we are now able to see some ICMP traffic flow through
<p>
<img src="https://github.com/user-attachments/assets/32b57bf7-e8bd-4e64-85c5-de635d6c2cf7" width="550" alt="Disk Sanitization Steps" />
</p>
<br />


## Configuring a Network Security Group
### Run the following command to ping traffic non-stop
<p>
<img src="https://github.com/user-attachments/assets/5eea0dc7-aee8-4349-ba54-986bcc7d8178" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Disable incoming traffic for the Ubuntu server within Azure
<p>
<img src="https://github.com/user-attachments/assets/fa33c022-c1da-4485-9a23-945a9b4ae726" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/b4245058-1121-4426-86ff-13b6babbf957" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/3acfc415-6294-4c33-9413-5b1c323da3fc" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/3acfc415-6294-4c33-9413-5b1c323da3fc" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/2b04421c-a24f-449b-8db5-b48a02deef2d" width="550" alt="Disk Sanitization Steps" />
</p>
<br />


### After importing the rule, we can see that the request for communication between the VMs has timed out
<p>
<img src="https://github.com/user-attachments/assets/7ac57998-d181-40a1-8205-d7a60d28443f" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/0549e24d-2ed2-4fcc-9770-7d6f9044ba3b" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### Re-enable ICMP traffic to flow between the two VMs
<p>
<img src="https://github.com/user-attachments/assets/f7080043-995a-458d-9227-01d206f69283" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/88d66272-1101-494c-97e5-ad5e989bc9c4" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/38d047f2-a82c-4bc0-b8b4-d62dbbcb8fc0" width="550" alt="Disk Sanitization Steps" />
</p>
<br />


## Observe SSH Traffic
### Start a new packet capture within Wireshark and filter for SSH traffic
<p>
<img src="https://github.com/user-attachments/assets/356e5a81-093c-4171-b32d-77ccb8d739a3" width="550" alt="Disk Sanitization Steps" />
</p>
<br />


### To view traffic remote into the Ubuntu server with the SSH protocal
<p>
<img src="https://github.com/user-attachments/assets/e2837d6a-9b18-4cb7-b631-bb217950e0c7" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/a5cfe245-334b-49b6-a4a1-f0b7052dbd2c" width="550" alt="Disk Sanitization Steps" />
</p>
<br />


## Observe DHCP Traffic
### Start a new packet capture within Wireshark and filter for DHCP traffic
<p>
<img src="https://github.com/user-attachments/assets/d2cc2e84-e9b6-47b5-ae9b-6547fcc78218" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### To view traffic, assign a new IP address within the command line
<p>
<img src="https://github.com/user-attachments/assets/e423df97-bc59-4052-b7a1-f193a9e428fe" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/bb79fdf2-f1b0-41a7-ada7-26ac419adc85" width="550" alt="Disk Sanitization Steps" />
</p>
<br />


## Observe DNS Traffic
### Start a new packet capture within Wireshark and filter for DNS traffic
<p>
<img src="https://github.com/user-attachments/assets/78685079-05c5-46c8-ac61-e055569eacbb" width="550" alt="Disk Sanitization Steps" />
</p>
<br />

### To view traffic, run the `nslookup` command to get the DNS settings for a certain domain name
<p>
<img src="https://github.com/user-attachments/assets/9c381c48-dc0a-4c5e-a00f-4cc3cd6e9ec0" width="550" alt="Disk Sanitization Steps" />
</p>
<p>
<img src="https://github.com/user-attachments/assets/0abbb730-ef88-4bcc-8b73-efd337f1ad99" width="550" alt="Disk Sanitization Steps" />
</p>
<br />


## Observe RDP Traffic
### Start a new packet capture within Wireshark and filter for RDP traffic
<p>
<img src="https://github.com/user-attachments/assets/b16b7029-8e0e-4f0d-b318-ec5265afcff4" width="550" alt="Disk Sanitization Steps" />
</p>
<p>Traffic for the following protocal is non-stop due to the live stream from one computer to another.</p>

---

<br />

# End of Project
