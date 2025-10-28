🧠 Proxmox + PNETLab Setup Guide (Dell PowerEdge R710)

This document provides a complete installation and configuration guide for setting up Proxmox Virtual Environment (VE) and PNETLab on a Dell PowerEdge R710 server.
It also includes a network flow diagram explaining how traffic moves between physical and virtual environments.

🧩 What is Proxmox VE?

Proxmox VE is an open-source virtualization platform that allows you to run and manage virtual machines (VMs) and Linux containers (LXC) efficiently.

🔑 Key Features

Web-based GUI for VM, storage, and network management

Integrated backup & clustering features

KVM for full virtualization, LXC for lightweight containers

VLAN & bridge networking for advanced topologies

Debian-based and completely open source

🌐 What is PNETLab?

PNETLab is a network emulation platform (like EVE-NG) that supports multiple vendor images — including Cisco, Palo Alto, Fortinet, Juniper, etc.

💡 Use Cases

Simulating enterprise network environments

Building CCNA, CCNP, and CCIE-level topologies

Practicing firewall, router, and switch configurations

🖥️ Hardware Requirements
Component	Specification
Server Model	Dell PowerEdge R710
CPU	Dual Intel Xeon
RAM	32 GB (minimum), 64 GB + recommended
Storage	SSD or RAID (500 GB minimum)
Network	2× Gigabit Ethernet NICs

⚙️ Step 1 — Install Proxmox VE
1️⃣ Prepare Installation Media

Download the ISO:
🔗 https://www.proxmox.com/en/downloads

Create a bootable USB using Rufus or BalenaEtcher.

2️⃣ BIOS Configuration

Enter BIOS (F2 or Ctrl + E)

Enable VT-x / VT-d (virtualization)

Configure RAID with PERC Controller (Ctrl + R)

3️⃣ Install Proxmox

Boot from USB → Select Install Proxmox VE

Choose target disk, network, and root password

Finish setup and reboot
