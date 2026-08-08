<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure account
- Azure Windows 11 Virtual Machine
- Remote Desktop Connection (RDP)
- Internet Information Services (IIS) enabled
- osTicket Installation Files
- PHP Manager for IIS
- URL Rewrite Module
- Microsoft Visual C++ Redistributable
- MySQL Server
- HeidiSQL Database Management Tool

<h2>Installation Steps</h2>


Step 1: Create an Azure Virtual Machine
  
A. Create a Windows 10 Virtual Machine in Microsoft Azure.

- Resource Group: osTicket
- Virtual Machine Name: osticket-vm
- Operating System: Windows 10 Pro
- Size: Standard D2s v3 2vcpus
- Username and Password created during deployment

<p>
<img width="871" height="894" alt="Create a Windows 10 Virtual Machine in Microsoft Azure" src="https://github.com/user-attachments/assets/b8280aff-2202-4203-b437-f56972b9aa36" />
</p>
<p>

B. After deployment, connect to the VM using Remote Desktop Protocol (RDP).

<p>
<img width="931" height="756" alt="RDP to virtual machine" src="https://github.com/user-attachments/assets/d3bfa779-47a7-427a-a90a-7dddcf3d0bd8" />
</p>
<p>

</p>
<br />


Step 2: Install IIS

Open Control Panel → Programs → Turn Windows Features On or Off.

Enable:

- Internet Information Services (IIS)
- World Wide Web Services
- Application Development Features
  - CGI

Click OK and allow Windows to install the required features.

<p>
<img width="621" height="713" alt="Install IIS" src="https://github.com/user-attachments/assets/b8588838-bcf4-41ef-ba04-f21a0d30d988" />
</p>
<p>
</p>
<br />


Step 3: Download osTicket Installation Package

Download the osTicket installation package and supporting files.
https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD

These files include:

- PHP Manager for IIS
- URL Rewrite Module
- Visual C++ Redistributable
- MySQL Server
- HeidiSQL
- osTicket
- PHP binaries
  
  <p>
<img width="657" height="570" alt="download osTicket installation file" src="https://github.com/user-attachments/assets/f8b4d76a-43f8-4300-9323-acfbdd67d36f" />
</p>
<p>
  
</p>
<br />


Step 4: Install PHP Manager and URL Rewrite

A. PHP Manager for IIS
<p>
<img width="861" height="682" alt="php manager installed" src="https://github.com/user-attachments/assets/a31e1773-ea2a-4368-88e1-24ffdecf74c4" />
</p>
<p>

B. URL Rewrite Module
<p>
<img width="885" height="700" alt="rewrite installed" src="https://github.com/user-attachments/assets/f54f6307-2c94-4a61-9165-835caff97953" />
</p>
<p>

These components allow IIS to properly run PHP applications such as osTicket.
</p>
<br />

Step 5 - Extract php binaries

A. Create the directory C:\PHP

Go to file explorer -> c: drive -> create folder PHP 

B. From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

<p>
<img width="878" height="669" alt="extract php binaries" src="https://github.com/user-attachments/assets/d751ec31-0e35-4418-86fc-2323a6ff87e6" />
</p>
<p>
</p>
<br />

Step 6: From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

<p>
<img width="872" height="663" alt="visual c installed" src="https://github.com/user-attachments/assets/b588daf9-dc51-4070-a1e5-07a94711cd5e" />
</p>
<p>

This provides required runtime libraries for PHP and other dependencies.
</p>
<br />

Step 7: Install PHP

A. Open IIS Manager (open IIS as an Admin)
 <p>
<img width="870" height="652" alt="php manager admin" src="https://github.com/user-attachments/assets/91e4dd43-8049-447f-9201-7e66ecbf6d67" />
</p>
<p>

B. Using PHP Manager:

