---
title: "First Boot & Connecting"
weight: 5
---

# Step 2 – First Boot & Connecting to RaspAP

In this step you’ll:

- plug everything into the Raspberry Pi,
- power it up,
- connect to the default RaspAP Wi-Fi,
- log into the web interface.

---

## 1. Wire Up the Raspberry Pi

1. Insert the freshly flashed **microSD card** into the Pi.

   ![Inserting microSD card into Raspberry Pi](/images/setup/insert-sd-into-pi.jpg "Insert SD card into Pi (placeholder)")

2. Connect the **Ethernet cable**:
   - one end to the Pi’s Ethernet port,
   - the other end to your **modem** or **upstream router**.

   ![Connecting Ethernet cable from Pi to home router](/images/setup/connect-ethernet.jpg "Connect Pi to router via Ethernet (placeholder)")

3. Plug in the **power supply** to the Pi and then to a wall outlet.

   ![Powering on Raspberry Pi](/images/setup/power-on-pi.jpg "Power on the Pi (placeholder)")

Give the Pi **2–3 minutes** on first boot. It will expand the filesystem and start the RaspAP services.

---

## 2. Default RaspAP Hotspot Settings

After setup, RaspAP creates a default Wi-Fi network and web admin login. By default, these are:

- **Router web interface:** `http://10.3.141.1`  
- **Admin username:** `admin`  
- **Admin password:** `secret`  
- **Wi-Fi SSID:** `RaspAP`  
- **Wi-Fi password:** `ChangeMe`  
- **DHCP range:** `10.3.141.50 – 10.3.141.254`

> These defaults are public and widely documented.  
> We’ll **change them for security** in the next section.

---

## 3. Connect from a Laptop or Phone

1. On your laptop or phone, open the list of Wi-Fi networks.
2. Look for the network named **`RaspAP`** and connect using password **`ChangeMe`**.

   ![Wi-Fi menu showing RaspAP network](/images/ui/wifi-menu-raspap.png "RaspAP SSID in Wi-Fi list (placeholder)")

3. Once connected, open a browser and go to:

   - `http://10.3.141.1`

4. You should see the **RaspAP login page**.

   ![RaspAP login page in browser](/images/ui/raspap-login.png "RaspAP login screen (placeholder)")

5. Log in with:

   - Username: `admin`  
   - Password: `secret`

If this works, you’re now inside the RaspAP web interface and ready to customize your router.
