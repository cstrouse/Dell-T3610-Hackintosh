**Note: You're nothing but an a-hole if you sell EFI folder (config) that's readily available for free.** -- *stole this from mighil because it's right on*

If this helps you, thank [mighil](https://github.com/mighildotcom) since he did the hard work!

This is based on his [X79 Catalina guide](https://github.com/mighildotcom/X79-Hackintosh-Catalina). Before finding this I had a usable machine but performance wasn't great. I improved things a bit by switching to Virtual SMC and OcQuirks; the X79 guide took me the rest of the way (sans USB 3.0).

# Budget Dell Precision T3610 Xeon Build (~$250)

Clover EFI folder and `config.plist` required for a Dell Precision T3610 hackintosh running macOS Catalina 10.15.3.

![20200320_121001.jpg](:/f376740df62046aeaa33ec76d3cc3f72)

## System Specs

![Screen Shot 2020-03-20 at 12.11.07 PM.png](:/0422a486fac4410295201322c0355091)

| Part        | Model Number
| ---         | ---
| CPU         | Xeon E5-2637 V2 (INCLUDE AppleIntelInfo.txt from darwindumper)
| Motherboard | Dell 
| BIOS        | A19
| Chipset     | Intel C602/X79
| Memory      | Micron 8GB DDR3-1333MHz Non-ECC x 4 (PN: 18KSF1G72PDZ-1G4E)
|             | Samsung 8GB DDR3-1333MHz Non-ECC x 4 (PN: M393B1K70DH0-CK0)
| GPU         | HP NVIDIA GK107GL Quadro K2000 2GB (ROM: v80.07.9b.00.07) - slot 1
| Storage     | PNY CS900 240GB SSD (Revision CS900J13)
| Bluetooth   | ASUS USB-BT400 (Firmware: v14 c4096)
| Ethernet    | Intel 82579LM (onboard)
| USB         | Renesas uPD720201 USB 3.0 Host Controller
| Sound       | Realtek ALC280 (Layout ID: 3)
| Keyboard    | Microsoft Surface (connected via Bluetooth)
| Mouse       | Logitech M590 (connected using Logitech Unified receiver)
| Clover      | 5105

### BIOS Configuration

- Secure Boot disabled
- VT-D disabled
- Disks set to AHCI mode (default is RAID)
- Fast Boot set to _?_
- Serial port disabled

## Readme

- Read everything first and be careful
- Tested on macOS Catalina 10.15.3 (vanilla)

## Before You Proceed

You should modify the EFI (a lot) if your system specs are different. I use the settings for my motherboard. My system has a Renesas USB 3.0 controller which is a pain in the ass to get to work (have yet to figure that out but supposedly it's possible). Chances are you'll have a different CPU at the very least which may require some changes. If you're not using an NVIDIA GPU, expect a bunch of changes to be required, too.

## BIOS Settings

## What Does Work

- App Store
- iMessage (works after SMBIOS edits)
- Quicktime (including screen recording)
- ethernet (onboard)
- bluetooth (added via USB dongle)
- GPU
- sound (Intel HDA and NVIDIA HDMI)
- 4k display

## What Doesn't Work

- USB 3.0 (XHCI shows up in IOReg but don't havea USB 3.0 device to test)
- Turbo Boost (needs work)
- CPU Frequency Scaling (needs work)

## How to create a bootable macOS Catalina USB install drive? (on MacOS)

[Refer to this guide from 9to5mac](https://9to5mac.com/2019/06/27/how-to-create-a-bootable-macos-catalina-10-15-usb-install-drive-video/)
