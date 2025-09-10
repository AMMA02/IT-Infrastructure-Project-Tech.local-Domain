# 🖥️ IT Infrastructure Project – Tech.local Domain

<img width="1024" height="1024" alt="Copilot_20250911_020411" src="https://github.com/user-attachments/assets/ab1f5f88-d209-4107-b330-c8c67163ede7" />

## 1. Project Overview

- **Domain Name**: `Tech.local`

- **Servers**:
  - **PDC** (Primary Domain Controller) → Windows Server 2016 Datacenter (Desktop Experience)
  - **ADC** (Additional Domain Controller) → Windows Server 2016 Datacenter (Core Edition – Command Line)

- **Client Computers**: 5 Desktops running Windows 10 Pro
  - Director_PC
  - DeputyDirector_PC
  - Archive_PC
  - Inventory_PC
  - Maintenance_PC

- **Password Policy**:
  - Default password for all users & administrators: **P@ssw0rd**

---

## 2. Primary Domain Controller (PDC)

### Roles & Features
1. **Active Directory Domain Services (AD DS)**
   - Domain: `Tech.local`
   - IP + DNS: `192.168.1.10`
   - AD Recycle Bin enabled

2. **DHCP Server**
   - Scope: `192.168.1.200 – 192.168.1.240`      
   - Exclusion: `192.168.1.241 – 192.168.1.254`
   - Lease Duration: `10 Days`

3. **File Server**
   - Quotas applied
   - Shadow copies enabled

4. **Backup Server**
   - Backup state configuration
     
<img width="1838" height="942" alt="PDC" src="https://github.com/user-attachments/assets/4f02436b-9287-4c63-912f-ad28690d16c3" />

---

### Scripts & Automation
- Script to **create bulk OUs**
- Script to **create bulk users**
- Script to **join machines to the domain**
- Script to **add local user** (`IT-Support`) with password on all machines via GPO (emergency access)
- Script to **map network drives** via GPO


---

### Group Policy (GPO) Configurations
1. **Security & Restrictions**
   - `Ctrl + Alt + Del` → Disable Task Manager & Change Password option
   - Prevent access to Control Panel
   - Deny access to all removable storage

2. **Desktop Environment**
   - Common wallpaper for all users
   - Shortcut for shared drive on Desktop
   - Shortcut for company website on Desktop
   - Map shared drive automatically
     
<img width="1838" height="942" alt="GP" src="https://github.com/user-attachments/assets/be27adee-c581-4ace-9edf-2b8ef07b4789" />
---

## 3. Additional Domain Controller (ADC)
- **OS**: Windows Server 2016 Datacenter (Core Edition – Command Line)
- **Role**: Backup domain controller for `Tech.local` domain

---

## 4. Users & Accounts

| Username   | Role            | Department  |
| ---------- | --------------- | ----------- |
| Sameh      | Director        | Management  |
| Araby      | Deputy Director | Management  |
| AbdelZaher | Deputy Director | Management  |
| Hamdan     | Deputy Director | Management  |
| Ehab       | Storekeeper     | Inventory   |
| Diaa       | Storekeeper     | Inventory   |
| Ebrahim    | Storekeeper     | Inventory   |
| Fawiz      | Archive Staff   | Archive     |
| Hatem      | Archive Staff   | Archive     |
| Ali        | Maintenance     | Maintenance |
| Abdallah   | Maintenance     | Maintenance |

---

## 5. Client Computers
- **Windows 10 Pro** machines joined to `Tech.local` domain
- Each mapped and restricted by GPO
