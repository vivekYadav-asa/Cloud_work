# Task 6: Generating a SAS Token for Secure, Restricted Access 🔐

**Domain:** Cloud & DevOps Summer Training  
**Objective:** To generate a Shared Access Signature (SAS) token on an Azure Storage account to grant temporary, IP-restricted access to storage resources without sharing primary account keys.

---

## 📝 Overview
Security is a critical component of Cloud and DevOps. In this task, we implemented the Principle of Least Privilege by creating a Shared Access Signature (SAS). Instead of providing full access to the storage account, we generated a secure URI that restricts access based on permissions, a specific time window, and a designated IP address.

## 🛠️ Prerequisites
* The active Azure Storage Account created in Task 5.
* The specific public IP address that will be granted access.

---

## 🚀 Step-by-Step Implementation

### Step 1: Navigating to Shared Access Signature Settings
In the Azure Portal, I opened my previously created Storage account. From the left-hand security menu under **Security + networking**, I selected **Shared access signature**.
<img width="1289" height="796" alt="image" src="https://github.com/user-attachments/assets/4ffedeb6-152a-449b-a90c-bb6118a918aa" />


### Step 2: Configuring Allowed Services and Permissions
I configured the required parameters for the token:
* **Allowed services:** Selected the relevant services (e.g., Blob for web files).
* **Allowed resource types:** Chose Service, Container, and/or Object depending on the required access level.
* **Allowed permissions:** Selected only what was strictly necessary (e.g., Read, List).


### Step 3: Setting Time and IP Restrictions
This is the core security step. I defined the exact window of access and restricted it to a specific network:
* **Start and expiry date/time:** Set a custom timeframe for when the token is valid.
* **Allowed IP addresses:** Entered the specific target IP address (or CIDR range) that is permitted to use this token. Requests from any other IP will be denied.
<img width="1017" height="598" alt="image" src="https://github.com/user-attachments/assets/3d00a69f-e901-45b4-857e-63b404665e01" />


### Step 4: Generating the SAS Token
After verifying all configurations, I scrolled down and clicked **Generate SAS and connection string**. Azure successfully generated the cryptographic token, providing a SAS token string, a Blob service SAS URL, and a connection string.
<img width="898" height="792" alt="image" src="https://github.com/user-attachments/assets/458ee6e7-34b6-4dc2-857f-6fe910abd541" />



---

## 🎯 Key Takeaways
* **Delegated Access:** Learned how to safely grant third parties or applications access to Azure resources without exposing the primary storage account keys.
* **Time-To-Live (TTL):** Understood the importance of expiring credentials automatically to reduce the attack surface.
* **Network-Level Security:** Demonstrated how IP whitelisting at the token level adds a robust layer of defense against unauthorized access.
