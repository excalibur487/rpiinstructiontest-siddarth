---
title: "Build Your Own Router with a Raspberry Pi (RaspAP)"
weight: 10
---

# Build Your Own Router with a Raspberry Pi

**Authors:** Siddarth Shinde, Ethan Xu, Caleb Locklear  
**Last updated:** 16 November 2025  

This guide walks you through turning a Raspberry Pi into a simple home or travel router using **RaspAP** and its **prebuilt OS image**. The main path avoids the command line as much as possible and is written for **beginners** who:

- have never set up a router before,
- are new to Linux, or
- just want an easier, cheaper alternative to buying a new router.

An optional advanced section at the end points you to the **manual RaspAP installation** and more networking features.

---

## 1. Why Build Your Own Router?

Many people either:

- rent a router from their internet provider every month, or  
- buy a box that works, but feels like a black box.

Using a Raspberry Pi as your router gives you:

### 1.1 Customization and Control

You can:

- change Wi-Fi name and password,
- add or change DNS servers,
- later add things like VPN, ad-blocking DNS, or custom firewall rules (within your local laws and ISP rules).

RaspAP is designed to make these options available through a web interface instead of only configuration files. 

### 1.2 Cost and Re-use

If you already own a Raspberry Pi, you can turn it into a router instead of:

- paying your ISP every month for their router, or  
- buying a separate travel router.

Even if you buy a Pi for this project, it can still be cheaper and more flexible than many off-the-shelf routers, especially for learning and experimenting.

### 1.3 Privacy, Security, and Travel

With your own router you can:

- avoid using random public Wi-Fi directly (airports, hotels, coffee shops),  
- put all your devices behind one Pi “bubble”,  
- add DNS filtering or ad-blocking later (e.g., Pi-hole, or RaspAP DNS blacklists).

### 1.4 Educational Value

This project is a gentle way to see real network concepts in action:

- **DHCP** – how devices get IP addresses,  
- **NAT** – how many devices share one public IP,  
- **port forwarding** – how incoming traffic can be routed to a specific device.

You do not need to fully understand these to finish the guide, but we’ll name them and briefly explain what each does.

---

## 2. What You Need

### 2.1 Raspberry Pi Options

You can use different Raspberry Pi models. These are the easiest options for beginners:

- **Raspberry Pi 3B / 3B+ / 4 / 5**  
  - Has built-in Wi-Fi and Ethernet.  
  - Works well as a small home or travel router.  
  - No USB network adapters required.

- **Raspberry Pi Zero 2 W (or Zero W)**  
  - Compact and low-power, good for travel.  
  - **Needs a second network interface**, usually:
    - USB-to-Ethernet adapter (recommended), or
    - USB Wi-Fi adapter (more advanced).
  - Slightly more fragile setup for beginners.

> If you have a choice, start with a **Pi 3B+ or newer**. It has two network interfaces built-in and is easier to get working.

### 2.2 Other Hardware

- **MicroSD card** – at least **16 GB**, blank or containing data you’re okay losing.  
- **Reliable power supply** – 5V, at least 1.5–2 A for most Pis.  
- **Ethernet cable** – to connect the Pi to your modem or upstream router (for internet).  
- **Computer with an SD card reader** – macOS, Windows, or Linux.  
- Optional: **HDMI display + keyboard** for first boot. This guide assumes headless setup where possible but a screen can help if something goes wrong.

### 2.3 Software / Downloads

You will need:

1. **RaspAP prebuilt OS image**  
   - From RaspAP’s **Simple Setup / Quick Start** docs, download the latest custom Raspberry Pi OS Lite image with RaspAP pre-installed (arm64 or armhf, depending on your Pi).

2. **Raspberry Pi Imager**  
   - The official flashing tool from the Raspberry Pi Foundation. Use this to write the RaspAP image to your microSD card. 

---

## 3. Big Picture: What We’re Going to Do

1. **Erase and flash** the microSD card with a RaspAP prebuilt image.  
2. **Customize basic settings** in Raspberry Pi Imager (Wi-Fi, SSH, username/password).  
3. **Boot the Pi** and wait for RaspAP to start its Wi-Fi hotspot.  
4. **Connect to the Pi’s Wi-Fi** and open the RaspAP web interface.  
5. **Change default admin and Wi-Fi passwords** (important for security). 
6. **Test the router** by browsing from a connected device.

Manual installation (starting from plain Raspberry Pi OS and running the RaspAP installer) is covered briefly at the end and linked to the official docs. 

---

## 4. Step 1 – Prepare and Flash the microSD Card

### 4.1 Format the microSD Card (optional but safer)

> ⚠️ **Warning:** This will erase the card. Double-check you picked the correct drive.

