Group_A_Project(Hagital_Consultant)
Secure Remote Access Setup and Configuration for Virtual Machines.


Tasks 1...

Windows VM Configuration and Access

VIRTUAL MACHINE SETUP:
CREATE A WINDOWS-BASED VIRTUAL MACHINE USING AZURE PORTAL.
In the portal's search bar, Search for virtual machine, Click on "Create virtual machine"

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

Username: Jane Doe
Password: Password
Confirm password: Password

Configure the network settings of the VM to ensure it is accessible from the network.
INBOUND PORT RULES
Public inbound ports: Allow selected ports.
Select inbound ports: RDP(3389)

DISK TAB.

OS Disk size: Image default (127 GiB)
OS Disk type: Premium SSD
Delete with VM: thick(Disck will delete alongside VM when VM is deleted)
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
.
.
.

  
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

Under "Remote Desktop" select "Allow remote connections to this computer" apply then OK...



b)
Configure the Firewall to Allow RDP Connections

Using Win + R to open the Run dialog box...
Type firewall.cpl enter.
click on "Allow an app or feature through windows defender firewall" in the left pane.

at the top-right, click change settings, check for "Remote Desktop" for both "Private and Public networks" click OK.


<img width="616" alt="ALLOW APPS THRU FIREWALL" src="https://github.com/user-attachments/assets/f7c1e54d-ec77-4ef1-ad28-a4182aab9507"/>






TASK 4.
Secure the Connection:
Set up a Virtual Private Network (VPN) or Network Security Group (NSG) to restrict access to the VM to specific IP addresses.
Enforce Multi-Factor Authentication (MFA) for remote access.
Document the steps taken to secure the VM and the RDP connection.

5. Test Remote Access:
   - Each group member should test remote access to the Windows VM using RDP.
   - Troubleshoot and resolve any connection issues.

6. *Monitoring and Logging:*
   - Enable and configure logging in the Windows Event Viewer to track remote access attempts.
   - Monitor the logs for any unauthorized access attempts and document the findings.

7. *Documentation:*
   - Prepare a comprehensive report detailing the setup, security measures, and testing process.
   - Include screenshots and command outputs where applicable.
