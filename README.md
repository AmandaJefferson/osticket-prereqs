# osticket-prereqs

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Resource Group)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (Version 22H2)

<h2>List of Prerequisites</h2>

- Image 1 Azure Portal
- Image 2 Virtual Machine Creation
- Image 3 Remote Desktop Protocol 
- Image 4 Internet Information Services (IIS)

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/fJTX7An.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/nUqOWCH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/guSCyIQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  
- Create an Azure Virtual Machine Windows 10, 2or 4 vCPUs
- Create a username and Password
  
</p>



<p>
<img src="https://i.imgur.com/ZX5Ge18.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
  
- Click Review + Create
  
</p>
<p>
<img src="https://i.imgur.com/OYK0zpU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

In Microsoft Azure, I created a resource group called RG-osTicket and a Virtual Machine both in the West US region where the matadate is stored. The resource group provides a way to organize and manage resources in a cohesive manner and the VIrtural Machine using Windows 10 created to access RDC to install the open-source help desk ticketing system osTicket.

<p>
  
</p>



<br />
<h2>Step 1: RDP</h2>
<p>
<img src="https://i.imgur.com/N5RvV5m.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

The IP Address from the osTicket created in Mircosoft Azure I accessed the Virtual Machine(VM) through Remote Desktop Connection (RDC), also known as Remote Desktop Protocol (RDP), to connect over a network connection.  

<p>
  
- Copy the Public IP Address 
- Open the Remote Desktop
- Paste the public IP address
- Enter your username and Password
  
</p>

<br />


<br />
<h2>Step 2: Enable IIS In Windows with CGI</h2>
<p>
<img src="https://i.imgur.com/VKQHyyh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/cgdonRL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  
</p>
Once you are in, you have to Install and enable Internet Information Services. This is a web server that runs on the windows operating system. 
</p>


- Right click the menu button 
- Click run
- Type Control (for control panel)
- Click Programs
- Click Turn Windows features On or Off
- Select and expand Internet Information Services(IIS)
- Select and expand Worldwide Web
- Select and expand Application Developer 
- Select CGI(what lets us install the PHP manager)
- Click OK




<br />
<h2>Installation Files</h2>
<p>
<img src="https://i.imgur.com/TCQj5zm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/mAakW7n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
From the installation file download the PHP manager for IIS(PHPMangerForLLS_V1.5.0msl). In osTicket PHP is the back end web pragraming language.
After file has downloaded 
  
- Click Open file
- Click Next
- Click I Agree
- Click Next 
- Click Close

  
<p>
<img src="https://i.imgur.com/4I26n8H.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

From the installation file download the rewrite module.  

<p>
<img src="https://i.imgur.com/tdDcb6q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Create the directory C:\PHP. 

- Windows C
- New folder
- Name folder "PHP"

<p>
<img src="https://i.imgur.com/1EcBP5a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


From the Installation file download PHP 7.3.8 and unzip the content into C:\PHP. Extract all>browse>this PC>windows C>PHP>select folder>Extract.
<br />

<p>
<img src="https://i.imgur.com/xuADHtJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
From the installation file download VC redistX86.exe.
  
  
<p>
<img src="https://i.imgur.com/4e70geq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>  
  
  
From the Installation file download MYSQL.5.5.62.
Installing a database on the computer, osTicket to store application data (tickets and users) needs a database to stores and MySQL stores everything.
Open it and agree. 
  
- Select Typical Setup 
- Check the box before Installing
- Launch Configuration Wizard (after install) 
- Select Standard Configuration 
- Enter a password (user name is root)
- Execute
- Finish
 
<p>
<img src="https://i.imgur.com/Exjatt3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>   
  
Open IIS as an administrator  

Internet Information Services (IIS) is a web server software used for hosting websites, web applications, and services on Windows-based servers.  
  
<p>
<img src="https://i.imgur.com/ArrIAdq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>    
  
  
<p>
<img src="https://i.imgur.com/RUGkhgu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>      
  
  
Register PHP from within IIS. 
  
</p>

- Search IIS 
- Click PHP Manager
- Click Register new PHP Version
- Click ---- on the right 
- Click Windows (C): drive
- Select PHP
- Select Php-cgi
- Click OK



<p>
<img src="https://i.imgur.com/7Apg0tC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>  


Download the osTicket from the Installation file folder. 
- Extract and copy “upload” folder to c:\inetpub\wwwroot Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

Open another file explorer next to the first. Go to the download and drag upload folder into c:\inetpub\wwwroot and let it install. Next rename the folder to osTicket.



<p>
<img src="https://i.imgur.com/PQx3sk8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>      

  
 Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
 
<br />
<p>
<img src="https://i.imgur.com/yTkVNZO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/qFlQZrc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Note that some extensions are not enabled




<p>
<img src="https://i.imgur.com/LqKsyCz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”


<p>
<img src="https://i.imgur.com/yTkVNZO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll



<p>
<img src="https://i.imgur.com/2bSi038.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>





Refresh the osTicket site in your browse, observe the changes


<p>
<img src="https://i.imgur.com/3f2UUAC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/3kkGhyB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php


Assign Permissions: 
- Right click ost-config.php
- Click Properties
- Click Security
- Click Advanced
- Click Disable inheritance 
- Click Remove All
- Click Add
- Select a Princple
- Type "Everyone"
- Click Check Names
- Select New Permissions
- Click OK
- Click Apply
- Select Full Control
- Click OK




<p>
<img src="https://i.imgur.com/4bokrp7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/gL9jS3T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Click countinue in the osTicket browser to countinue settings.

Name Helpdesk (Amanda Help Desk)

Default email (receives email from customers)amanda@osTicket.com

Set user name and password. In this case user name is "user-admin".

<p>
<img src=https://i.imgur.com/bhEsuqA.png"" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/RHmZD85.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


<p>
<img src="https://i.imgur.com/dLZqnj8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>



From the Installation Files, download and install HeidiSQL.
Open Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”



<p>
<img src="https://i.imgur.com/Ckm4HPH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”




<p>
<img src="https://i.imgur.com/dYBVIa8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Congratulations, hopefully it is installed with no errors!

- Delete C:\inetpub\wwwroot\osTicket\setup - 
- Set Permissions to "Read" only at c:\inetpub/wwwroot/osTicket/include/lost-config.php
Go to C:\inetpub\wwwroot\osTicket\include\ost-config.php>properties>security>advanced>everyone>EDIT>and unchecked everything and just leave it to read and execute.


<p>
<img src="https://i.imgur.com/2hdSxE4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

Clean up


<p>
<img src="https://i.imgur.com/1nSC1fr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Help Desk login page






















































