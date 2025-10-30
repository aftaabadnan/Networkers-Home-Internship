# 🧠 Installing PNETLab on Proxmox

This guide walks you through installing **PNETLab** (the network emulation platform) on **Proxmox VE**, including file setup, extraction, and access configuration.

---

## 📥 Step 1: Download the PNETLab File

1. Open your browser and download PNETLab from the following link:  
   🔗 [Download PNETLab OVA/OVF File](https://drive.google.com/file/d/1BbOL7JEQbChymPeux9JGrHZpLsQyCpPQ/view)

2. The downloaded file will have an **`.ovf`** extension.  
   ⚠️ Proxmox **does not support `.ovf`** files directly — we’ll handle this next.

---

## 🔄 Step 2: Transfer File to Proxmox using WinSCP

1. Install and open **WinSCP** on your Windows system.  
2. Connect to your **Proxmox server** using:
   - **File Protocol:** SFTP  
   - **Host Name:** your Proxmox IP  
   - **Port Number:** 22  
   - **Username:** `root`  
   - **Password:** (your Proxmox password)

3. Once connected, drag and drop the downloaded `.ovf` file into the **root directory** of Proxmox (`/`).

---

## 📦 Step 3: Extract and Import the OVF File

1. Open your **Proxmox web console** or SSH into the Proxmox host.  
2. Navigate to the directory where you uploaded the `.ovf` file.  
3. Run the following command to extract the contents:

   ```bash
   tar -xvf PNET_VERSION
