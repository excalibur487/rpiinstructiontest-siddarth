---
title: "Secure & Rename Your Router"
weight: 6
---

# Step 3 – Secure & Rename Your Router

Now that you’re in the RaspAP web interface, we’ll:

1. change the **admin password**, and  
2. change the **Wi-Fi name (SSID)** and password.

This is important because the defaults are public and not safe to leave in place.

---

## 1. Change the Admin Password

1. In the left sidebar, find the **Authentication** or **System / Authentication** section (the exact label can vary slightly by version).
2. Change the password for the `admin` user to something **strong and unique**.
3. Save your changes.

From now on, you’ll use this new password to log into the RaspAP web UI.

![RaspAP admin password settings page](/images/ui/raspap-auth-settings.png "Admin authentication settings (placeholder)")

---

## 2. Change the Wi-Fi Network Name and Password

1. In the sidebar, go to **Hotspot → Security** (or similar).
2. In the **Security** section:
   - Set a new **SSID** (Wi-Fi name), such as `MyPiRouter` or `TravelPi`.
   - Set a new **Pre-shared key (PSK)**, which is your Wi-Fi password.
3. Save the changes.
4. When prompted, **restart the hotspot**.

![RaspAP hotspot security settings screen](/images/ui/raspap-hotspot-security.png "Hotspot security settings (placeholder)")

After the hotspot restarts:

- your old `RaspAP` network will disappear,
- your new SSID will appear with the new password you chose.

Reconnect your laptop or phone to the **new Wi-Fi network**.

---

## 3. Keep the Setup Simple

For this beginner-friendly route, we recommend:

- Leaving **interface assignments** at their defaults:
  - Ethernet (`eth0`) for upstream internet,
  - Wi-Fi (`wlan0`) for your hotspot.
- Not touching advanced settings like:
  - firewall rules,
  - custom NAT or routing,
  - VPN, ad-blocking, or special DNS setups.

These can all be added later once the basic router is working reliably.
