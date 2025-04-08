# osTicket - Prerequisites and Installation

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>


This project documents the setup and configuration of the open-source ticketing system **osTicket**, performed as a hands-on home lab to simulate real-world IT Helpdesk environments. The goal of this project was to gain practical experience deploying, configuring, and managing a ticketing system — a core tool in IT operations.

---

### 🌐 Environments and Technologies Used

- **Microsoft Azure** (Virtual Machines/Compute)
- **Remote Desktop Protocol (RDP)**
- **Internet Information Services (IIS)**
- **osTicket v1.15.8**
- **MySQL 5.5.62**
- **PHP 7.3.8**

### 🖥️ Operating Systems Used

- **Windows 10 (21H2)**

---

## ✅ List of Prerequisites

Before osTicket installation, the following items were prepared:

- Azure VM provisioned with Windows 10 (4 vCPUs)
- Remote Desktop access configured
- IIS installed with CGI support enabled
- PHP Manager for IIS
- Rewrite Module for IIS
- PHP 7.3.8 extracted to `C:\PHP`
- Visual C++ Redistributable installed
- MySQL Server installed and configured (user: `root`, pass: `root`)
- All necessary installation files pre-downloaded into a single ZIP folder for efficient access

---

## ⚙️ Installation Steps

1. **Provision Azure Virtual Machine**
   - Created a new Windows 10 VM via Azure
   - VM Name: `osticket-vm`
   - Credentials: `labuser / osTicketPassword1!`

2. **Remote Desktop Access**
   - Used RDP to access the virtual machine and perform all configurations remotely.

3. **Prepare Installation Files**
   - Unzipped the `osTicket-Installation-Files.zip` onto the desktop.
   - This centralized all dependencies required for the lab.

4. **Install IIS with CGI**
   - Enabled Internet Information Services with Application Development Features > CGI.

5. **Install Required Modules**
   - Installed:
     - **PHP Manager for IIS**
     - **Rewrite Module for IIS**
     - **VC_redist.x86.exe**
     - **MySQL Server 5.5.62** (configured with root/root credentials)

6. **PHP Setup**
   - Created `C:\PHP` directory
   - Unzipped PHP 7.3.8 into `C:\PHP`
   - Registered PHP with IIS via PHP Manager

7. **Configure osTicket**
   - Unzipped osTicket v1.15.8 and moved the “upload” folder to `C:\inetpub\wwwroot`, renamed it `osTicket`
   - Reloaded IIS and navigated to `http://localhost/osTicket`
   - Enabled required PHP extensions:
     - `php_imap.dll`
     - `php_intl.dll`
     - `php_opcache.dll`

8. **Final Configuration**
   - Renamed `ost-sampleconfig.php` to `ost-config.php`
   - Configured permissions for `ost-config.php`
   - Continued browser-based installation of osTicket
   - Set up database using **HeidiSQL** (created DB: `osTicket`)

9. **Clean Up**
   - Deleted `setup` directory for security
   - Set `ost-config.php` to read-only

---
