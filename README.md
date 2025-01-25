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
  - Right-click the user and select **Properties**.  
  - Go to the **Member Of** tab and click **Add**.  
  - Add the user to the **Domain Admins** security group.  
- Log off as `labuser` and log in as `jane_admin` for further changes.  


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
<br />- Join the client VM to the domain:  
<br />- Open the **System** menu on the client VM.  
<br />- Click **Rename this PC (advanced)** and then **Change**.  
<br />- Enter the domain name and provide the necessary credentials (e.g., domain path and username).  
<br />- Log in with credentials in the format: `domain\username`.  
<br />- VerifyThe client VM is now part of the domain.  
<br />- VerifyOn the domain controller, the client appears under **Computers** in the **Active Directory Users and Computers** panel.  
</p>
<br />

<p>
<img src="https://i.imgur.com/jmR2LXa.png" height="80%" width="80%" alt="Configuration Steps"/>
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
<img src="https://i.imgur.com/HrI6BTq.png" height="80%" width="80%" alt="Configuration Steps"/>
<img src="https://i.imgur.com/c7LaN48.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
Creating users can be done manually or through the use of a script. For this lab, I will be using a PowerShell script. The PowerShell script can be found <a href="https://github.com/AsiaPonder001/BunchofUsers/blob/main/README.md?plain=1)"> here. </a> On the domain controller, open PowerShell ISE as an administrator (and make sure you are logged in with an admin account on the domain controller). Create a new file and paste the script into ISE console. Run the script and observe the accounts being created. 
</p>
<br />

<p>
<img src="https://i.imgur.com/Xn5tQU2.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
After creating the users, Client-1 can now be signed in as one of the new users that were created from the PowerShell script. Pick a name and simply sign in to the client with the context of the domain. In my case, it is ernestotest.com\bon.rovej.
</p>
<br />

<h2>Lessons Learned</h2>

Doing this lab has made me learn how to set up Active Directory and join clients to the domain. I also created users and assigned the necessary permissions. Active Directory is not difficult to learn despite all the menu navigation that takes place. This lab is a segway for me to learn about DNS settings in-depth and file permissions in action. I will go into detail about these topics in other labs.
