# Task 11: Implementing an Azure Public Load Balancer ⚖️🌐

**Domain:** Cloud & DevOps Summer Training  
**Objective:** To provision an Azure Public Load Balancer and configure it to distribute incoming web traffic evenly across two backend Virtual Machines (`m1` and `m2`) located in different subnets (`subnet 1` and `subnet 2`) within `labvnet`.

---

## 📝 Overview
In a production environment, relying on a single server is a single point of failure. In this task, we implemented High Availability (HA) by deploying an **Azure Load Balancer**. We created a single public-facing Frontend IP and directed it to a Backend Pool containing our two VMs (`m1` and `m2`) sitting inside `labvnet`. If one VM goes down, the Load Balancer automatically routes all traffic to the healthy one.

## 🛠️ Prerequisites
* The custom Virtual Network (`labvnet`) created in Task 10.
* Two active Virtual Machines: `m1` (in `subnet 1`) and `m2` (in `subnet 2`).
* A web server (like IIS, Apache, or Nginx) installed on both VMs serving a default webpage so we can test the traffic distribution.

---

## 🚀 Step-by-Step Implementation

### Step 1: Creating the Load Balancer and Frontend IP
In the Azure Portal, I searched for **Load Balancers** and clicked **Create**. 
* **Basics:** Assigned it to my Resource Group and gave it a name (e.g., `lab-lb`). Selected **Public** as the type and **Regional** as the tier.
* **Frontend IP Configuration:** Clicked **Add a frontend IP configuration**, named it (e.g., `lb-frontend`), and created a new Public IP address so the Load Balancer can be accessed from the internet.
<img width="931" height="795" alt="image" src="https://github.com/user-attachments/assets/a85cb72b-9179-4688-93cb-39742cb78139" />
<img width="615" height="806" alt="image" src="https://github.com/user-attachments/assets/3aa9f540-8486-49c6-a99c-9ed7a73bc167" />


### Step 2: Configuring the Backend Pool
Next, I moved to the **Backend pools** tab to tell the Load Balancer where to send the traffic.
* Clicked **Add a backend pool** and named it (e.g., `lab-backend-pool`).
* Selected `labvnet` as the Virtual network.
* In the **Virtual machines** section, I clicked **Add**, and selected both `m1` (from subnet 1) and `m2` (from subnet 2).
<img width="1862" height="849" alt="image" src="https://github.com/user-attachments/assets/ac83ab0f-e5aa-488f-8395-4ed330ee01a1" />

### Step 3: Setting Up a Health Probe
The Load Balancer needs to know if the VMs are actually running before sending traffic to them. I went to the **Health probes** tab and created a new probe.
* **Protocol:** TCP (or HTTP).
* **Port:** 80 (Standard web traffic port).
* **Interval:** Left at the default (e.g., 5 seconds). This means the LB pings the VMs every 5 seconds to check if they are alive.


### Step 4: Creating the Load Balancing Rule
Finally, I tied everything together in the **Load balancing rules** tab. I created a rule (e.g., `HTTP-Rule`) that states:
* If traffic hits the **Frontend IP** on **Port 80**, 
* Send it to the **Backend Pool** (`lab-backend-pool`) on **Port 80**,
* Using the **Health Probe** we just created to monitor status.
I then clicked **Review + create** and deployed the Load Balancer.
<img width="1866" height="788" alt="image" src="https://github.com/user-attachments/assets/caf38ed1-d092-4304-aadc-4f1aeba901a0" />
<img width="1839" height="413" alt="image" src="https://github.com/user-attachments/assets/078c6ca6-dda8-4d55-a681-dc0af65d963f" />



### Step 5: Testing the Load Balancer
Once deployed, I copied the new **Public IP Address** of the Load Balancer from its overview page and pasted it into a web browser. The traffic successfully routed to one of the VMs. 

*(Optional test for proof: By stopping one of the VMs or refreshing the page across different network sessions, we can observe the Load Balancer seamlessly failing over or distributing the traffic to the other VM).*
<img width="1873" height="947" alt="image" src="https://github.com/user-attachments/assets/1376f87b-bad4-4add-85ff-0b0bd8327843" />



---

## 🎯 Key Takeaways
* **High Availability:** Demonstrated how Load Balancers eliminate single points of failure by spreading traffic across multiple instances.
* **Health Probes:** Understood that the LB actively monitors the health of `m1` and `m2` and will stop sending traffic to a node if it stops responding.
* **Single Entry Point:** Learned how to hide multiple backend servers behind one single Public IP address, improving both security and user experience.
