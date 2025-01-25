<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Configurations in Azure</h1>

<br /><h2>Objectives</h2>
This lab builds upon the previous one where I installed Active Directory and set up a domain controller. In this lab, I will configure Active Directory, join a client to the domain, and create user accounts.. <br />

<h2>Skills</h2>

- Azure Administration
- Active Directory Deployment
- Virtual Machine Configuration
- Group Policy Management

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (21H2)

<h2>Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/zo0BWbb.png" height="80%" width="80%" alt="Configuration Steps"/>
<img src="https://i.imgur.com/EHU2ooS.png" height="80%" width="80%" alt="Configuration Steps"/>
<img src="https://i.imgur.com/arbzQKI.png" height="80%" width="80%" alt="Configuration Steps"/>  
</p>
<p>

<br />- Open the **Active Directory Users and Computers** console.  
<br />- Right-click on your domain (e.g., `tawannatest.com`) and create a new **Organizational Unit (OU)**.  
<br />- Create two OUs: `_EMPLOYEES` and `_ADMINS` (used for later PowerShell scripts).  
<br />- Within the `_ADMINS` OU, create a new user (e.g., **Jane Doe**).  
<br />- To grant admin privileges:  
<br />- Right-click the user and select **Properties**.  
<br /> - Go to the **Member Of** tab and click **Add**.  
<br /> - Add the user to the **Domain Admins** security group.  
<br />- Log off as `labuser` and log in as `jane_admin` for further changes.  


</p>
<br />

<p>

</p>
<p>
   
</p>
 

<p>
<img src="https://i.imgur.com/YtUCCF9.png" height="80%" width="80%" alt="Configuration Steps"/>
<img src="https://i.imgur.com/q0tdWdI.png" height="80%" width="80%" alt="Configuration Steps"/>
<img src="https://i.imgur.com/URuAmsO.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
<br />- Join the client VM to the domain <br /> 
<br />- Open the **System** menu on the client VM. <br /> 
<br />- Click **Rename this PC (advanced)** and then **Change**. <br /> 
<br />- Enter the domain name and provide the necessary credentials (e.g., domain path and username). <br /> 
<br />- Log in with credentials in the format: `domain\username`. <br /> 
<br />- VerifyThe client VM is now part of the domain. <br /> 
<br />- VerifyOn the domain controller, the client appears under **Computers** in the **Active Directory Users and Computers** panel.<br />  
</p>
<br />

<p>
<img src="https://i.imgur.com/8FUGk5N.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
<br />


<br />- Enable Remote Desktop for non-administrative users <br />
<br />- Log in as an administrator (e.g., Jane).  
<br />- Open **System Properties** and click on **Remote Desktop**.  
<br />- Select users that can remotely access the PC.  
<br />- Allow **Domain Users** access to Remote Desktop.  
<br />- Non-administrative users can now log in to the client computer.  
<br />- Note: Group Policy can be used to apply this change across multiple systems, but it is not used in this lab.  
</p>
<br />

<p>
<img src="https://i.imgur.com/h9c3YOM.png" height="80%" width="80%" alt="Configuration Steps"/>
<img src="https://i.imgur.com/xalP6Gh.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>

<br />- Users can be created manually or with a script.<br />  
<br />- For this lab, a PowerShell script is used.<br />  
<br />- Log in to the domain controller with an admin account.<br />  
<br />- Open **PowerShell ISE** as an administrator.<br />  
<br />- Create a new file and paste the script into the ISE console.<br />  
<br />- Run the script and observe the accounts being created.<br />  
</p>

<p>
<img src="https://i.imgur.com/Xn5tQU2.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
<br />- Users created with the PowerShell script can now sign in to Client-1.  
<br />- Select a user and sign in with the domain context.  
<br />- Example: `ernestotest.com\bon.rovej`.
</p>
<br />

<h2>Lessons Learned</h2>

Doing this lab has made me learn how to set up Active Directory and join clients to the domain. I also created users and assigned the necessary permissions. Active Directory is not difficult to learn despite all the menu navigation that takes place. This lab is a segway for me to learn about DNS settings in-depth and file permissions in action. I will go into detail about these topics in other labs.
