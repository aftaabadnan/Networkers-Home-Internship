# 🧰 Fixing Cat Command & Repository Update (Quick Guide)

A simple recovery checklist for Proxmox or Debian systems when `cat` stops working or repositories become outdated.

---

### 1️⃣ Reinstall Coreutils
If `cat` doesn’t work:
```bash
apt install --reinstall coreutils
cat /etc/debian_version
If it says “cannot be downloaded”, your sources are outdated.

2️⃣ Update System
bash
Copy code
apt update
apt full-upgrade -y
reboot
3️⃣ Check Repositories
bash
Copy code
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
cat /etc/apt/sources.list.d/pve-enterprise.list
4️⃣ Replace “bullseye” with “bookworm”
Edit your repo files:

bash
Copy code
nano /etc/apt/sources.list
Change every bullseye → bookworm
Example:

bash
Copy code
deb http://ftp.debian.org/debian bookworm main contrib
5️⃣ Use No-Subscription Repo
Replace Proxmox enterprise repo with:

bash
Copy code
deb http://download.proxmox.com/debian/pve bookworm pve-no-subscription
6️⃣ Verify & Upgrade
Check for old entries:

bash
Copy code
grep -r "bullseye" /etc/apt/sources.list /etc/apt/sources.list.d/
Then update and upgrade:

bash
Copy code
apt update
apt dist-upgrade -y
7️⃣ Reboot & Confirm
bash
Copy code
reboot
cat /etc/debian_version
✅ cat works
✅ Debian version → Bookworm
✅ Proxmox uses no-subscription repo
