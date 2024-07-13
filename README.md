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

- Setting Up the Environment:

Create Azure Virtual Machines: Set up one or more Azure VMs to serve as the environment for observing network traffic.
![Screenshot 2024-07-12 221426](https://github.com/user-attachments/assets/0454cb5d-3c96-4191-af58-8ad535d8138a)
![Screenshot 2024-07-12 221455](https://github.com/user-attachments/assets/c30a0355-7db8-4f1a-a5f3-196ee86d33c2)
![Screenshot 2024-07-12 222117](https://github.com/user-attachments/assets/d7074296-b752-40ef-a9a9-f6650470a7f6)
![Screenshot 2024-07-12 223814](https://github.com/user-attachments/assets/f4bc19b1-47fc-4352-ab16-5a6fe763d11e)




- Connect to the Second VM via RDP:
- Open RDP Client: On the first VM, opened the Remote Desktop Connection application.
- Enter IP Address: Entered the public IP address of the second VM in the Remote Desktop Connection application.
- Authentication: Entered the appropriate credentials (username and password) for the second VM when prompted.
- Establish Connection: Clicked "Connect" to initiate the RDP session.
  ![Screenshot 2024-07-12 231428](https://github.com/user-attachments/assets/1e281671-9888-4c54-92f5-9c23d84696dc)
  ![Screenshot 2024-07-12 232253](https://github.com/user-attachments/assets/0ad25831-d964-40ec-95f4-f8090ecc6738)

- Install Wireshark
  ![Screenshot 2024-07-12 234446](https://github.com/user-attachments/assets/3138afdf-2f79-4114-8fa1-b1f22cb2f6fa)

- Capturing Network Traffic with Wireshark:
- Start Wireshark: Launch Wireshark on the VM or local machine.
- Select Network Interface: Choose the appropriate network interface for capturing traffic.
- Capture Traffic: Start the capture session to begin recording network packets to and from the VM.
  ![Screenshot 2024-07-13 000109](https://github.com/user-attachments/assets/00f52ca9-51c0-4d7a-8252-aaf756efe487)

  - Allow ICMP Traffic: Checked the Network Security Groups (NSGs) associated with both VMs to ensure they allowed ICMP traffic, which is necessary for ping operations.
  - Ping the Private IP Address:
  - Open Command Prompt: On the first VM, opened the Command Prompt or PowerShell.
  - Execute Ping Command: Typed the ping command followed by the private IP address of the second VM and pressed Enter:
    ![Screenshot 2024-07-13 001034](https://github.com/user-attachments/assets/2a9e6e2c-c0f8-4e0d-a0c1-1c705d9bf8ba)

  -  Ping the Second VM Continuously:
  - Open Command Prompt: On the first VM, opened the Command Prompt or PowerShell.
  - Execute Continuous Ping Command: Typed the following command to continuously ping the private IP address of the second VM:
  - Modify Firewall Settings on the Second VM:
  - Access the Second VM: Logged into the second VM using Remote Desktop Protocol (RDP) or another suitable method.
  - Open Windows Defender Firewall:
  - Navigated to Control Panel > System and Security > Windows Defender Firewall.
  - Clicked on "Advanced settings" to open the Windows Defender Firewall with Advanced Security.
  - Create New Inbound Rule to Block ICMP:
  - In the left-hand pane, selected "Inbound Rules".
  - Clicked on "New Rule..." in the right-hand pane.
  - Chose "Custom" and clicked "Next".
  - Selected "All programs" and clicked "Next".
  - For protocol type, chose "ICMPv4" and clicked "Next".
  - Specified "Any IP address" for both local and remote IP addresses and clicked "Next".
  - Selected "Block the connection" and clicked "Next".
  - Applied the rule to "Domain", "Private", and "Public" profiles and clicked "Next".
  - Gave the rule a name, such as "Block ICMP Traffic", and clicked "Finish".
  - Apply the Rule: Ensured the new rule was enabled and active.
    ![Screenshot 2024-07-13 002025](https://github.com/user-attachments/assets/d711d8e3-9071-45ab-85e5-beec457b6620)
    ![Screenshot 2024-07-13 003512](https://github.com/user-attachments/assets/c88f9ce4-1f24-4c55-bd39-3447cbbb8c45)
    ![Screenshot 2024-07-13 003919](https://github.com/user-attachments/assets/a681978b-b47a-4867-a9bc-059bfc1dae6e)

  - Capture SSH Traffic with Wireshark:
  - Open Wireshark: Launched Wireshark on the second VM.
  - Select Network Interface: Chose the network interface corresponding to the network connection used for communication between the VMs.
  - Start Capture: Clicked the "Start Capture" button to begin capturing network traffic.
  - Initiate SSH Connection:
  - Open SSH Client: On the second VM, opened a terminal (Linux) or PowerShell/Command Prompt (Windows).
  - Connect to First VM: Initiated an SSH connection to the first VM using its private IP address:
    ![Screenshot 2024-07-13 010443](https://github.com/user-attachments/assets/42705c56-e51b-4f48-9640-5a180fc2f84b)
    ![Screenshot 2024-07-13 010503](https://github.com/user-attachments/assets/e1fb04ba-2736-4f16-b685-d6cc4e514fb5)
    ![Screenshot 2024-07-13 011229](https://github.com/user-attachments/assets/af337f09-2994-46bd-b0bf-bd4f7a205b1e)

