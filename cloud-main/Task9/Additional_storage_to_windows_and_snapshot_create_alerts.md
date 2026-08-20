# Task 9: Scaling Storage, Snapshots, and VM Monitoring 📈💾

**Domain:** Cloud & DevOps Summer Training  
**Objective:** To attach a massive 1TB data disk to the `m1` Virtual Machine, create a point-in-time snapshot of the disk for backup purposes, and configure a CPU metric alert to proactively monitor the VM's health.

---

## 📝 Overview
As applications grow, their infrastructure must scale and remain resilient. In this task, we simulated scaling up our storage by provisioning a 1TB (1024 GiB) disk for `m1`. To ensure data safety, we took a **Snapshot** of the disk (a read-only, point-in-time backup). Finally, we configured an **Azure Monitor Alert** to notify us automatically if the VM's CPU usage spikes beyond a critical threshold, enabling proactive incident response.

## 🛠️ Prerequisites
* The active Windows Virtual Machine (`m1`).
* Azure Portal access with permissions to create Disks, Snapshots, and Alert Rules.

---

## 🚀 Step-by-Step Implementation

### Phase 1: Provisioning a 1TB Data Disk

#### Step 1: Attaching the 1TB Disk
Navigated to the `m1` VM in the Azure Portal and selected **Disks** from the left menu. Clicked **Create and attach a new disk**. I named the disk (e.g., `ahsanz-1TB-Data`), selected the storage type, and specifically set the **Size (GiB)** to `1024` (1 TB). Clicked **Save** to apply the configuration.

<img width="1276" height="790" alt="image" src="https://github.com/user-attachments/assets/641c8651-325e-4908-a1b9-771f30573a27" />



#### Step 2: Initializing in Windows
*(Just like in Task 7)* I connected to `m1` via RDP, opened **Disk Management**, initialized the new 1TB disk as GPT, and formatted it as a New Simple Volume (NTFS) so the OS could utilize the massive storage space.

<img width="979" height="727" alt="image" src="https://github.com/user-attachments/assets/28867676-b2ef-488d-b011-4407fa99c97d" />
<img width="1461" height="482" alt="image" src="https://github.com/user-attachments/assets/d4fc26fb-5f9e-40c4-8bcd-18daf0611886" />


---

### Phase 2: Creating a Disk Snapshot

#### Step 3: Navigating to the Disk
Back in the Azure Portal, I went back to the `m1` **Disks** menu and clicked directly on the blue hyperlink name of the newly created 1TB disk to open its dedicated resource page.

#### Step 4: Taking the Snapshot
On the disk's overview page, I clicked **Create snapshot** from the top menu bar. I provided a name (e.g., `m1-1TB-Backup-Snap`), selected **Full** for the snapshot type, and assigned it to my resource group. Clicked **Review + create**, and then **Create**.

<img width="1395" height="814" alt="image" src="https://github.com/user-attachments/assets/77ec3fe7-6eba-45e2-a695-e8aecd61a07a" />
<img width="1013" height="800" alt="image" src="https://github.com/user-attachments/assets/7fb49163-4f63-4992-8f22-4bb6432bbfd3" />

---

### Phase 3: Configuring a CPU Alert

#### Step 5: Creating the Alert Rule
I navigated back to the `m1` VM overview page. Under the **Monitoring** section on the left menu, I selected **Alerts** and clicked **+ Create > Alert rule**.

<img width="1284" height="794" alt="image" src="https://github.com/user-attachments/assets/860b11f1-482d-46e7-8b7a-3e6f80bf3aeb" />
<img width="921" height="790" alt="image" src="https://github.com/user-attachments/assets/0623afcf-17f2-4543-b8b6-5776a2efa1ac" />


#### Step 6: Setting the Condition (CPU Usage)
Under the **Condition** tab, I selected the **Percentage CPU** signal. I configured the alert logic to trigger when the **Average CPU percentage is greater than 80%** over a 5-minute evaluation granularity. 
<img width="943" height="766" alt="image" src="https://github.com/user-attachments/assets/b3785796-4bdf-4eaf-9300-6943525f1804" />



#### Step 7: Configuring the Action Group
Under the **Actions** tab, I created a new **Action Group**. I configured the notification type to **Email/SMS message/Push/Voice** and entered my email address. This ensures I receive an email the moment the CPU spikes. Finally, I named the alert rule and clicked **Review + create**.
<img width="473" height="634" alt="image" src="https://github.com/user-attachments/assets/a0688177-d25a-4862-b20b-a184e70c2808" />




---

## 🎯 Key Takeaways
* **Storage Scalability:** Successfully attached and formatted enterprise-scale (1TB) storage to a running instance without needing to rebuild the VM.
* **Disaster Recovery:** Learned that Snapshots are essential for data backup, allowing us to restore the disk to its exact state in case of data corruption or accidental deletion.
* **Proactive Monitoring:** Understood the importance of Azure Monitor. Setting up CPU alerts transitions DevOps teams from a reactive state (waiting for a crash) to a proactive state (investigating high load before an outage occurs).
