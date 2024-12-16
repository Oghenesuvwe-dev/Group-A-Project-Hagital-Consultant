*Group B: Windows VM Configuration and Access<br>

1.Virtual Machine Setup:<br>
- Create a Windows-based virtual machine using your Azure portal.
- Configure the network settings of the VM to ensure it is accessible from the network.<br>
 
 <br>
 In the azure portal's search bar<BR>

Search for virtual machine, click on "Virtual machine" under Services<BR>


<img width="1038" alt="Azure portal" src="https://github.com/user-attachments/assets/976a410a-61ef-4615-bc80-a9fdc8a76d55" /><BR>

Basics TAB.<BR>

PROJECT DETAILS<BR>
Select Subscription and Resource group.<BR>

INSTANCE DETAILS.<BR>
Vm Name: MyVm<br>
Region: East Us<br>
Availability Option: No Infrastructure Redundancy Required.<br>
Security Type: Standard<br>
Image: Windows Server 2022 Datacenter<br>
<img width="1417" alt="BASIC TAB IMAGE" src="https://github.com/user-attachments/assets/e87e71a6-6dce-439b-8885-ec3a16a60bba" /><BR>


Vm Architecture: X64<br>
Size: Standard_D2S_V3 - 2Vcpus,8 Gib Memory  

ADMINISTRATOR ACCOUNT.  

Username: MyVm<br>
Password: Password<br> 
Confirm password: Password<br>
<img width="1416" alt="ARC ADMIN" src="https://github.com/user-attachments/assets/61ca4416-e84f-46ca-9de4-2fdce6030aec" /><br>


<br>
CONFIGURE THE NETWORK SETTINGS OF THE VM TO ENSURE IT IS ACCESSIBLE FROM THE NETWORK.<br>
<br>
inbound port Rules<br>
Public inbound ports: Allow selected ports.<br> 
Select inbound ports: RDP(3389)<br>
<img width="1419" alt="INBOUND RDP" src="https://github.com/user-attachments/assets/e1c6275d-867b-4be5-9f02-7b6fd020a489" /><br>

  
<br>
DISK TAB.<br>

<br>
OS Disk size: Image default<br>  
OS Disk type: Premium SSD<br> 
Delete with VM: thick (Disk will delete alongside VM when VM is deleted)<br> 
Key management: Platform-managed key<br>

<img width="1418" alt="DISK" src="https://github.com/user-attachments/assets/aa26c616-59fa-47e7-a0a3-3a736c3dacf4" /><br>


<br>
NETWORKING TAB.<br>
<br>
Virtual Network: MyVm-Vnet<br>
Subnet: Default<br> 
Public IP: My IP<br> 
NIC network security group: Basic<br>
Public inbound ports: Allow selected ports<br> 
Select inbound ports: RDP(3389)<br>
Load balancing options: None<br>
<img width="1417" alt="NETWORKING TAB" src="https://github.com/user-attachments/assets/75c1b253-abbd-4fd9-99c8-702421930db0" /><br>
<br>
Review + create.<br> 

<br>
2.
User Account Management<br>
- Create user accounts on the Windows VM for each group member.<br>
- Assign appropriate permissions based on the principle of least privilege.<br>
<br>
On the VM, open "Computer Management" by entering "computer management" in windows search bar.<br>

<img width="980" alt="Com mngmnt" src="https://github.com/user-attachments/assets/a1050ba4-8afb-4725-ba57-36af4c5644d5" /><br>
<br>
Navigate to "Local Users and Groups" then click "Users".<br>
Right-click "Users" then select "New User"<br>
Fill in the details for a group member, then click "Create"<br>

<img width="570" alt="ADD USERS" src="https://github.com/user-attachments/assets/bebe910a-0c13-4eaa-b4e6-141b440743b1"/><br>

Assign appropriate permissions based on the principle of least privilege.<br>

<img width="351" alt="Babatunde" src="https://github.com/user-attachments/assets/541ab3e8-8e76-4ff2-b2c9-3fdd5730fabb"/>
<img width="352" alt="Danita" src="https://github.com/user-attachments/assets/b049eef1-9f8d-4445-8407-63b343bacb34"/>
<img width="260" alt="Gab" src="https://github.com/user-attachments/assets/b7b0806b-9930-4e0c-94e7-a0c5630b803d"/>
<img width="357" alt="Suvwe" src="https://github.com/user-attachments/assets/6dec0d05-3de9-48c3-963a-99f82ad2d01c"/>
<img width="353" alt="Success" src="https://github.com/user-attachments/assets/5cd4c2d4-728d-4fba-b180-6d63f5f803fd"/>
<img width="352" alt="Iyke" src="https://github.com/user-attachments/assets/2e28814a-7523-4c2a-b4cd-c5563b53680b"/>
<img width="355" alt="Ola" src="https://github.com/user-attachments/assets/897d6cac-7fb0-4b74-8158-c926fc230198"/><br>

  