- Register PHP (we're making the server aware of the existence of PHP the computer and tell it where it is ):
  double click php manager -> register new php -> click three dots -> find php-cgi in C:PHP
 <p>
<img width="876" height="657" alt="php-cgi" src="https://github.com/user-attachments/assets/7d538cb8-f950-4ba1-a72e-da79768944bc" />
</p>
<p>

C. Verify PHP is recognized by IIS: Reload IIS (Open IIS, Stop and Start the server) … click on osticket-vm (osticket) , right click stop , right click start
 <p>
<img width="876" height="448" alt="reload server" src="https://github.com/user-attachments/assets/b5e71418-3fd9-46c6-a1e1-ea8c8446bbdf" />
</p>
<p>

Step 8: From the “osTicket-Installation-Files” folder, install mysql-5.5.62-win32.msi
  
During installation:

- Select Typical Setup
- Launch Configuration Wizard (after install) 
- Choose standard configuration
- Create a root username and a root password  

Verify MySQL service is running after installation.

<p>
<img width="872" height="599" alt="install mysql " src="https://github.com/user-attachments/assets/82768547-e349-4132-bc5d-a0a58ac6ac8c" />
</p>
<p>
</p>
<br />

Step 9: Install osTicket v1.15.8
  
A. From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” to the same folder  

B. Copy the upload folder contents to:

C:\inetpub\wwwroot\osTicket

C. Rename:
upload → osTicket

<p>
<img width="899" height="695" alt="upload to osTicket" src="https://github.com/user-attachments/assets/90232a39-536e-4ecb-9b2f-95fc3b840e88" />
</p>
<p>

D. Restart IIS.

<p>
<img width="876" height="448" alt="reload server" src="https://github.com/user-attachments/assets/b5e71418-3fd9-46c6-a1e1-ea8c8446bbdf" />
</p>
<p>

E. Go to sites -> Default -> osTicket
On the far right, click “Browse *:80”

<p>
<img width="950" height="761" alt="loading osTicket" src="https://github.com/user-attachments/assets/67ba264d-f527-4d3b-a94f-7740a29f5903" />
</p>
<p>

Note that some extensions are not enabled

F. Go back to IIS, sites -> Default -> osTicket -> Double-click PHP Manager -> Click “Enable or disable an extension”

Enable: php_imap.dll -> Enable: php_intl.dll -> Enable: php_opcache.dll

G. Refresh the osTicket site in your browser, observe the changes

<p>
<img width="950" height="764" alt="osTicket enabled" src="https://github.com/user-attachments/assets/339f83b0-9034-4345-a29d-15a7556e2bfd" />
</p>
<p>
  
</p>
<br />

Step 10: Rename: ost-config.php

A. From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

B. Assign Permissions: ost-config.php (right click -> properties -> security -> advanced )

Disable inheritance -> Remove All

Add New Permissions -> select principal -> type Everyone -> check names -> All (full control etc) apply - ok

<p>
<img width="1421" height="736" alt="assign permissions" src="https://github.com/user-attachments/assets/3b413eb2-4f4a-46b4-b6f2-03e47038a776" />
</p>
<p>

Now OSticket has full control of the configuration file

C. Continue Setting up osTicket in the browser (click Continue)

Name Helpdesk

Default email (your email)

Admin user: email address different from default

<p>
<img width="803" height="933" alt="osticket continue set up" src="https://github.com/user-attachments/assets/f21f5c4d-1e60-47e3-9ade-4dcb4d05a632" />
</p>
<p>
</p>
<br />

Step 11: From the “osTicket-Installation-Files” folder, install HeidiSQL. (to make a connection to our database)

A. Install HeidiSQL and launch 

<p>
<img width="693" height="543" alt="heidi installed" src="https://github.com/user-attachments/assets/8a82ab0d-40da-4d67-90d3-fe910335ef48" />
</p>
<p>

B. Connect to MySQL using:

- Create a new session, root/ROOT
- Connect to the session
  
<p>
<img width="791" height="602" alt="root ROOT" src="https://github.com/user-attachments/assets/f091fec1-5e10-4247-8521-dd6cc914964e" />
</p>
<p>

C. Create a database called “osTicket” (right click unamed -> create new -> database-> osTicket) you’ll see that it was created but thre is nothing in it

<p>
<img width="936" height="593" alt="osTicket database" src="https://github.com/user-attachments/assets/82c027e3-cc4f-45cb-b605-cada9e4e2266" />
</p>
<p>

D. Verify successful database connection / finish setting up OS Ticket page 

<p>
<img width="648" height="460" alt="osTicket finish set up" src="https://github.com/user-attachments/assets/e599a27f-a1be-4018-8f62-60150127d484" />
</p>
<p>

<p>
<img width="806" height="646" alt="osTicket completed" src="https://github.com/user-attachments/assets/594e7c1a-085e-40e8-82c7-5b502f8f56d3" />
</p>
<p>

</p>
<br />

<h2>Skills Demonstrated</h2>

- Cloud Computing (Microsoft Azure)
- Virtual Machine Deployment
- Remote Desktop Administration
- Windows Server Concepts
- IIS Web Server Configuration
- PHP Configuration
- MySQL Database Management
- Application Installation and Troubleshooting
- User Permission Management
- Help Desk Ticketing Systems




- <p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>
This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Post-Install Configuration Objectives</h2>

- Configure Roles and Permissions
- Configure Departments and Teams
- Configure Agents and Users
- Configure SLA Plans and Help Topics
- Configure Ticket Visibility and Access Controls

<h2>Configuration Steps</h2>

<p>
Step 1: Acknowledge Agent Panel Vs Admin Pnael
</p>

A. Log in as Admin/Analyst http://localhost/osTicket/scp/login.php 

B. Agent Panel
<p>
<img width="926" height="388" alt="2 - Agent Panel" src="https://github.com/user-attachments/assets/26aa2891-603b-4aa8-a0c4-0d371ed24f61" />
</p>

C. Admin Panel
<p>
<img width="914" height="366" alt="1 - admin panel " src="https://github.com/user-attachments/assets/fa40d2bc-d991-4da4-929d-a9bd9ff272c3" />
</p>
<br />

<p>
Step 2 Configure Roles (for grouping permissions)
  
- Go to Admin Panel -> Agents -> Roles -> add new role -> Supreme Admin (check everything in permissions: tickets , tasks and knowledgeable)
</p>

<p>
<img width="910" height="399" alt="3 - supreme admin" src="https://github.com/user-attachments/assets/ac64ca5f-70ef-4851-9ce3-778c0360968b" />
</p>
<br />

<p>
Step 3: Configure Departments (Ticket Visibility, Help Desk vs SysAdmins, vs Networking)
  
- Go to Admin Panel -> Agents -> Departments -> new department -> parent = top level department-> name = sysadmins 
</p>

<p>
<img width="925" height="360" alt="4 - sysadmins dept" src="https://github.com/user-attachments/assets/612decb3-21a6-45f3-868b-6ad178e0af6f" />
</p>
<br />

<p>
Step 4: Configure Teams
  
- Go to Admin Panel -> Agents -> Teams (Pull Agents from different Departments) -> add new team -> name = online banking  
</p>

<p>
<img width="918" height="312" alt="5 - online banking team" src="https://github.com/user-attachments/assets/4f474de5-90e8-4792-bc67-76c3bd0b3a00" />
</p>
<br />

<p>
Step 5: Allow anyone to create tickets
  
- Go to Admin Panel -> Settings -> User Settings -> UNCHECK Registration Required: Require registration and login to create tickets (unregistered users can create tickets)
</p>

<p>
<img width="881" height="620" alt="6 - allow everyone to create tickets" src="https://github.com/user-attachments/assets/fbd036e9-c0dd-4bcf-9067-7990517e1002" />
</p>
<br />

<p>
Step 6: Configure Agents (workers/help desk tech)
  
- Go to Admin Panel -> Agents -> Add New
- Jane doe, fake email (Dept: SysAdmins - supreme admin - online banking- set password (uncheck sent to agent and password required next login))
- John doe, fake email (Dept: Support -  view only? - online banking- set password (uncheck sent to agent and password required next login)
</p>

<p>
<img width="913" height="384" alt="7 - agents" src="https://github.com/user-attachments/assets/ca46fd13-584f-4eb0-802a-f0c0daeaf6f7" />
</p>
<br />

<p>
Step 7: Configure Users (customers)
  
- Go to Agent Panel -> Users -> Add New
- Karen (fake email address)
</p>

<p>
<img width="920" height="371" alt="8 - user karen" src="https://github.com/user-attachments/assets/1e7bc656-721a-4316-8291-1486ba79bb36" />
</p>
<br />

<p>
Step 8: Configure SLA (how much time you have to handle a ticket and how to prioritize them)
  
- Go to Admin Panel -> Manage -> SLA -> Add new
- Sev-A (Grace Period: 1 hour, Schedule: 24/7)
- Sev-B (Grace Period: 4 hours, Schedule: 24/7)
- Sev-C (Grace Period: 8 hours, Business Hours)
</p>

<p>
<img width="914" height="439" alt="9 - SLA" src="https://github.com/user-attachments/assets/578e7eb1-9a42-46d6-b572-643fa11889d3" />
</p>
<br />

<p>
Step 9: Configure Help Topics (For when users create a ticket)
  
- Go to Admin Panel -> Manage -> Help Topics
- Business Critical Outage / report a problem
- Personal Computer Issues / report a problem
- Equipment Request / General Inquiry 
- Password Reset / Report a problem
- Other / General Inquiry
</p>

<p>
<img width="916" height="679" alt="10 - help topics" src="https://github.com/user-attachments/assets/9e6adfe6-cf1b-4abb-a07d-7289874961ce" />
</p>
<br />

<h2>Final Result</h2>

<p>
Successfully configured roles, departments, teams, agents, users, SLA plans, and help topics within osTicket. The ticketing system is now fully prepared to receive, route, prioritize, and manage support requests in a simulated IT help desk environment.
</p>




<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Ticket Lifecycle: Intake Through Resolution</h1>
This tutorial outlines the lifecycle of a ticket from intake to resolution within the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Ticket Lifecycle Stages</h2>

- Intake
- Assignment and Communication
- Working the Issue
- Resolution

<h2>Lifecycle Stages</h2>

<p>
Step 1: Delete the maintenance department 
  
  - When you create tickets they gets automatically assigned to this department that gets installed alongside osTicket, but we've actually already created our own department 
  - Log in as admin: http://localhost/osTicket/scp/login.php 
  - Go to agents -> departments ->check maintenance and delete it
</p>
<p>
<img width="915" height="393" alt="1 - delete maintenance dept" src="https://github.com/user-attachments/assets/5b664f93-efeb-448b-97aa-66f5a0af6d95" />
</p>
<br />

<p>
Step 2: Using end user osTicket create new ticket

  - create ticket as end user (karen): http://localhost/osTicket  
</p>
<p>
<img width="802" height="721" alt="2 - karen ticket" src="https://github.com/user-attachments/assets/78cb7389-807c-4432-8e5a-1f93aab2fbcd" />
</p>
<br />

<p>
Step 3: As a Help Desk Agent (john), observe the ticket’s properties

  - Log in as Agent John: http://localhost/osTicket/scp/login.php
  - Observe that we can only view the ticket and leave an internal note
</p>
<p>
<img width="781" height="777" alt="3 - john view only" src="https://github.com/user-attachments/assets/46b011c8-9cbf-44b1-98b0-9599387d8aea" />
</p>
<br />

<p>
Step 4: change Agent John's access level

  - log in as admin: http://localhost/osTicket/scp/login.php
  - Go to admin panel -> agents -> John Doe -> access -> all access
</p>
<p>
<img width="815" height="581" alt="4 - john all access" src="https://github.com/user-attachments/assets/186cbc68-25ef-4f50-a65c-2cf29e56bcef" />
</p>
<br />

<p>
Step 5: As a Help Desk Agent (john), triage the ticket

- Based on communications with end user (karen)
- Priority: emergency
- Department: Support
- SLA: Sev - A 
- Help topic: business critical outage
  
  <p>
<img width="901" height="851" alt="5 - triaging ticket" src="https://github.com/user-attachments/assets/87aef362-f3bf-4d6b-bc14-846e4bbe0be0" />
</p>

- change Assigned To: jane doe
- change Department: sysadmins
- Post reply: Escalating to sysadmins department after triaging ticket
- Notice John no longer has access to ticket once transfered to sysadmins
</p>

<p>
<img width="912" height="391" alt="6 - john no longer access" src="https://github.com/user-attachments/assets/e581e66f-d7bb-467e-b480-9203c12655e0" />
</p>
<br />

<p>
Step 6: working the ticket to completion as Agent Jane (Admin panel)
  
- Log in as Jane and open ticket
- Post reply: We accidentally restarted the online banking system backend server during business hours due to a configuration issue. Will check the settings and attempt to restart.
- WOrk on solution
- Post reply: server successfully restarted, online banking seems to be back up! Confirmed with Karen, closing ticket
 </p> 
  <p>
<img width="901" height="793" alt="7 - ticket solved" src="https://github.com/user-attachments/assets/ab53cca5-332d-46db-b5df-007209891929" />
</p>
</p>
- Inform colleagues on Teams , slack etc
- Update Status from open to resolved (if pending user's satisfaction) or closed if user's feedback was satisfactory  
</p>
 <p>
<img width="903" height="312" alt="8 - ticket resolved" src="https://github.com/user-attachments/assets/abe7ca6a-ce64-4ae6-a5e1-be6476c63dbd" />
</p>
<br />

<h2>Skills Demonstrated</h2>

<ul>
  <li>Created and managed support tickets through the complete ticket lifecycle.</li>
  <li>Performed ticket triage by evaluating business impact, assigning priorities, and applying appropriate SLA plans.</li>
  <li>Configured agent permissions and access levels to support role-based ticket management.</li>
  <li>Assigned and escalated tickets between departments based on issue severity and ownership.</li>
  <li>Utilized internal notes and ticket replies to document troubleshooting activities and communicate with stakeholders.</li>
  <li>Managed ticket ownership and observed how department transfers affect agent visibility and access.</li>
  <li>Applied incident management concepts including severity classification, escalation procedures, and resolution workflows.</li>
  <li>Documented troubleshooting steps and communicated service restoration updates to end users.</li>
  <li>Resolved incidents and properly closed tickets following confirmation of issue resolution.</li>
  <li>Gained hands-on experience using osTicket as both an end user and a help desk technician.</li>
</ul>

<h2>Final Result</h2>

<p>
Successfully simulated a real-world help desk incident from ticket creation through final resolution. The exercise demonstrated how IT support teams intake requests, triage issues, escalate incidents, communicate with stakeholders, troubleshoot technical problems, and document resolutions while adhering to service level agreements (SLAs) and organizational workflows.
</p>
