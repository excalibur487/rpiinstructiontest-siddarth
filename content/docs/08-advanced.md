---
title: "Advanced & Manual Installation"
weight: 9
---

# Advanced & Manual Installation (Optional)

The main guide uses the **prebuilt RaspAP OS image** so beginners don’t have to touch the terminal.

If you’re comfortable with the command line or want more control, you can:

- start from a **standard Raspberry Pi OS Lite** image,
- then install **RaspAP manually** with their installer,
- and layer on advanced features like ad-blocking, VPN, and more.

This section gives an overview and points you to the right external docs.

---

## 1. Manual RaspAP Installation (High-Level)

The general flow is:

1. Flash a fresh **Raspberry Pi OS Lite** image to the SD card using Raspberry Pi Imager.
2. Boot the Pi and update packages:

   ```bash
   sudo apt-get update
   sudo apt-get full-upgrade
   sudo reboot
