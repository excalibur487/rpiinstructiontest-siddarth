---
title: "Hardware & Software Requirements"
weight: 3
---

# What You Need

This section lists the **hardware** and **software** you’ll need before you start flashing anything.

---

## Raspberry Pi Options

These are the most beginner-friendly options:

### Raspberry Pi 3B / 3B+ / 4 / 5

- Has **built-in Ethernet + Wi-Fi**.
- Works well as a **small home or travel router**.
- No USB network adapters required.

**Recommended for most beginners.**

![Example Raspberry Pi with Ethernet and Wi-Fi](/images/setup/pi-with-ethernet-and-wifi.jpg "Example Raspberry Pi with Ethernet and Wi-Fi (placeholder)")

### Raspberry Pi Zero 2 W (or Zero W)

- Very small and low-power, good for travel.
- Needs a **second network interface**, usually:
  - a **USB-to-Ethernet** adapter (recommended), or
  - a USB Wi-Fi adapter (more advanced).

This setup is slightly more fragile for beginners, but still doable.

![Raspberry Pi Zero 2 W next to USB Ethernet adapter](/images/setup/pi-zero-ethernet.jpg "Pi Zero 2 W with USB Ethernet (placeholder)")

> If you have the choice, start with a **Pi 3B+ or newer** for the simplest wiring.

---

## Other Hardware

You’ll also need:

- **MicroSD card** – at least **16 GB**, blank or okay to erase.
  - Faster cards make updates smoother, but any decent card works.
- **Power supply** – 5V, at least **1.5–2 A** for most Pis.
- **Ethernet cable** – to connect the Pi to your **modem or upstream router**.
- **Computer with an SD card reader** – macOS, Windows, or Linux.

Optional but helpful:

- **HDMI display + keyboard** to debug if headless setup fails.

![Plugging microSD card into laptop card reader](/images/setup/insert-sd-into-laptop.jpg "Insert microSD card into card reader (placeholder)")

---

## Software / Downloads

You will need:

1. **RaspAP prebuilt OS image**  
   Download the latest **custom Raspberry Pi OS Lite image with RaspAP pre-installed** from the RaspAP “Simple Setup / Quick Start” page.

2. **Raspberry Pi Imager**  
   Official tool from the Raspberry Pi Foundation used to **flash the RaspAP image** onto your microSD card.

We’ll walk through using Raspberry Pi Imager in the next section, with tabbed instructions for **macOS, Windows, and Linux**.
