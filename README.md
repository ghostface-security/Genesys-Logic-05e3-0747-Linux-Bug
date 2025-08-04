# SD Card Reader Workaround on Linux

This repository documents a specific hardware-to-software incompatibility where certain SD card readers fail to function on Linux distributions. It outlines a working solution using USB-C adapters and provides a place for others to share affected hardware and system configurations.
1. The Problem

SD cards fail to mount or appear as a device when using a standard USB-A card reader on various Linux distributions. This issue has been observed on different Linux systems (including BlackArch, Kali, and Ubuntu) on specific laptop hardware. The lsusb output for the problematic reader shows no device is detected unless an SD card is physically inserted into the reader.

Affected Hardware:

    Laptop Model: HP Laptop 14

    Operating System: BlackArch Linux

    Kernel: Linux 6.15.9-arch1-1

    Problematic Card Reader: Genesys Logic, Inc. USB Storage (ID 05e3:0747)

2. The Workaround

The issue can be bypassed by using a USB-C port, which is handled by a different USB controller and driver.

    Obtain a USB-C card reader or a USB-C adapter (like the one used for a Samsung phone).

    Connect the adapter and SD card to a USB-C port on the laptop.

    The SD card should now be recognized and mounted correctly.

3. The Technical Explanation

The lsusb command shows the problematic card reader is only detected on a specific USB bus (Bus 004) and only when an SD card is present in the reader. When a different USB port and a USB-C adapter are used, the same device is detected on a different USB bus (Bus 001), confirming that the issue is a driver or controller incompatibility. The USB-C path bypasses the problematic USB-A driver, allowing the card to be read.
4. Testing and Logs

The following files contain the lsusb output from different stages of testing, providing concrete evidence of the behavior described above. These logs were collected on the affected hardware and have been added to this repository for review.

    Linux-Bug-Testing/sdcard-reader-removed.txt: lsusb output with no card reader connected.

    Linux-Bug-Testing/sdcard-reader-inserted-without-sdcard.txt: lsusb output with the USB-A card reader connected, but no SD card inserted.

    Linux-Bug-Testing/sdcard-reader-inserted-with-sdcard.txt: lsusb output with the USB-A card reader connected and an SD card inserted.

    Linux-Bug-Testing/sdcard-reader-inserted-with-adapter.txt: lsusb output with the USB-A card reader connected to a USB-C port via an adapter and an SD card inserted.

5. Contributing

If you are experiencing a similar issue and this workaround works for you, please contribute to this project by adding your hardware information to the list below.

    Laptop Model:

    OS:

    Problematic Card Reader:

    Working Solution:
