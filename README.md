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


**Step 1: Create an Azure Virtual Machine**
  
A. Create a Windows 10 Virtual Machine in Microsoft Azure.

- Resource Group: osTicket
- Virtual Machine Name: osticket-vm
- Operating System: Windows 10 Pro
- Size: Standard D2s v3 2vcpus
- Username and Password created during deployment

![Create a Windows 10 Virtual Machine in Microsoft Azure](screenshots/Create-a-Windows-10-Virtual-Machine-in-Microsoft-Azure.png)
<p>

B. After deployment, connect to the VM using Remote Desktop Protocol (RDP).


![RDP to virtual machine](screenshots/RDP-to-virtual-machine.png)
</p>

<br />


**Step 2: Install IIS**

Open Control Panel → Programs → Turn Windows Features On or Off.

Enable:

- Internet Information Services (IIS)
- World Wide Web Services
- Application Development Features
  - CGI

Click OK and allow Windows to install the required features.


![Install Internet Information Services](screenshots/Install-IIS.png)
</p>

<br />


**Step 3: Download osTicket Installation Package**

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
  

![Download osTicket Installation File](screenshots/download-osTicket-installation-file.png)
</p>

<br />


**Step 4: Install PHP Manager and URL Rewrite**

A. PHP Manager for IIS

![PHP Manager Installed](screenshots/php-manager-installed.png)
</p>


B. URL Rewrite Module

![Rewrite Installed](screenshots/rewrite-installed.png)
</p>


These components allow IIS to properly run PHP applications such as osTicket.
</p>
<br />

**Step 5 - Extract php binaries**

A. Create the directory C:\PHP

Go to file explorer -> c: drive -> create folder PHP 

B. From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

![Extract PHP Binaries](screenshots/extract-php-binaries.png)
</p>

<br />

**Step 6: From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.**


![Visual C Installed](screenshots/visual-c-installed.png)
</p>


This provides required runtime libraries for PHP and other dependencies.
</p>
<br />

**Step 7: Install PHP**

A. Open IIS Manager (open IIS as an Admin)

![PHP Manager Admin](screenshots/php-manager-admin.png)
</p>

B. Using PHP Manager:

- Register PHP (we're making the server aware of the existence of PHP the computer and tell it where it is ):
  double click php manager -> register new php -> click three dots -> find php-cgi in C:PHP
  
![PHP CGI](screenshots/php-cgi.png)
</p>

C. Verify PHP is recognized by IIS: Reload IIS (Open IIS, Stop and Start the server) … click on osticket-vm (osticket) , right click stop , right click start

![Reload Server](screenshots/reload-server.png)
</p>

**Step 8: From the “osTicket-Installation-Files” folder, install mysql-5.5.62-win32.msi**
  
During installation:

- Select Typical Setup
- Launch Configuration Wizard (after install) 
- Choose standard configuration
- Create a root username and a root password  

Verify MySQL service is running after installation.

![Install MySQL](screenshots/install-mysql.png)
</p>

<br />

**Step 9: Install osTicket v1.15.8**
  
A. From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” to the same folder  

B. Copy the upload folder contents to:

C:\inetpub\wwwroot\osTicket

C. Rename:
upload → osTicket


![Upload To osTicket](screenshots/upload-to-osTicket.png)
</p>


D. Restart IIS.

![Reload Server](screenshots/reload-server.png)
</p>


E. Go to sites -> Default -> osTicket
On the far right, click “Browse *:80”


![Loading osTicket](screenshots/loading-osTicket.png)
</p>

Note that some extensions are not enabled

F. Go back to IIS, sites -> Default -> osTicket -> Double-click PHP Manager -> Click “Enable or disable an extension”

Enable: php_imap.dll -> Enable: php_intl.dll -> Enable: php_opcache.dll

G. Refresh the osTicket site in your browser, observe the changes


![osTicket Enabled](screenshots/osTicket-enabled.png)
</p>


**Step 10: Rename: ost-config.php**

A. From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

B. Assign Permissions: ost-config.php (right click -> properties -> security -> advanced )

Disable inheritance -> Remove All

Add New Permissions -> select principal -> type Everyone -> check names -> All (full control etc) apply - ok


![Assign Permissions](screenshots/assign-permissions.png)
</p>


Now OSticket has full control of the configuration file

C. Continue Setting up osTicket in the browser (click Continue)

Name Helpdesk

Default email (your email)

Admin user: email address different from default


![Continue Set Up osTicket](screenshots/osticket-continue-set-up.png)
</p>


**Step 11: From the “osTicket-Installation-Files” folder, install HeidiSQL. (to make a connection to our database)**

A. Install HeidiSQL and launch 


![Heidi Installed](screenshots/heidi-installed.png)
</p>


B. Connect to MySQL using:

- Create a new session, root/ROOT
- Connect to the session
  

![root ROOT](screenshots/root-ROOT.png)
</p>


C. Create a database called “osTicket” (right click unamed -> create new -> database-> osTicket) you’ll see that it was created but thre is nothing in it


![osTicket Database](screenshots/osTicket-database.png)
</p>


D. Verify successful database connection / finish setting up OS Ticket page 


![Finish osTicket set up](screenshots/osTicket-finish-set-up.png)
</p>



![osTicket Completed](screenshots/osTicket-completed.png)
</p>


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


**Step 1: Acknowledge Agent Panel Vs Admin Pnael**
</p>

A. Log in as Admin/Analyst http://localhost/osTicket/scp/login.php 

B. Agent Panel

![Agent Panel](screenshots/2-Agent-Panel.png)
</p>

C. Admin Panel

![Admin Panel](screenshots/1-admin-panel.png)
</p>


**Step 2 Configure Roles** (for grouping permissions)
  
- Go to Admin Panel -> Agents -> Roles -> add new role -> Supreme Admin (check everything in permissions: tickets , tasks and knowledgeable)
</p>


![Supreme Admin](screenshots/3-supreme-admin.png)
</p>



**Step 3: Configure Departments** (Ticket Visibility, Help Desk vs SysAdmins, vs Networking)
  
- Go to Admin Panel -> Agents -> Departments -> new department -> parent = top level department-> name = sysadmins 
</p>


![Sys Admin Dept](screenshots/4-sysadmins-dept.png)
</p>



**Step 4: Configure Teams**
  
- Go to Admin Panel -> Agents -> Teams (Pull Agents from different Departments) -> add new team -> name = online banking  
</p>


![Online Banking Team](screenshots/5-online-banking-team.png)
</p>



**Step 5: Allow anyone to create tickets**
  
- Go to Admin Panel -> Settings -> User Settings -> UNCHECK Registration Required: Require registration and login to create tickets (unregistered users can create tickets)
</p>


![Allow Everyone To Create Tickets](screenshots/6-allow-everyone-to-create-tickets.png)
</p>



**Step 6: Configure Agents** (workers/help desk tech)
  
- Go to Admin Panel -> Agents -> Add New
- Jane doe, fake email (Dept: SysAdmins - supreme admin - online banking- set password (uncheck sent to agent and password required next login))
- John doe, fake email (Dept: Support -  view only? - online banking- set password (uncheck sent to agent and password required next login)
</p>


![Agents](screenshots/7-agents.png)
</p>



**Step 7: Configure Users** (customers)
  
- Go to Agent Panel -> Users -> Add New
- Karen (fake email address)
</p>


![User Karen](screenshots/8-user-karen.png)
</p>



**Step 8: Configure SLA** (how much time you have to handle a ticket and how to prioritize them)
  
- Go to Admin Panel -> Manage -> SLA -> Add new
- Sev-A (Grace Period: 1 hour, Schedule: 24/7)
- Sev-B (Grace Period: 4 hours, Schedule: 24/7)
- Sev-C (Grace Period: 8 hours, Business Hours)
</p>


![Service Level Agreement](screenshots/9-SLA.png)
</p>



**Step 9: Configure Help Topics** (For when users create a ticket)
  
- Go to Admin Panel -> Manage -> Help Topics
- Business Critical Outage / report a problem
- Personal Computer Issues / report a problem
- Equipment Request / General Inquiry 
- Password Reset / Report a problem
- Other / General Inquiry
</p>


![Help Topics](screenshots/10-help-topics.png)
</p>


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


**Step 1: Delete the maintenance department**
  
  - When you create tickets they gets automatically assigned to this department that gets installed alongside osTicket, but we've actually already created our own department 
  - Log in as admin: http://localhost/osTicket/scp/login.php 
  - Go to agents -> departments ->check maintenance and delete it

![Delete Maintenance Dept](screenshots/1-delete-maintenance-dept.png)
</p>



**Step 2: Using end user osTicket create new ticket**

  - create ticket as end user (karen): http://localhost/osTicket  

![Karen Ticket](screenshots/2-karen-ticket.png)
</p>



**Step 3: As a Help Desk Agent (john), observe the ticket’s properties**

  - Log in as Agent John: http://localhost/osTicket/scp/login.php
  - Observe that we can only view the ticket and leave an internal note

![John View Only](screenshots/3-john-view-only.png)
</p>



**Step 4: change Agent John's access level**

  - log in as admin: http://localhost/osTicket/scp/login.php
  - Go to admin panel -> agents -> John Doe -> access -> all access

![John All Access](screenshots/4-john-all-access.png)
</p>

**Step 5: As a Help Desk Agent (john), triage the ticket**

- Based on communications with end user (karen)
- Priority: emergency
- Department: Support
- SLA: Sev - A 
- Help topic: business critical outage
  


![Triaging Ticket](screenshots/5-triaging-ticket.png)
</p>

- change Assigned To: jane doe
- change Department: sysadmins
- Post reply: Escalating to sysadmins department after triaging ticket
- Notice John no longer has access to ticket once transfered to sysadmins
</p>


![John No Longer Access](screenshots/6-john-no-longer-access.png)
</p>



**Step 6: working the ticket to completion as Agent Jane (Admin panel)**
  
- Log in as Jane and open ticket
- Post reply: We accidentally restarted the online banking system backend server during business hours due to a configuration issue. Will check the settings and attempt to restart.
- WOrk on solution
- Post reply: server successfully restarted, online banking seems to be back up! Confirmed with Karen, closing ticket

![Ticket Solved](screenshots/7-ticket-solved.png)
</p>

- Inform colleagues on Teams , slack etc
- Update Status from open to resolved (if pending user's satisfaction) or closed if user's feedback was satisfactory  


![Ticket Resolved](screenshots/8-ticket-resolved.png)
</p>


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