1. Insert the microSD card into your computer.  
2. If your OS complains about formatting, let it format as **FAT32** or **ExFAT**, or:
   - Use **SD Card Formatter** or your OS’s disk utility to do a “quick format”.  
3. Once it completes, you’re ready to flash the new image.

### 4.2 Download the RaspAP Prebuilt Image

1. Go to the **RaspAP “Simple Setup” / Quick Start** page.  
2. In the **Custom OS image** section, download the recommended **RaspAP Raspberry Pi OS Lite** image for your Pi (for example, the arm64 Lite image based on Debian 13 “Trixie”).
3. Note where the `.img` or `.img.zip` file was saved.

### 4.3 Use Raspberry Pi Imager (with tabs for each OS)

We’ll now use Raspberry Pi Imager to write the RaspAP image to the card. The exact screens look slightly different on macOS, Windows, and Linux, but the steps are the same.

{{< tabs >}}
{{% tab "macOS" %}}

1. Install **Raspberry Pi Imager** from the official Raspberry Pi website and open it.
2. Click **Choose device** and select your Pi model (e.g., “Raspberry Pi 3/4/5” or “Raspberry Pi Zero 2 W”).  
3. Click **Choose OS → Use custom**, then select the **RaspAP image** you downloaded.  
4. Click **Choose storage** and select your microSD card.  
5. Click **Next**, then **Edit settings**:
   - Set **hostname** (e.g., `raspap-router`).
   - Create a **username and password** (write them down).
   - Enable **Wi-Fi** and enter your current home Wi-Fi name (SSID) and password if you want the Pi to join it on first boot (optional if you plan to use Ethernet only).
   - Set **time zone** and **keyboard layout**.  
6. Open the **Services** tab:
   - Enable **SSH**.
   - If you have an SSH public key, choose **public key auth**; otherwise allow password login.  
7. Save, confirm the warning, and let the imager write + verify the card.  
8. When it finishes, safely eject the microSD card.

{{% /tab %}}

{{% tab "Windows" %}}

1. Install **Raspberry Pi Imager for Windows** and open it. 
2. Click **Choose device** → pick your Pi model.  
3. Click **Choose OS → Use custom**, and pick the **RaspAP image** you downloaded.  
4. Click **Choose storage** and select your microSD card (double-check the drive letter).  
5. Click **Next → Edit settings**:
   - Set **hostname** (for example, `raspap-router`).
   - Set **username and password**.
   - Optionally configure **Wi-Fi** SSID and password if you want the Pi to join your existing network on first boot.
   - Choose your **time zone** and **keyboard layout**.  
6. Under **Services**, enable **SSH** and allow password or public key access.  
7. Confirm and start writing. Wait until the progress bar and verify step are done.  
8. Click **Continue**, then safely remove the SD card using the “Safely remove hardware” option.

{{% /tab %}}

{{% tab "Linux" %}}

1. Install **Raspberry Pi Imager** from your distro’s repositories or AppImage and open it. 
2. Click **Choose device** → select your Pi model.  
3. Click **Choose OS → Use custom** and select the **RaspAP image** file.  
4. Click **Choose storage** → pick your microSD device (e.g., `/dev/sdb`).  
5. Click **Next → Edit settings**:
   - Set **hostname** (e.g., `raspap-router`).
   - Configure **username/password**.
   - (Optional) Set **Wi-Fi** SSID and password and select your Wi-Fi country.  
6. In **Services**, enable **SSH** and choose how you’ll log in (password or key).  
7. Start writing; wait for the verify step to finish.  
8. Eject the microSD card safely.

{{% /tab %}}
{{< /tabs >}}

---

## 5. Step 2 – First Boot and Connecting to RaspAP

1. Insert the flashed **microSD card** into your Raspberry Pi.  
2. Connect:
   - Pi → modem/router with **Ethernet** (for internet), and  
   - plug in the **power supply**.

Give the Pi a few minutes on first boot; it will expand the filesystem and start RaspAP.

### 5.1 Default RaspAP Hotspot and Login

After setup, RaspAP creates a default Wi-Fi network and admin login. According to the official docs, the initial settings are: 

- **Router IP (from a client device):** `http://10.3.141.1`  
- **Admin username:** `admin`  
- **Admin password:** `secret`  
- **SSID (Wi-Fi network name):** `RaspAP`  
- **Wi-Fi password:** `ChangeMe`  
- **DHCP range:** `10.3.141.50 – 10.3.141.254`

> These defaults are widely known. **You should change them as soon as you log in.**   

### 5.2 Connect from Your Laptop or Phone

1. On your laptop or phone, open Wi-Fi networks.  
2. Find **`RaspAP`** and connect using password **`ChangeMe`**.  
3. Once connected, open a browser and go to `http://10.3.141.1`  
   - If that fails (especially in bridged mode later), you can also try `http://raspberrypi.local` or your hostname from the imager.  
