# 🪟 Installing Windows VM on Proxmox (with VirtIO Drivers + Network Fix)

This guide explains how to install **Windows on Proxmox**, upload ISOs, configure the VM, and fix driver or network issues.  
It’s meant as a quick reference for your future Windows VM setups.

---

## ⚙️ Step 1: Upload Windows ISO to Proxmox

1. Download the **Windows ISO** file (shared by Umair via Gmail).  
2. In Proxmox, go to:  
   **`local → ISO Images → Upload`**  
3. Attach the downloaded **Windows ISO** file.

---

## 📦 Step 2: Upload VirtIO Drivers ISO

1. Download the **VirtIO Drivers ISO** (for Windows).  
2. In Proxmox, go to:  
   **`local → ISO Images → Upload`**  
3. Attach the **VirtIO drivers** file (usually named like `virtio-win.iso`).
### `https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/latest-virtio/`

---

## 🖥️ Step 3: Create a New Virtual Machine (VM)

Use the following configuration as a reference:

### Recommended Configuration:
- **Memory:** 4–8 GB (or more if available)  
- **Processors:** 2–4 cores  
- **BIOS:** Default (SeaBIOS)  
- **Machine:** `pc-i440fx`  
- **SCSI Controller:** VirtIO SCSI single  
- **Hard Disk:** qcow2 (around 60–80 GB)  
- **CD/DVD Drive 1:** VirtIO Drivers ISO  
- **CD/DVD Drive 2:** Windows ISO  
- **Network Device:** VirtIO (bridge to your main `vmbr`)

---

## 🪄 Step 4: Install Windows via Console

1. Start the VM and open the **Console**.  
2. Proceed through the Windows installation steps.  
3. When prompted to select a disk (and none appear):  
   - Click **Load Driver**.  
   - Browse to **D:\ (VirtIO Drive)**.  
   - Select the proper **storage driver** → click **OK**.  
4. Continue with installation → set your language, region, and create a user/password.  
5. Wait for reboot → login once setup completes.

---

## 🌐 Step 5: Enable Internet Access

If the Internet doesn’t work right away, try one of these fixes:

### 🧩 Option 1: Update Drivers via Device Manager

1. Open **Device Manager**.  
2. Right-click any **Unknown Device** → **Update Driver**.  
3. Choose **Browse my computer for drivers** → navigate to **D:\ (VirtIO ISO)**.  
4. Repeat for all missing devices (especially **Network Adapter**).

---

### 🌍 Option 2: Fix DNS Manually (if no Internet)

1. Press **Win + R**, then type:
   ```bash
   ncpa.cpl
