# DCNET - Dreamcast Online Revival

DCNET is a modern fork of DreamPi that enables Dreamcast games to go online again, reviving the classic online gaming experience of the Sega Dreamcast. This guide covers everything you need to get started, including setup instructions, supported games, troubleshooting tips, and more.

---

## Table of Contents

1. [Pre-requisites](#pre-requisites)  
2. [Setup Guide](#setup-guide)  
3. [Supported Games](#supported-games)  
4. [Troubleshooting](#troubleshooting)  
5. [Credits and Acknowledgments](#credits-and-acknowledgments)

---

## Pre-requisites

Before setting up DCNET, ensure you have the following:

### Dreamcast Console and Accessories
1. **Sega Dreamcast Console**  
   - A working Sega Dreamcast console (PAL, NTSC, or NTSC-J versions supported).  
   - All Dreamcast consoles originally came with a **dial-up modem**, which is required for online play.  

2. **Controller**  
   - At least one Sega Dreamcast controller is required for gameplay.  

3. **VMU (Visual Memory Unit)**  
   - A VMU is essential for saving game data and other in-game functionalities.  

4. **Optional Accessories**:  
   - **Keyboard/Mouse**: Useful for specific games (e.g., Quake, Planet Ring) or web browsing.  
   - **Broadband Adapter (BBA)**: For supported games (if you have one).  

---

### DreamPi Hardware
1. **Raspberry Pi**  
   - Any standard Raspberry Pi model is supported: **Pi 1, 2, 3, 4, 5, or Zero W 2**.  

2. **Compatible USB Modem**  
   - A USB modem is required to connect the Dreamcast to the Pi.  
   - **Known compatible models**:
     - Dell / Lenovo RD04-D400  
     - TRENDnet TFM-561U  
     - Zoom 3095  

3. **Line Voltage Inducer**  
   - Necessary for most Dreamcast modems to function correctly.  
   - **Examples**:
     - **PAL Line Voltage Inducer**: Available for £16.99 from the DreamPi website or via [this eBay link](https://www.ebay.co.uk/itm/276895422817?_skw=dreamcast+line+voltage&itmmeta=01JTGPA50RMXGBVJD4ERBT53DH&hash=item407840d961:g:17gAAOSwEIhnjA0~&itmprp=enc%3AAQAKAAAA8FkggFvd1GGDu0w3yXCmi1ed%2FHn9qbTRWTwkMxm06VXUIriwQHSfJ1I50krNjUP4z6zSmhowMt0A6wfPsS0ae2OC1PTvBXOv1Pu0TCa1SlgpkDUqrF7nSYQUEbRis9afNjUTXhgx6ME5zSOqR2uZikTlLPaZQpdhCwEBrf9gBNYAFnI88gOSMS227VYxBeAkcPmh7MeuKWzmrv6GNFnNmj4%2F6kWPICmQxKhNwyNa8orx3kBwfuQHETSrryAuoYVglZHlR2S9%2FDmyvn--KhoPQQFZTur%2BZGHYYT4HRzuzgNjR1oStvn8%2FMW8DGGC7pYgyWw%3D%3D%7Ctkp%3ABk9SR8LQqJbUZQ).  
     - Powered via the Raspberry Pi’s USB port.  

4. **SD Card**  
   - A microSD card (8GB or larger) to flash the DreamPi software image.  

5. **Ethernet Cable**  
   - Required for connecting the Raspberry Pi to your router for a stable internet connection.  

---

### Optional
1. **CD-R Discs**  
   - Needed for burning custom software or patched game discs.  

2. **GDEMU or Similar Optical Drive Emulator**  
   - Enables loading games directly from an SD card, bypassing the need for discs.  

3. **Additional Accessories**  
   - VGA cable for improved video output (if supported by your setup).  

---

## Setup Guide

Follow these steps to set up DCNET on your Dreamcast and Raspberry Pi:

### Step 1: Download and Flash the DreamPi Image

1. Download the latest DreamPi image from the Dreamcast Live website:
   - For general Raspberry Pi models:  
     [DreamPi 1.9 DLE](https://dreamcastlive.net/files/DreamPi-1.9-DLE.zip)  
   - For Raspberry Pi 4:  
     [DreamPi 1.9 DLE for Pi4](https://dreamcastlive.net/files/DreamPi-1.9-DLE-Pi4.zip)

2. Flash the downloaded image to an SD card:
   - On **Mac**: Use [Balena Etcher](https://etcher.balena.io/).  
   - On **Windows**: Use [Win32 Disk Imager](https://dreamcastlive.net/files/win-32-disk-imager-1.0.zip).

3. Insert the SD card into your Raspberry Pi.

---

### Step 2: Connect and Power On the Raspberry Pi

1. Connect the following hardware to the Raspberry Pi:
   - **USB modem** (plugged into the Pi).  
   - **Line voltage inducer** (connected between the USB modem and the Dreamcast modem).  
   - **Ethernet cable** (from the Pi to your router).  

2. Power on the Raspberry Pi by connecting it to a power source.

---

### Step 3: Configure the Raspberry Pi for DCNET

1. **Connect to the Pi over SSH**:
   - On **Windows**: Use [PuTTY](https://www.putty.org/).  
   - On **Mac/Linux**: Use the built-in Terminal app.  

2. Find the Raspberry Pi’s IP address:
   - Check your router’s DHCP table for the Raspberry Pi’s MAC address.  
   - Ideally, set a **static IP reservation** in your router for the Pi to avoid its IP address changing.  

3. SSH into the Pi:
   - Use the following credentials to log in:
     ```
     ssh pi@<Raspberry Pi IP Address>
     ```
   - Default login credentials:
     - **Username**: `pi`  
     - **Password**: `raspberry`  

4. Change the default password for security:
   - After logging in, run:
     ```
     passwd
     ```
   - Follow the prompts to set a new password.

5. Install and enable DCNET:
   - Run the following commands:
     ```
     wget github.com/scrivanidc/dreampi_custom_scripts/raw/main/dcnet_on_off.sh
     chmod +x dcnet_on_off.sh
     ./dcnet_on_off.sh
     ```
   - When prompted, type `1` and press Enter to enable DCNET.

6. Your Raspberry Pi is now set up for DCNET.

---

### Step 4: Configure the Dreamcast

1. Download the Dreamcast Web Browser:
   - [XDP LE R4 Web Browser](https://dreamcastlive.net/files/xdp_le_r4.zip)

2. Use the browser to configure your Dreamcast’s internet settings:
   - **Dial-Up Number**: `111-1111`  
   - **Username**: Any custom value (e.g., your name).  
   - **Password**: Must be `password`.  
   - **DNS Settings**: Set both Primary and Secondary DNS to `0.0.0.0`.  

3. Save these settings to your VMU (Visual Memory Unit) and test the connection.

---

## Supported Games

DCNET currently supports the following games. See the table below for details on their online functionalities:

| Game Title                        | Genre               | Online Functionality Summary                                           |
|-----------------------------------|---------------------|------------------------------------------------------------------------|
| 4x4 EVO                           | Racing              | Online multiplayer off-road racing with customizable vehicles.         |
| Daytona USA 2001                  | Racing              | Online multiplayer arcade racing with classic tracks and vehicles.     |
| ChuChu Rocket!                    | Puzzle              | Online multiplayer gameplay where players guide mice into rockets.     |
| Planet Ring                       | Party               | Online minigames, including races, trivia, and cooperative challenges. |
| (Full list continues...)          |                     |                                                                        |

---

## Troubleshooting

If you encounter issues, check the following:

### Common Issues
1. **Dreamcast Fails to Connect**:
   - Verify your Dreamcast’s internet settings, especially the DNS and dial-up number.  
   - Ensure the Raspberry Pi is powered on and connected to the same network.

2. **Modem Not Detected**:
   - Confirm that the USB modem is compatible with DreamPi/DCNET.  
   - Check the line voltage inducer connections.

3. **Lag or Connection Drops**:
   - Use a stable wired Ethernet connection for the Raspberry Pi.  
   - Avoid heavy internet usage on your local network during gameplay.

---

## Credits and Acknowledgments

- **Original DreamPi Project**: Thanks to the creators for reviving Dreamcast online gaming.  
- **DCNET Contributors**: Special thanks to the contributors maintaining this fork.  
- **Dreamcast Community**: For keeping the spirit of Sega’s online gaming alive.

---

Ready to play? Set up your Dreamcast and relive the glory days of online gaming!
