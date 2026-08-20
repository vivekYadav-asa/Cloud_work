# Task 5: Hosting a Static Website on Azure Storage Account 🗄️🌐

**Domain:** Cloud & DevOps Summer Training  
**Objective:** To create an Azure Storage account, enable the static website hosting feature, upload web files, and access the site globally via the generated public endpoint.

---

## 📝 Overview
In this task, we transitioned from IaaS (Virtual Machines) to a more Serverless approach. By utilizing Azure Storage Accounts, we hosted a static website (HTML, CSS, JS) without managing any underlying server infrastructure. This method is highly scalable, secure, and cost-effective for static content.

## 🛠️ Prerequisites
* An active Microsoft Azure account.
* Basic static website files (`index.html`, `style.css`, etc.).

---

## 🚀 Step-by-Step Implementation

### Step 1: Creating a Storage Account
Navigated to the Azure Portal, searched for "Storage accounts," and clicked **Create**. I configured the Resource Group, provided a globally unique Storage account name, and selected the region. 

<img width="844" height="763" alt="image" src="https://github.com/user-attachments/assets/a6f85ba3-c532-46ad-92d9-686e2d84b22a" />
<img width="918" height="736" alt="image" src="https://github.com/user-attachments/assets/ecf03c74-a50e-470e-b001-1c59e14f1604" />
<img width="883" height="715" alt="image" src="https://github.com/user-attachments/assets/e38d8512-d936-4534-8546-5274b747bc01" />

### Step 2: Enabling Static Website Hosting
Once the storage account was deployed, I navigated to the resource. In the left-hand menu under **Data management**, I selected **Static website**. I toggled the setting to **Enabled** and specified `index.html` as the Index document name.
<img width="1279" height="797" alt="image" src="https://github.com/user-attachments/assets/79651a82-5d0b-454c-95c6-561287f964e0" />


### Step 3: Uploading the Website Files
Enabling the feature automatically created a container named `$web`. I navigated to the **Containers** section (or used Azure Storage Explorer), opened `$web`, and uploaded my local static website files directly through the Azure Portal.
<img width="1287" height="538" alt="image" src="https://github.com/user-attachments/assets/1f953cd3-984f-4664-9e12-1576f01340f3" />
<img width="1710" height="870" alt="image" src="https://github.com/user-attachments/assets/80947b09-9060-4c7e-b3c9-1d35187bda19" />

### Step 4: Accessing the Hosted Website
I went back to the **Static website** menu tab, copied the auto-generated **Primary endpoint** URL, and pasted it into a new browser tab. The static website loaded successfully over the internet!
<img width="1307" height="743" alt="image" src="https://github.com/user-attachments/assets/f2a06b62-97c9-4ae5-9496-b153b1029f71" />
<img width="1910" height="959" alt="image" src="https://github.com/user-attachments/assets/23bbf6b5-a92d-4f45-8c12-91af2311cb35" />


---

## 🎯 Key Takeaways
* **Serverless Hosting:** Discovered that static sites do not require a full VM (like we used in Task 4), saving compute resources and reducing maintenance overhead.
* **The `$web` Container:** Learned that Azure automatically designates a special `$web` blob container to serve web assets publicly when static hosting is enabled.
* **Cost-Efficiency:** Understood that storage-based hosting is incredibly cheap compared to running a virtual machine 24/7 for static content.
