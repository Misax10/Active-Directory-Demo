# Azure Active Directory Lab on Windows Server 2022

This project documents the setup of a Windows Server 2022 virtual machine on Microsoft Azure for practicing Active Directory (AD) configuration. It is intended as a portfolio project to demonstrate cloud infrastructure and identity management skills.

## 🚀 Project Purpose

- Learn how to deploy and configure a Windows Server VM on Azure
- Practice installing and managing Active Directory Domain Services (AD DS)
- Showcase cloud and identity skills on a GitHub portfolio

---

## 🛠️ Azure VM Configuration

| Setting                     | Value                                      |
|----------------------------|--------------------------------------------|
| **VM Name**                | AD-DC-VM                                   |
| **Region**                 | West US 2                                  |
| **Availability Zone**      | Zone 2                                     |
| **Image**                  | Windows Server 2022 Datacenter - Gen2      |
| **VM Size**                | Standard D2s v3 (2 vCPUs, 8 GiB RAM)       |
| **OS Disk Type**           | Premium SSD LRS                            |
| **Security Type**          | Trusted Launch (Secure Boot + vTPM)        |
| **Public Inbound Ports**   | RDP (3389)                                 |
| **Accelerated Networking** | Enabled                                    |
| **Resource Group**         | AD-Lab-RG                                  |
| **Virtual Network**        | AD-DC-VM-vnet                              |
| **Subnet**                 | default (10.0.0.0/24)                       |
| **Public IP**              | AD-DC-VM-ip                                |
| **NSG**                    | Basic (RDP open to internet for testing)   |

---

## 🔐 Security Notes

- RDP (port 3389) is open to the internet **only for testing**.
- After deployment, restrict RDP access to your IP:
  1. Go to **Network Security Groups** in Azure.
  2. Add an inbound rule:
     - Source: IP Addresses
     - Source IP: `your-public-ip`
     - Destination Port: 3389
     - Action: Allow
  3. Remove the default "Allow RDP from Any" rule.

---

## 🧩 Active Directory Setup (Post-Deployment)

### 📸 Screenshots
![Deployment Success](images/deployment_success.png)
![Server Manager with AD DS and DNS](images/server_manager_ad_ds_dns.png)

1. **Connect via RDP** to the VM.
2. Open **Server Manager** > Add Roles and Features.
3. Install **Active Directory Domain Services (AD DS)**.
4. Promote the server to a **Domain Controller**:
   - Add a new forest: `adlab.local`
   - Set DSRM password
5. Reboot and log in with domain credentials.
6. Open **Active Directory Users and Computers** to verify.

---

### 🧪 Sample Organizational Units and Users
![Active Directory Users and Computers](images/ad_users_and_computer.png)
After verifying the domain setup, the following Organizational Units (OUs) and sample users were created for demonstration purposes:

**Organizational Units (OUs):**
- IT
- HR
- Finance
- TestLab

**Sample Users:**
- `Alice Nguyen` in OU: IT
- `Bob Tran` in OU: HR
- `Charlie Le` in OU: Finance
- `Test User` in OU: TestLab

These users were created using the 'Active Directory Users and Computers' tool by right-clicking the respective OU and selecting **New > User**.

---
## 📁 GitHub Documentation

This repository includes:
- Step-by-step setup instructions
- Screenshots of the Azure portal and AD configuration
- Notes on security, troubleshooting, and lessons learned

---

## ✅ Status:
- ✅ VM successfully deployed and validated
- ✅ Active Directory installed and domain controller promotion complete
- ✅ Logged into the domain and verified AD DS and DNS roles
- ✅ RDP access secured post-deployment
- ✅ Project documented on GitHub
---

## 👤 Author

**Khoa Diep**  
Azure Enthusiast | Windows Server | Active Directory | Cloud Projects

