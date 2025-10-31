# 🧩 Configuring RustDesk in Proxmox

This guide explains how to set up the **RustDesk Server** inside a **Proxmox LXC container**, connect it with **pfSense** for controlled network access, and use it to allow **Windows VMs to communicate without Internet** — ideal for isolated lab environments like **PNETLab**.

---

## ⚙️ Step 1: Install RustDesk Server in Proxmox

1. Download the **RustDesk Server community script** for Proxmox.  
2. Deploy it inside an **LXC container**.  
3. Configure Internet access for the container through **pfSense**, allowing specific traffic via the firewall.  
4. **Umair provided IP ranges** for the RustDesk network to use internally.

---

## 💻 Step 2: Add Windows Virtual Machines

1. Create **two Windows VMs** in Proxmox.  
2. Install the **RustDesk client** on both machines.  
3. The main goal is to **access PNETLab without using the Internet** — by creating a private, local connection through the RustDesk server.

---

## 🔐 Why Install and Use RustDesk?

RustDesk acts as a **secure private remote-access bridge** between Windows VMs.  
It assigns **internal IP addresses** and keeps all communication **within your local IP range**, providing:

- Encrypted and private VM-to-VM connectivity  
- No dependence on external Internet access  
- A more secure and isolated testing environment

In short, RustDesk helps the Windows VMs communicate **locally and securely**, even when the Internet is disconnected.

---

## 🌐 Step 3: Configure Network on Windows VMs

Each Windows VM will receive an IP from **DHCP** (via Proxmox or pfSense).  
To manually configure IP settings and ensure local communication:

1. Inside the Windows VM, press **Win + R**, then type:
   ```cmd
   ncpa.cpl

if we take the gateway of pfsense we access the internet,
if we take the gateway of rustdesk we the the vms without the internet.
