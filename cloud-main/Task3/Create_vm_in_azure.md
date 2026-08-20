# Task 3: Provisioning a Virtual Machine (m1) on Azure 🖥️

**Domain:** Cloud & DevOps Summer Training  
**Objective:** To provision, configure, and successfully deploy a Virtual Machine named `m1` using the Azure Portal.

---

## 📝 Overview
In this task, we moved from account setup to actual Infrastructure as a Service (IaaS) deployment. We created a Virtual Machine (VM) named **`m1`**. This VM will serve as a foundational compute resource for hosting applications, running scripts, and practicing future DevOps tasks.

## 🛠️ Prerequisites
* An active Microsoft Azure account (Free Tier or Pay-As-You-Go).
* Basic understanding of compute resources (OS, RAM, CPU).

---

## 🚀 Step-by-Step Implementation

### Step 1: Navigating to Virtual Machines
From the Azure Portal dashboard, searched for "Virtual Machines" in the top search bar and clicked on **Create > Azure virtual machine**.


### Step 2: Configuring the Basics
In the **Basics** tab, I configured the core details for the instance:
* **Resource Group:** Created a new resource group (or selected an existing one) to logically group this task's resources.
* **Virtual machine name:** `m1`
* **Region:** Selected a suitable region (e.g., East US or Central India).
* **Image:** Selected the Operating System (e.g., Ubuntu Server or Windows Server).
* **Size:** Chosen a Free-Tier eligible size (like `Standard_B1s`).

<img width="1406" height="749" alt="image" src="https://github.com/user-attachments/assets/68b6fa88-ee93-4102-8453-6ad0a26d7692" />

### Step 3: Setting Up Administrator Account
Configured the admin credentials to securely access the `m1` VM later. 
* *Note: If using Linux, this involves setting up an SSH public key or a Password. If Windows, setting up a Username and Password.*
<img width="1127" height="766" alt="image" src="https://github.com/user-attachments/assets/cdacc5b3-ac74-4300-a693-4007184d53e2" />


### Step 4: Configuring Inbound Port Rules
To ensure the VM is accessible over the internet for our DevOps tasks, I allowed selected inbound ports (e.g., Port `22` for SSH on Linux, or Port `3389` for RDP on Windows, along with Port `80/443` for web traffic if needed).

### Step 5: Review and Create
Clicked on **Review + create**. Azure ran a final validation check. Once validation passed, I clicked **Create** to initialize the deployment.

### Step 6: Deployment Success
Waited a few minutes for Azure to allocate the compute, network, and storage resources. Once finished, Azure displayed the "Your deployment is complete" screen. I then clicked **Go to resource** to view the `m1` overview page.

<img width="1633" height="824" alt="image" src="https://github.com/user-attachments/assets/ac43d0c6-31cd-4372-9528-cfcdd293d8ce" />


---

## 🎯 Key Takeaways
* **Resource Groups:** Learned how Azure organizes related resources together.
* **Compute Sizing:** Understood how to select VM sizes based on requirement and Free Tier eligibility.
* **Networking & Security:** Learned the importance of opening specific inbound ports (like SSH/RDP) to allow remote access to the virtual machine.
