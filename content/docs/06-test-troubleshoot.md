---
title: "Test & Troubleshoot"
weight: 7
---

# Step 4 – Test & Troubleshoot

Now we’ll make sure:

1. your Pi is actually routing traffic, and  
2. you have some basic troubleshooting steps ready.

---

## 1. Basic Network Test

1. Confirm that the Pi is connected to your **modem / upstream router** via Ethernet.
2. On your laptop/phone, connect to your **new Pi Wi-Fi network** (the SSID you set in the previous step).
3. Open a browser and try loading a simple website (e.g., `example.com`).

If the page loads quickly, your basic router setup is working.

You can also look at the **Status** page in RaspAP:

![RaspAP status page showing interfaces](/images/ui/raspap-status.png "RaspAP status screen (placeholder)")

Check that:

- `eth0` has an IP address from your upstream router.
- `wlan0` is up and broadcasting.

---

## 2. Common Problems and Quick Checks

### “I don’t see the RaspAP Wi-Fi network.”

- Make sure the Pi has been **booting for at least 2–3 minutes**.
- Check power: is the Pi’s power LED solid and not constantly rebooting?
- If you recently changed hotspot settings and it stopped working:
  - Connect by Ethernet and use the RaspAP UI to reset hotspot settings, **or**
  - Re-flash the SD card and start fresh if you’re completely stuck.

---

### “I see the Wi-Fi, but there’s no internet.”

- Confirm the **Ethernet cable**:
  - one end must be in the Pi,
  - the other end in your modem or main router.
- In RaspAP’s **Status** page:
  - `eth0` should have a valid IP address.
  - `wlan0` should be running as an access point.
- If you changed advanced DNS or DHCP settings, try resetting them to defaults.

---

### “I can’t reach `10.3.141.1` anymore.”

This can happen after switching modes or changing network settings.

Try:

1. Using `http://raspberrypi.local` in your browser, or  
2. Checking your upstream router’s **client list** to see what IP address the Pi has now, then browsing to that IP.

If that still doesn’t work and you’re not attached to your settings, the most beginner-friendly fix is to **re-flash the SD card** with the RaspAP image and redo the steps. It’s annoying, but also a clean reset.

---

At this point, if:

- the Pi is on,
- your device can connect to the Pi’s Wi-Fi,
- and you can browse the internet,

…then you have a working Pi-based router with the simple RaspAP setup.
