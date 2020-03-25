**Note: You're nothing but an a-hole if you sell EFI folder (config) that's readily available for free.** -- *stole this from mighil because it's right on*

If this helps you, thank [mighil](https://github.com/mighildotcom) since he did the hard work!

This is based on his [X79 Catalina guide](https://github.com/mighildotcom/X79-Hackintosh-Catalina). Before finding this I had a usable machine but performance wasn't great. I improved things a bit by switching to Virtual SMC and OcQuirks; the X79 guide took me the rest of the way (sans USB 3.0).

# Budget Dell Precision T3610 Xeon Build (~$250)

Clover EFI folder and `config.plist` required for a Dell Precision T3610 hackintosh running macOS Catalina 10.15.3.

![20200320_121001](https://user-images.githubusercontent.com/849044/77206086-17116c80-6aee-11ea-9084-9c27b42e7dae.jpg)

## System Specs

![Screen Shot 2020-03-20 at 12.11.07 PM.png](https://user-images.githubusercontent.com/849044/77206132-2f818700-6aee-11ea-9e46-8f005329db8c.png)

| Part        | Model Number
| ---         | ---
| CPU         | Xeon E5-2637 V2 @ 3.0 GHz (INCLUDE AppleIntelInfo.txt from darwindumper)
| Motherboard | Dell 09M8Y8 Revision 3
| BIOS        | A19
| Chipset     | Intel C602/X79
| Memory      | Micron 8GB DDR3-1333MHz Non-ECC x 4 (PN: 18KSF1G72PDZ-1G4E)
|             | Samsung 8GB DDR3-1333MHz Non-ECC x 4 (PN: M393B1K70DH0-CK0)
| GPU         | HP NVIDIA GK107GL Quadro K2000 2GB (ROM: v80.07.9b.00.07) - slot 1
| Storage     | PNY CS900 240GB SSD (Revision CS900J13)
| Bluetooth   | ASUS USB-BT400 (Firmware: v14 c4096)
| Ethernet    | Intel 82579LM (onboard)
| USB         | Renesas uPD720201 USB 3.0 Host Controller
| Sound       | Realtek ALC3220 (ALC280) (Layout ID: 3)
| Keyboard    | Microsoft Surface (connected via Bluetooth)
| Mouse       | Logitech M590 (connected using Logitech Unified receiver)
| Clover      | 5107

### BIOS Configuration

1. Reset to optimized defaults
2. Secure Boot disabled
3. Enable VT for Direct I/O disabled
4. Disks set to AHCI mode (default is RAID)
5. Fast Boot set to 'thorough'
6. CPU XD support enabled
7. TPM disabled

## Readme

- Read everything first and be careful
- Tested on macOS Catalina 10.15.3 (vanilla)

## Before You Proceed

You should modify the EFI (a lot) if your system specs are different. I use the settings for my motherboard. My system has a Renesas USB 3.0 controller which is a pain in the ass to get to work (have yet to figure that out but supposedly it's possible). Chances are you'll have a different CPU at the very least which may require some changes. If you're not using an NVIDIA GPU, expect a bunch of changes to be required, too.

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

- USB 3.0 (XHCI shows up in IOReg but requires work to get Renesas controller working)

## How to create a bootable macOS Catalina USB install drive? (on MacOS)

[Refer to this guide from 9to5mac](https://9to5mac.com/2019/06/27/how-to-create-a-bootable-macos-catalina-10-15-usb-install-drive-video/)
