# Task 4: Hosting a Static Website on VM Localhost via RDP 🌐

**Domain:** Cloud & DevOps Summer Training  
**Objective:** To connect to the Azure Virtual Machine using Remote Desktop Protocol (RDP), configure a local web server, and host a static website accessible via `localhost`.

---

## 📝 Overview
In this task, we took our newly provisioned Virtual Machine and turned it into a web server. By connecting securely via RDP, we accessed the VM's graphical interface, deployed a web server environment (like IIS, XAMPP, or a simple HTTP server), placed our static website files in the root directory, and successfully served the site on the machine's localhost.

## 🛠️ Prerequisites
* The active Virtual Machine (`m1`) created in Task 3.
* Remote Desktop Connection (RDP) client (built-in on Windows).
* Basic static website files (`index.html`, `style.css`, etc.).

---

## 🚀 Step-by-Step Implementation

### Step 1: Connecting to the VM via RDP
Navigated to the Azure Portal, went to the `m1` VM overview, and clicked on **Connect > RDP**. I downloaded the RDP file, opened it, and logged in using the Administrator credentials configured during VM creation.
<img width="1077" height="743" alt="image" src="https://github.com/user-attachments/assets/3c42fc11-70c8-4c1c-9b85-89445bbd9a80" />
<img width="660" height="555" alt="image" src="https://github.com/user-attachments/assets/37638934-bd00-49dd-a1ed-1f8a27b86663" />
<img width="605" height="199" alt="image" src="https://github.com/user-attachments/assets/b05b06a3-b03b-473d-8844-a2c07e29f5d8" />



### Step 2: Preparing the Web Server Environment
Once inside the Windows VM desktop, I set up the web server. *(Note: Depending on your specific training instructions, this could be enabling IIS (Internet Information Services) via Server Manager, installing XAMPP, or running a simple Python/Node server).*


### Step 3: Deploying the Static Website Files
Copied my static website files (HTML, CSS, JS) from my local machine and pasted them into the VM. I then moved these files into the web server's root directory (e.g., `C:\inetpub\wwwroot` for IIS or the `htdocs` folder for XAMPP), replacing any default files.

<img width="1900" height="795" alt="image" src="https://github.com/user-attachments/assets/8dfdd253-8ff3-4aa4-a188-05069032fe3a" />
<img width="1469" height="713" alt="image" src="https://github.com/user-attachments/assets/f6f9b9ce-b376-4d6d-aa78-24c96b99e012" />


### Step 4: Accessing the Website on Localhost
Opened the web browser (like Microsoft Edge) **inside** the RDP session. In the address bar, I typed `http://localhost` and hit Enter. The static website successfully loaded, proving the local web server was correctly configured and serving the files.
<img width="1915" height="814" alt="image" src="https://github.com/user-attachments/assets/d491a4d0-c841-4a0c-90ed-2d86cb6b7a46" />
<img width="351" height="527" alt="image" src="https://github.com/user-attachments/assets/628c5d0a-a433-41b7-b43e-701dade87d26" />


---

## 🎯 Key Takeaways
* **Remote Desktop Protocol (RDP):** Gained hands-on experience connecting to and managing a cloud-based Windows server using a graphical interface.
* **Web Server Root Directories:** Learned how web servers map physical folders (like `wwwroot` or `htdocs`) to web addresses.
* **Localhost Concept:** Understood that `localhost` (or the IP `127.0.0.1`) refers to the machine you are currently working on—in this case, the Azure VM itself.