3.<br>
Enable Remote Desktop Protocol (RDP)<br>
- Enable RDP on the Windows VM.<br>
- Configure the firewall to allow RDP connections (default port TCP/3389).<br>
<br>

a)- Enable RDP on the Windows VM.<br>
ON THE VM.<br>
Using the "Win + R" open the Run dialog box. enter "sysdm.cpl" to run open System Properties.<br>
click on the "Remote" tab at the top-right...<br>

<img width="407" alt="Remote" src="https://github.com/user-attachments/assets/66c87655-fced-4fd7-8669-04745f469e0e" /><br>

Under "Remote Desktop" > "Allow remote connections to this computer"  then OK...<br>

<br>
b)
Configure the Firewall to Allow RDP Connections<br>

Using Win + R to open the Run dialog box...<br>
Type firewall.cpl enter.<br>
click on "Allow an app or feature through windows defender firewall" in the left pane.<br>

at the top-right, click change settings, check for "Remote Desktop" for both "Private and Public networks" click OK.<br>


<img width="616" alt="ALLOW APPS THRU FIREWALL" src="https://github.com/user-attachments/assets/f7c1e54d-ec77-4ef1-ad28-a4182aab9507"/> <br>  



4.Secure the Connection:<br>
   - Set up a Virtual Private Network (VPN) or Network Security Group (NSG) to restrict access to the VM to specific IP addresses.<br>
   - Enforce Multi-Factor Authentication (MFA) for remote access.<br>
   - Document the steps taken to secure the VM and the RDP connection.<br>

CREATE INBOUND SECURITY RULES:  
On portal.azure.com > NSG's overview page.  
Click on "Inbound security rules" in the left-hand menu.<br>
Create a new rule.  

<img width="579" alt="Inbound Rules" src="https://github.com/user-attachments/assets/eb016845-6a4d-45f2-8f4a-79e91b3acc36" />

SOURCE:  "IP Addresses".  
SOURCE IP ADDRESSES/CIDR RANGES: "VM's IP Address".  
DESTINATION: "Any".  
SERVICE: "RDP"  
ACTION: "Allow"  
PRIORITY: "100"  
NAME: "AllowRDPFromSpecificIP"  
SAVE the rule.  

CREATE OUTBOUND SECURITY RULES:  

On portal.azure.com > NSG's overview page.  
Click on "Outbound security rules" in the left-hand menu.  
Create a new rule.  

<img width="579" alt="AllowAnyDNS Outbound" src="https://github.com/user-attachments/assets/7a3aaf0a-2134-4dbb-a8c4-55d910245830" />

Source:  "Any"  
Destination:  "IP Addresses"  
Destination IP Addresses/CIDR Ranges: "VM's IP Address"  
Service "TCP"  
Action:  "Allow"  
Priority: Set a priority number 200  
Name: "AllowOutboundToSpecificIP"  
Save the rule  
 


5.
Test Remote Access:*
   - Each group member should test remote access to the Windows VM using RDP.
   - Troubleshoot and resolve any connection issues.


TASK 6.  
MONITORING AND LOGGING
Enable and configure logging in the Windows "Event Viewer" to track remote access attempts.
Monitor the logs for any unauthorized access attempts and document the findings.  

ON THE VM

Using "Win + R". open "Run" dialog box, 
Type "eventvwr.msc" into the Run dialog box. Enter to open the Event Viewer
Navigate to Security Logs, double-click on it to view the  loggings.    



Configure Logging Settings:
In the Event Viewer, using "Filter Current Log..." in the right-hand Actions pane.
For logon events 
4624 for successful logons, 
4625 for failed logons  
4648 Logon attempt using explicit credentials. 


ENABLING AUDITING FOR LOGON EVENTS.
In the Event Viewer, 
Using Win + R, open "Run" dialog box type in "secpol.msc" then enter to open the Local Security Policy.
In the Local Policies, Audit Policy > then audit policies for Logon double click and check "Success and Failure"



Project Title: *Secure Remote Access Setup and Configuration for Virtual Machines

Duration: 3 weeks

*Objective:*
The objective of this project is to enable you to understand, configure, and secure remote access to virtual machines (VMs) running Windows operating systems. This group will be responsible for setting up a VM, ensuring it is securely accessible from a physical computer, and documenting the process and security measures.


  





6. *Monitoring and Logging:*
   - Enable and configure logging in the Windows Event Viewer to track remote access attempts.
   - Monitor the logs for any unauthorized access attempts and document the findings.

7. *Documentation:*
   - Prepare a comprehensive report detailing the setup, security measures, and testing process.
   - Include screenshots and command outputs where applicable.




