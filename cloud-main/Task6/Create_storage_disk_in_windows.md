# Task 7: Creating and Attaching an Additional Data Disk to VM (m1) 💾

**Domain:** Cloud & DevOps Summer Training  
**Objective:** To provision a new Azure Managed Disk, attach it to our existing `m1` Virtual Machine, and initialize/format the disk within the Windows operating system for data storage.

---

## 📝 Overview
Virtual Machines come with a default OS (Operating System) disk, but best practices in DevOps and cloud architecture dictate that application data should be stored on separate "Data Disks." In this task, we dynamically attached a new data disk to `m1` and used Windows Disk Management to make the volume usable. 

## 🛠️ Prerequisites
* The active Windows Virtual Machine (`m1`) created in Task 3.
* RDP access to the VM.

---

## 🚀 Step-by-Step Implementation

### Phase 1: Attaching the Disk via Azure Portal

#### Step 1: Navigating to VM Disks
In the Azure Portal, I went to the overview page for the `m1` Virtual Machine. Under the **Settings** section on the left-hand menu, I clicked on **Disks**.
<img width="1870" height="819" alt="image" src="https://github.com/user-attachments/assets/9ee3d68f-7969-4ead-8299-7bcab9f79c3c" />


#### Step 2: Creating and Attaching the Disk
Under the "Data disks" section, I clicked on **Create and attach a new disk**. I configured the following settings:
* **Disk Name:** Left as default or provided a descriptive name (e.g., `m1-datadisk-01`).
* **Storage Type:** Selected Standard HDD or Standard SSD depending on the requirement.
* **Size (GiB):** Specified the required storage size (e.g., 10 GiB ).
<img width="1003" height="161" alt="image" src="https://github.com/user-attachments/assets/3649dfdf-2f75-4ad9-afff-3192bd4485d3" />


#### Step 3: Saving the Configuration
After entering the disk details, I clicked **Save** at the top of the Disks page to apply the changes. Azure successfully updated the VM and attached the unmanaged raw storage.
<img width="1029" height="168" alt="image" src="https://github.com/user-attachments/assets/ff69c472-6164-4a61-8955-3c3c8b8fb747" />


---

### Phase 2: Initializing the Disk in Windows

#### Step 4: Connecting and Opening Disk Management
I connected to the `m1` VM using RDP. Once logged in, I right-clicked the Windows Start button and selected **Disk Management** (or typed `diskmgmt.msc` in Run).


#### Step 5: Initializing the Disk
Upon opening Disk Management, a prompt automatically appeared asking to initialize the newly detected disk. I selected the disk and chose the partition style (GPT is recommended for newer/larger drives, MBR for older compatibility) and clicked **OK**.

> **[Screenshot 5 Placeholder]** 
> *(Add your screenshot showing the "Initialize Disk" popup box)*
> `![Initialize Disk](link_to_image)`

#### Step 6: Formatting and Assigning a Drive Letter
The disk now appeared as "Unallocated" space. I right-clicked the unallocated space and selected **New Simple Volume**. I followed the wizard to:
1. Specify the volume size (used maximum).
2. Assign a drive letter (e.g., `F:`).
3. Format the volume with the **NTFS** file system and named it (e.g., "DataDrive").

> **[Screenshot 6 Placeholder]** 
> *(Add your screenshot showing the New Simple Volume Wizard or the final formatted drive)*
> `![Format Disk](link_to_image)`

#### Step 7: Verifying the New Drive
Finally, I opened Windows File Explorer and verified that the new drive (e.g., `Local Disk (F:)`) was visible and ready to store files.

> **[Screenshot 7 Placeholder]** 
> *(Add your screenshot showing "This PC" with both the C: drive and your newly created drive side-by-side)*
> `![Verify Drive in File Explorer](link_to_image)`

---

## 🎯 Key Takeaways
* **Decoupled Storage:** Learned that storage disks in the cloud are decoupled from compute (the VM), meaning data disks can be detached and moved to other VMs if needed without losing data.
* **Disk Initialization:** Understood that cloud providers simply attach raw block storage to the machine; it is the OS administrator's job to format and partition it before it can be used.
* **Scalability:** Demonstrated how easily a cloud environment can scale up its storage capacity with zero physical downtime.