4. You should see the RaspAP login page. Enter:
   - Username: `admin`  
   - Password: `secret`  

You are now inside the RaspAP web interface.

---

## 6. Step 3 – Make It Yours (Secure and Rename)

### 6.1 Change Admin Password

1. In the left sidebar, open **Authentication** (or similar, depending on version).  
2. Set a new strong password for the `admin` account.  
3. Save your changes.

### 6.2 Change Wi-Fi Network Name and Password

1. Go to **Hotspot → Security**.   
2. Change:
   - **SSID** (Wi-Fi name) to something like `MyPiRouter` or `TravelPi`.  
   - **Pre-shared key (PSK)** to a strong Wi-Fi password.  
3. Save and **restart the hotspot** when prompted.

Your devices will disconnect from `RaspAP` and you should now see your new SSID. Connect to it with your new password.

---

## 7. Step 4 – Basic Network Check

At this point, the most common beginner setup is:

- Internet coming into the Pi via **Ethernet (`eth0`)**,  
- Wi-Fi hotspot going out through **`wlan0`** (the onboard Wi-Fi adapter).

To test:

1. Make sure your Pi is plugged into your modem/router with Ethernet.  
2. On your laptop/phone, join your **new Pi Wi-Fi** (the SSID you just set).  
3. Try visiting a website (for example, `example.com`).  
4. If it loads, your basic router configuration is working.

---

## 8. Step 5 – Quick Troubleshooting

Here are three very common problems and quick checks.

### 8.1 “I can’t see the `RaspAP` Wi-Fi network.”

- Double-check the Pi is:
  - powered on (power LED solid), and  
  - finished booting (wait 2–3 minutes after first boot).  
- If you changed hotspot settings and it stopped working:
  - Try a **system reset** from **System → Tools → Perform reset**, which restores default RaspAP config.  
- Make sure Wi-Fi country is set correctly in the Pi’s system settings; mismatched regulatory settings can stop the AP from starting.

### 8.2 “I see the Wi-Fi, but there’s no internet.”

- Ensure the **Ethernet cable** is connected from Pi → modem/router.  
- In RaspAP, open **Status** and check that:
  - `eth0` has an IP address from your upstream router.  
  - `wlan0` is up and broadcasting.  
- If you changed DNS or DHCP advanced settings, use **System reset** to return to defaults and test again.

### 8.3 “I can’t reach 10.3.141.1 anymore.”

This can happen in **bridged mode** or after major network changes.

- Try going to `http://raspberrypi.local` (or whatever hostname you set in the imager).  
- Check which IP your Pi has from your upstream router and browse to that address instead.  
- If you’re stuck and don’t mind losing settings, re-flash the SD card with the RaspAP image and start over.

---

## 9. Alternatives to a Raspberry Pi Router

If you like the *idea* of this project but want different hardware, here are some alternatives.

### 9.1 Off-the-Shelf Routers (e.g., TP-Link)

- **What they are:** Standard home routers from brands like TP-Link, ASUS, etc.  
- **Pros:**
  - Easiest to set up (plug in, follow quick-start wizard).
  - Firmware is tuned for Wi-Fi performance and reliability.  
- **Cons:**
  - Less customizable than a Pi + RaspAP.
  - Often locked to vendor firmware; advanced features may require more expensive models.

### 9.2 Higher-Power Single Board Computers (e.g., Rock 5C)

- **What they are:** More powerful SBCs with faster CPUs and sometimes better I/O.  
- **Pros:**
  - More performance for heavy loads, VPNs, or advanced routing.  
- **Cons:**
  - Community support and prebuilt images may be weaker than Raspberry Pi.
  - Usually more expensive and slightly more power-hungry.

### 9.3 x86 Boards / Mini PCs (e.g., ZimaBoard)

- **What they are:** Small x86 computers designed for DIY servers and routers.  
- **Pros:**
  - Multiple Ethernet ports; can run full Linux/BSD router distros (pfSense, OpenWrt, etc.).  
- **Cons:**
  - More expensive than a Pi.
  - Overkill for simple home or travel routing, and draws more power.

For this course project, the **Pi + RaspAP** approach keeps the instructions focused, testable, and beginner-friendly, while still having room for advanced tweaks.

---

## 10. Going Further (Optional / Advanced)

If you’d like to extend these instructions beyond the beginner path, here are directions and links.

### 10.1 Manual RaspAP Installation (CLI)

If you prefer to start from a plain Raspberry Pi OS Lite image instead of the prebuilt RaspAP image, follow the official **Manual installation** or **Quick installer** guides. 

The basic idea:

1. Flash **standard Raspberry Pi OS Lite** with Raspberry Pi Imager.  
2. Boot the Pi and update packages:
   ```bash
   sudo apt-get update
   sudo apt-get full-upgrade
   sudo reboot
