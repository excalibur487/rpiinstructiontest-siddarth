---
title: "Flash the RaspAP Image"
weight: 4
---

# Step 1 – Flash the RaspAP Image

In this step you will:

1. (Optionally) **format** your microSD card.
2. **Download** the RaspAP prebuilt image.
3. Use **Raspberry Pi Imager** to write the image to the card.

This is the part where you should **double-check drive selection** so you don’t erase the wrong disk.

---

## 1. Format the microSD Card (Optional but Safer)

> ⚠️ **Warning:** This will erase the card. Make sure you picked the right drive.

1. Insert the microSD card into your computer.

   ![Inserting microSD card into laptop](/images/flash/step1-sd-insert.jpg "Insert the microSD card (placeholder)")

2. If your OS asks to format, let it format as **FAT32** or **ExFAT**.  
   - Alternatively, you can use a tool like *SD Card Formatter* or your OS’s disk utility.
3. After the quick format completes, the card is ready for flashing.

---

## 2. Download the RaspAP Prebuilt Image

1. Go to the RaspAP **“Simple Setup / Quick Start”** page in your browser.
2. In the **Custom OS image** section, download the recommended **RaspAP Raspberry Pi OS Lite** image for your Pi:
   - for example, a Debian 13 “Trixie” Lite image for 64-bit Pis.
3. Note the folder where the `.img` or `.img.zip` file is saved.

![RaspAP download page in browser](/images/flash/step2-raspap-download.png "RaspAP download page (placeholder)")

---

## 3. Use Raspberry Pi Imager (macOS / Windows / Linux)

Now we’ll use **Raspberry Pi Imager** to write the RaspAP image to the microSD card and pre-configure some settings.

The screens look slightly different across operating systems, so use the tab for your platform.

{{< tabs >}}
{{% tab "macOS" %}}

1. Install and open **Raspberry Pi Imager**.
2. Click **Choose device** and select your Pi model  
   (e.g., “Raspberry Pi 3 / 4 / 5” or “Raspberry Pi Zero 2 W”).

   ![Raspberry Pi Imager choose device screen on macOS](/images/flash/mac-choose-device.png "Pi Imager – Choose Device (placeholder)")

3. Click **Choose OS → Use custom**, then select the **RaspAP image** you downloaded.
4. Click **Choose storage** and select your microSD card.
5. Click **Next → Edit settings**:
   - Set **hostname** (e.g., `raspap-router`).
   - Create a **username and password** (write them down).
   - Optionally configure **Wi-Fi** if you want the Pi to join your existing network on first boot.
   - Set **time zone** and **keyboard layout**.
6. Open the **Services** tab:
   - Enable **SSH**.
   - Allow **password login** or add your SSH public key.
7. Save the settings and confirm the write operation.

   ![Raspberry Pi Imager settings dialog on macOS](/images/flash/mac-edit-settings.png "Pi Imager – Edit Settings (placeholder)")

8. Wait for the write and verify steps to finish, then safely eject the microSD card.

{{% /tab %}}

{{% tab "Windows" %}}

1. Install and open **Raspberry Pi Imager for Windows**.
2. Click **Choose device** → pick your Pi model.
3. Click **Choose OS → Use custom** and choose the **RaspAP image** file.
4. Click **Choose storage** → select the correct microSD card (check the drive letter).
5. Click **Next → Edit settings**:
   - Set **hostname** (e.g., `raspap-router`).
   - Set **username and password**.
   - (Optional) Configure **Wi-Fi SSID and password** for your home network so the Pi can join it.
   - Set your **time zone** and **keyboard layout**.
6. In **Services**, enable **SSH** and choose password or key-based login.
7. Start the write process and let the verify step complete.
8. Use “Safely remove hardware” to eject the card cleanly.

![Raspberry Pi Imager on Windows with device, OS, and storage selected](/images/flash/windows-imager-main.png "Pi Imager on Windows (placeholder)")

{{% /tab %}}

{{% tab "Linux" %}}

1. Install **Raspberry Pi Imager** from your distro’s repo or as an AppImage, then open it.
2. Click **Choose device** → pick your Pi model.
3. Click **Choose OS → Use custom** and select the **RaspAP image**.
4. Click **Choose storage** → choose the correct microSD device (e.g., `/dev/sdb`).
5. Click **Next → Edit settings**:
   - Set **hostname**.
   - Set **username/password**.
   - (Optional) Configure **Wi-Fi** SSID/password and Wi-Fi country.
6. In **Services**, enable **SSH** and choose login method (password/key).
7. Start writing and wait for the verify step.
8. Unmount/eject the microSD card when done.

![Raspberry Pi Imager on Linux](/images/flash/linux-imager-main.png "Pi Imager on Linux (placeholder)")

{{% /tab %}}
{{< /tabs >}}

Once you’ve flashed the SD card and safely ejected it, you’re ready for **first boot**.
