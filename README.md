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

## 🧪 Lab 2 – osTicket Configuration

This phase focused on configuring the osTicket system to simulate a real-world helpdesk environment.

### ✅ Admin and Agent Access
- Admin Panel: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)
- End User Portal: [http://localhost/osTicket](http://localhost/osTicket)

### 🔧 Configuration Steps

- **Roles**: Created “Supreme Admin” role to define admin-level access.
- **Departments**: Created “SysAdmins” for ticket visibility and routing.
- **Teams**: Set up “Online Banking” team by pulling agents from various departments.
- **User Access Settings**:
  - Enabled registration/login requirement for ticket creation.

- **Agents**: Added Jane (SysAdmins) and John (Support).
- **Users**: Added Karen and Ken as end users.
- **SLA Policies**:
  - **Sev-A** (1 hr, 24/7)
  - **Sev-B** (4 hrs, 24/7)
  - **Sev-C** (8 hrs, Business Hours)
- **Help Topics**:
  - Business Critical Outage
  - Personal Computer Issues
  - Equipment Request
  - Password Reset
  - Other

This gave me exposure to managing roles, access control, and how tickets can be routed based on severity and department.

---

## 🧪 Lab 3 – Ticket Handling Workflow

This final lab simulated day-to-day help desk operations by creating and resolving tickets from both end-user and agent perspectives.

### 🗒️ Ticket 1: Banking System Outage
- **Created by End User**: Reported online banking outage
- **Handled by**: Jane (SysAdmins)
- **SLA**: Sev-A (1 hr)
- **Team**: Online Banking
- Practiced assigning critical tickets and learned how permissions restrict visibility across departments.

### 🗒️ Ticket 2: Adobe Upgrade
- **Created by End User**: Broken Adobe software in Accounting
- **Handled by**: John (Support)
- **SLA**: Sev-B (4 hrs)
- Understood assignment best practices and aligning severity with business needs.

### 🗒️ Ticket 3: CFO Laptop Won’t Boot
- **Created by End User**
- **Handled by**: John (Support)
- **SLA**: Sev-B (4 hrs)
- Developed escalation and visibility awareness by toggling SysAdmins as a top-level department.

### 🔍 Observations
- Learned that restricted departments hide tickets unless access is explicitly granted.
- Solved all tickets by assigning SLAs, departments, and updating statuses accordingly.

---

## 💬 Real-World Insights

- Ticket communication includes email integration — users are notified of updates and can reply directly.
- Tickets can originate via phone calls, email, web forms, or even hallway conversations — creating a ticket for **every** interaction ensures metrics are tracked and issues are documented.
- Practiced documenting, responding, and closing tickets — crucial for real helpdesk environments.

---

## 📚 Technical Skill Development

- Reinforced foundational skills: IIS, PHP, MySQL, Windows Services
- Learned configuration management and access control within a ticketing system
- Understood end-to-end Help Desk ticket flow from user creation to issue resolution
- Repeated the lab multiple times to improve my speed, confidence, and intuition when setting up and using osTicket

---
