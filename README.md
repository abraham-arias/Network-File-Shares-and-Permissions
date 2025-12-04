<p align="center">
  <img src="https://i.imgur.com/AeiqMDZ.png" alt="Network File Shares"/>
</p>

# Network File Shares & Permissions  
This lab demonstrates how to configure shared folders, NTFS permissions, and security groups within an Active Directory environment.  
These concepts are essential for IT Support, Desktop Support, and System Administrator roles, as file access management is a core daily responsibility in most organizations.

---

# 🧰 Environments & Technologies Used
- Microsoft Azure (Domain Controller VM + Client VM)
- Remote Desktop Protocol (RDP)
- Active Directory Users and Computers (ADUC)
- Windows File Sharing / NTFS Permissions

---

# 💻 Operating Systems Used
- **Windows Server (DC-1)**  
- **Windows 10 (Client-1)**

---

# 🧪 Lab Overview
In this project, you will:

- Create shared network folders  
- Configure NTFS permissions  
- Configure share permissions  
- Test access from a client machine  
- Create an AD security group  
- Restrict folder access based on group membership  

This lab mirrors real enterprise file-server workflows.

---

# 🛠️ Step-by-Step Instructions

---

## 🔹 Step 1 — Create Shared Folders on DC-1  
On the Domain Controller (DC-1), create four folders on the C:\ drive:

- `read-access`  
- `read-write-access`  
- `no-access`  
- `accounting`  

These folders will be used to demonstrate different permission models.

<br/>

<img src="https://i.imgur.com/k70dozS.png" width="80%" alt="Folder creation"/>

---

## 🔹 Step 2 — Configure Share Permissions & NTFS Permissions  
Right-click each folder → **Properties → Sharing → Advanced Sharing**  

Set permissions as follows:

### **read-access**
- Domain Users → **Read Only**

### **read-write-access**
- Domain Users → **Read/Write**

### **no-access**
- Only Domain Admins → **Full Control**  
- No access for normal users

This demonstrates the difference between **share permissions** and **NTFS permissions**, both of which must be configured correctly to secure a file share.

<br/>

<img src="https://i.imgur.com/wcpB5Ex.png" width="80%" alt="Share permissions"/>
<img src="https://i.imgur.com/hku11Pt.png" width="80%" alt="NTFS permissions"/>

---

## 🔹 Step 3 — Test Permissions From Client-1  
Log into **Client-1** using a normal domain user account.

Attempt to access each of the shared folders:

- `read-access` → Should open and allow viewing only  
- `read-write-access` → User should be able to open, edit, and save files  
- `no-access` → Access should be denied  

This confirms that the permissions applied on DC-1 are working as expected.

<br/>

<img src="https://i.imgur.com/CGQ8yaO.png" width="80%" alt="Testing permissions"/>
<img src="https://i.imgur.com/f9TldBO.png" width="80%" alt="User denied"/>

---

## 🔹 Step 4 — Create a Security Group for Restricted Access  
Back on **DC-1**:

1. Open **Active Directory Users and Computers**  
2. Create a new security group:  
3. This group will control access to the `accounting` shared folder.

Assign permissions to the `accounting` folder:

- Only members of the **Accountants** group → **Full Control / Read**  
- Normal users → **No access**

To give a user access, simply add them to the **Accountants** group.

<br/>

<img src="https://i.imgur.com/QADy92Z.png" width="80%" alt="Create security group"/>
<img src="https://i.imgur.com/BUm3L2Q.png" width="80%" alt="Assign permissions"/>
<img src="https://i.imgur.com/fH8fU7b.png" width="80%" alt="Access restricted"/>

---

# 🎯 Skills Demonstrated

### 🔐 Permission Management
- Configuring NTFS permissions  
- Configuring share permissions  
- Understanding effective permissions  
- Enforcing least-privilege access  

### 🧩 Active Directory Administration  
- Creating and managing security groups  
- Assigning users to groups  
- Role-based access control  

### 💻 Windows System Administration  
- Managing shared folders  
- Testing access using domain users  
- Understanding security inheritance  

### 🧠 Real-World IT Concepts Covered
- Principle of least privilege  
- Separate control of share vs. NTFS permissions  
- Group-based access control (GBAC)  
- Preventing unauthorized access to sensitive data  

---

# 🏁 Summary  
This lab demonstrates the fundamentals of enterprise file sharing and access control — a critical responsibility in IT support and system administration roles.

By configuring NTFS/share permissions and security group–based access, you show:

- Strong understanding of Windows administration  
- Ability to secure data through correct permission design  
- Knowledge of AD user/group management  
- Practical troubleshooting and verification skills  

These concepts form the backbone of file server administration in nearly every company.

