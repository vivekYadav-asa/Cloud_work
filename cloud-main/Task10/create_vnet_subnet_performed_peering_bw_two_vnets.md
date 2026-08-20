# Task 10: Virtual Networks, Subnets, and VNet Peering 🌐🔗

**Domain:** Cloud & DevOps Summer Training  
**Objective:** To create a custom Virtual Network (`labvnet`) with two isolated subnets (`subnet 1` and `subnet 2`), deploy a Virtual Machine into each subnet, and configure VNet Peering to allow secure communication with another Virtual Network.

---

## 📝 Overview
Networking is the backbone of cloud infrastructure. In this task, we built a custom network topology. We created `labvnet` and logically divided it into two subnets. After deploying VMs into these subnets, we established **VNet Peering**, which routes traffic between two separate Azure Virtual Networks privately over Microsoft's backbone infrastructure, without exposing data to the public internet.

## 🛠️ Prerequisites
* An active Azure account.
* Another existing Virtual Network (e.g., the default VNet where `m1` or `m2` reside) to act as the peering target.

---

## 🚀 Step-by-Step Implementation

### Phase 1: Creating the Virtual Network and Subnets

#### Step 1: Provisioning `labvnet`
In the Azure Portal, I searched for **Virtual Networks** and clicked **Create**. I assigned it to my Resource Group, named it `labvnet`, and selected the region. 
<img width="879" height="768" alt="image" src="https://github.com/user-attachments/assets/9cc8d900-2732-4257-819a-2e08afce8d77" />


#### Step 2: Defining the IP Address Space and Subnets
Under the **IP Addresses** tab, I defined the IPv4 address space (e.g., `10.0.0.0/26`). I then removed the "default" subnet and explicitly added two new subnets:
* **Name:** `subnet 1` (Address range: `10.0.0.0/25`)
* **Name:** `subnet 2` (Address range: `10.0.0.128/25`)
After configuring, I clicked **Review + create** and deployed the VNet.

<img width="829" height="707" alt="image" src="https://github.com/user-attachments/assets/dda465bd-10f3-4363-93c9-8eb1a9cf8cda" />

---

### Phase 2: Deploying VMs into the Subnets

#### Step 3: Deploying VM 1 to `subnet 1`
I created a new Virtual Machine. In the **Networking** tab during creation, I specifically selected `labvnet` as the Virtual network and `subnet 1` as the Subnet. I completed the deployment.



#### Step 4: Deploying VM 2 to `subnet 2`
I repeated the process to create a second Virtual Machine, this time selecting `labvnet` as the Virtual network and `subnet 2` as the Subnet. 

---

### Phase 3: Configuring VNet Peering

#### Step 5: Initiating the Peering Connection
I navigated to the `labvnet` resource page. From the left-hand menu under **Settings**, I clicked on **Peerings** and selected **+ Add**.
<img width="1149" height="789" alt="image" src="https://github.com/user-attachments/assets/3bfc459e-fd6b-49f8-8ac4-1a8fcbd65f87" />


#### Step 6: Configuring the Peering Link
I filled out the peering configuration to connect `labvnet` to my other existing VNet:
* **Peering link name (Local to Remote):** `labvnet-to-othervnet`
* **Virtual network (Remote):** Selected the other VNet from the dropdown.
* **Peering link name (Remote to Local):** `othervnet-to-labvnet`
Azure automatically handles creating the link in both directions. I clicked **Add**.

<img width="851" height="764" alt="image" src="https://github.com/user-attachments/assets/266bb308-5cf9-4e94-8cd1-c4a6e66b7548" />
<img width="826" height="750" alt="image" src="https://github.com/user-attachments/assets/a3d3b31d-5b87-4d33-a652-832e29365295" />


#### Step 7: Verifying Peering Status
Once deployed, I checked the **Peerings** page in `labvnet`. The Peering status successfully showed as **Connected**. VMs in `labvnet` can now communicate with VMs in the peered network using their private IP addresses.
<img width="1904" height="554" alt="image" src="https://github.com/user-attachments/assets/423b1087-b28b-4fdb-8d53-a515655d2719" />


---

## 🎯 Key Takeaways
* **Subnet Isolation:** Learned how to logically partition a large VNet (`/16`) into smaller, manageable subnets (`/24`) to organize resources.
* **Network Placement:** Understood that VMs must be explicitly placed into specific virtual networks and subnets during provisioning.
* **VNet Peering:** Demonstrated that Azure VNets are isolated by default, but Peering securely bridges them together using private IP routing without traversing the public internet.
