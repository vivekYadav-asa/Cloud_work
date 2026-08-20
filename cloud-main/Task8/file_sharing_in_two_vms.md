# Task 8: Developing a Centralized File Sharing System Between VMs 📁🔗

**Domain:** Cloud & DevOps Summer Training  
**Objective:** To create a centralized file-sharing system between two Virtual Machines (`m1` and `m2`) by utilizing an Azure File Share hosted on our existing `mynewdb` storage account.

---

## 📝 Overview
In a distributed architecture, multiple servers often need access to the same files simultaneously. Instead of copying files back and forth, we leveraged our existing storage account (`mynewdb`) to create an **Azure File Share**. By mounting this share as a network drive on both `m1` and `m2`, any file created or modified on one VM is instantly accessible on the other. 

*(Note: The `mynewdb` account is already hosting our static website via Blob Storage, showcasing how a single Azure Storage account can seamlessly handle multiple distinct storage services simultaneously).*

## 🛠️ Prerequisites
* Existing Virtual Machines: `m1` and `m2`.
* Existing Storage Account: `mynewdb`.
* RDP access to both VMs.

---

## 🚀 Step-by-Step Implementation

### Step 1: Creating a File Share in the Storage Account
Navigated to the Azure Portal and opened the `mynewdb` storage account. From the left-hand menu under **Data storage**, I selected **File shares** and clicked **+ File share**. I named the share (e.g., `shared-files`) and allocated a small quota (e.g., 5 GiB) for the transaction optimized tier, then clicked **Create**.
<img width="1630" height="801" alt="image" src="https://github.com/user-attachments/assets/bb0d585c-e8fa-430c-9ea4-eb4686ae2aaa" />
<img width="938" height="816" alt="image" src="https://github.com/user-attachments/assets/4445259e-8821-45a7-bbde-6c15e010bcaa" />



### Step 2: Generating the Connection Script
I clicked on the newly created `shared-files` file share. At the top of the menu, I clicked **Connect**. A side panel opened where I selected **Windows** and a Drive letter (e.g., `Z:`). Azure automatically generated a PowerShell script containing the storage account key to securely map the drive. I clicked **Show script** and copied it.
<img width="1903" height="812" alt="image" src="https://github.com/user-attachments/assets/f8e7b22a-9eb5-4bc3-9d21-0484187cab31" />
<img width="569" height="775" alt="image" src="https://github.com/user-attachments/assets/fdbd9ee7-b130-4394-a6fe-8bfde1166299" />


### Step 3: Mounting the Network Drive on VM 1 (`m1`)
I connected to the first virtual machine (`m1`) via RDP. I opened **Windows PowerShell** as an Administrator, pasted the copied script, and pressed Enter. The script executed successfully, securely mounting the Azure File Share as the `Z:` drive via the SMB protocol.
<img width="1537" height="757" alt="image" src="https://github.com/user-attachments/assets/748ed30f-099a-4534-ad10-22db1af315e8" />


### Step 4: Mounting the Network Drive on VM 2 (`m2`)
I repeated the exact same process for the second machine. I connected to `m2` via RDP, opened PowerShell, pasted the identical script, and executed it. The `Z:` drive was now successfully mapped on `m2` as well.

<img width="1903" height="789" alt="image" src="https://github.com/user-attachments/assets/47ee91c7-3e11-489f-b7d4-03173dcff5d3" />


### Step 5: Testing File Synchronization
To verify the system worked, I opened the `Z:` drive on `m2` and created a new text document named `sync-test.txt`. I then switched over to my RDP session for `m1`, opened the `Z:` drive, and confirmed that `sync-test.txt` was instantly visible and accessible. 
<img width="857" height="245" alt="image" src="https://github.com/user-attachments/assets/501c5f02-f070-49bd-82a9-bb4b9a3f4c77" />
<img width="1891" height="764" alt="image" src="https://github.com/user-attachments/assets/f247d503-3eda-43ef-a8e8-b947c40248ad" />
`m2- created a file in shared z disk named sync-text.txt`

<img width="1893" height="796" alt="image" src="https://github.com/user-attachments/assets/20242e35-e453-4105-a6f3-608b43ee4045" />
`m1-has now a shared z disk with sync-text.txt file `

---

## 🎯 Key Takeaways
* **Azure Files vs. Blobs:** Understood the difference between Blob storage (used for our static website) and Azure Files (used for SMB network mapping).
* **SMB Protocol:** Learned how Windows machines natively interact with cloud file shares using standard networking protocols.
* **Centralized Data:** Demonstrated a highly available architecture where compute (VMs) can be destroyed or recreated without losing the centralized shared data.
