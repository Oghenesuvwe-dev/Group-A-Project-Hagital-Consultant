GroupA Project (Hagital Consultant)
Secure Remote Access Setup and Configuration for Virtual Machines.


TASKS 1...  

Windows VM Configuration and Access  

VIRTUAL MACHINE SETUP:  
CREATE A WINDOWS-BASED VIRTUAL MACHINE USING AZURE PORTAL.  
In the portal's search bar, Search for virtual machine, click on "Create virtual machine"  

BASIC TAB.   

PROJECT DETAILS.  
Select Subscription and Resource group.  

INSTANCE DETAILS.  

Vm Name: MyVm
Region: East Us
Availability Option: No Infrastructure Redundancy Required. 
Security Type: Standard
Image Type: Windows Server 2022 Datacenter  
Vm Architecture: X64  
Size: Standard_D2S_V3 - 2Vcpus,8 Gib Memory  

ADMINISTRATOR ACCOUNT.  

Username: MyVm 
Password: Password  
Confirm password: Password  

CONFIGURE THE NETWORK SETTINGS OF THE VM TO ENSURE IT IS ACCESSIBLE FROM THE NETWORK.  

INBOUND PORT RULES  
Public inbound ports: Allow selected ports.  
Select inbound ports: RDP(3389)  
  

DISK TAB.

OS Disk size: Image default  
OS Disk type: Premium SSD  
Delete with VM: thick (Disk will delete alongside VM when VM is deleted)  
Key management: Platform-managed key  

NETWORKING TAB.

Virtual Network: MyVm-Vnet  
Subnet: Default   
Public IP: My IP  
NIC network security group: Basic  
Public inbound ports: Allow selected ports.  
Select inbound ports: RDP(3389)  
Load balancing options: None  

MANAGEMENT TAB  
Auto-shutdown to Enable auto-shutdown  
Shutdown time: 7PM  
Time zone: WAT  

Review + Create.  


  
TASK 2...  

USER ACCOUNT MANAGEMENT. 
Create user accounts on the windows virtual machine for the group members.

On the VM, open "Computer Management" search for computer management in windows search bar.

<img width="980" alt="Com mngmnt" src="https://github.com/user-attachments/assets/a1050ba4-8afb-4725-ba57-36af4c5644d5" />

Navigate to "Local Users and Groups" then click "Users".
Right-click "Users" then select "New User"
Fill in the details for each group member then click "Create"

<img width="570" alt="ADD USERS" src="https://github.com/user-attachments/assets/bebe910a-0c13-4eaa-b4e6-141b440743b1"/>

Assign appropriate permissions based on the principle of least privilege.

<img width="351" alt="Babatunde" src="https://github.com/user-attachments/assets/541ab3e8-8e76-4ff2-b2c9-3fdd5730fabb"/>
<img width="352" alt="Danita" src="https://github.com/user-attachments/assets/b049eef1-9f8d-4445-8407-63b343bacb34"/>
<img width="260" alt="Gab" src="https://github.com/user-attachments/assets/b7b0806b-9930-4e0c-94e7-a0c5630b803d"/>
<img width="357" alt="Suvwe" src="https://github.com/user-attachments/assets/6dec0d05-3de9-48c3-963a-99f82ad2d01c"/>
<img width="353" alt="Success" src="https://github.com/user-attachments/assets/5cd4c2d4-728d-4fba-b180-6d63f5f803fd"/>
<img width="352" alt="Iyke" src="https://github.com/user-attachments/assets/2e28814a-7523-4c2a-b4cd-c5563b53680b"/>
<img width="355" alt="Ola" src="https://github.com/user-attachments/assets/897d6cac-7fb0-4b74-8158-c926fc230198"/>  

  
TASK 3...



ENABLE RDP
a)  Enable RDP on the Windows VM.  
b) Configure the firewall to allow RDP connections (default port TCP/3389).  

a)
ON THE VM. 
Using the "Win + R" open the Run dialog box. enter "sysdm.cpl" to run open System Properties.
click on the "Remote" tab at the top-right...

<img width="407" alt="Remote" src="https://github.com/user-attachments/assets/66c87655-fced-4fd7-8669-04745f469e0e" />

Under "Remote Desktop" > "Allow remote connections to this computer"  then OK...


b)
Configure the Firewall to Allow RDP Connections

Using Win + R to open the Run dialog box...
Type firewall.cpl enter.
click on "Allow an app or feature through windows defender firewall" in the left pane.

at the top-right, click change settings, check for "Remote Desktop" for both "Private and Public networks" click OK.


<img width="616" alt="ALLOW APPS THRU FIREWALL" src="https://github.com/user-attachments/assets/f7c1e54d-ec77-4ef1-ad28-a4182aab9507"/> <br>  


TASK 4.  


SECURE THE CONNECTION:
SET UP A NETWORK SECURITY GROUP (NSG) TO RESTRICT ACCESS TO THE VM TO SPECIFIC IP ADDRESSES.  
 
CREATE INBOUND SECURITY RULES:  

On portal.azure.com > NSG's overview page.  
Click on "Inbound security rules" in the left-hand menu.  
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


TASK 5. 
TEST REMOTE ACCESS.  
Each group member should test remote access to the Windows VM using RDP.  
Troubleshoot and resolve any connection issues.    



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




