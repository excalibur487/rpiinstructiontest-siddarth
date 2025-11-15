---
title: "Overview & Motivation"
weight: 2
---

# Build Your Own Router with a Raspberry Pi

**Authors:** Siddarth Shinde, Ethan Xu, Caleb Locklear  
**Last updated:** 16 November 2025  

This guide walks you through turning a Raspberry Pi into a working router using **RaspAP**. Our main goal is to give **beginner-friendly**, testable instructions that do **not** assume deep networking or Linux knowledge.

Instead of treating the router as a “black box,” you’ll:

- see what the Pi is doing at each step,
- learn basic concepts like DHCP, NAT, and Wi-Fi security,
- end up with a router you can actually use at home or when you travel.

---

## Why Build Your Own Router?

Many people either:

- rent a router from their internet provider every month, or  
- buy a plug-and-play router they never really understand.

Using a Raspberry Pi as your router gives you:

### Customization and Control

You can:

- choose your own Wi-Fi network name and password,
- change DNS servers,
- later add things like VPN, ad-blocking DNS, or custom firewall rules (within local laws and ISP rules).

The key idea: **you** control the device, not your ISP or router vendor.

### Cost and Re-use

If you already own a Pi, you can:

- avoid monthly rental fees for an ISP router,
- avoid buying yet another plastic box.

Even if you buy a Pi for this, it can still be cheaper and more flexible than many off-the-shelf routers, especially if you like to tinker or learn.

### Privacy, Security, and Travel

With your own Pi router you can:

- avoid connecting devices directly to random public Wi-Fi,
- put all your devices behind a single “Pi bubble,”
- add DNS filtering or ad-blocking later (e.g., Pi-hole or RaspAP DNS blacklists).

It also makes a nice **travel router**: plug the Pi into hotel Ethernet (if available), or use it with a hotspot and share a single connection safely across your devices.

### Educational Value

You’ll get a gentle, concrete intro to real networking ideas:

- **DHCP** – how devices automatically get IP addresses,  
- **NAT** – how many devices share one public IP,  
- **port forwarding** – how incoming traffic can be routed to a specific device.

You don’t need to fully understand these to follow the guide. We’ll name them and give short explanations where they appear so the instructions double as a learning tool.
