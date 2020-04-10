**Note: You're nothing but an a-hole if you sell EFI folder (config) that's readily available for free.** -- *stole this from mighil because it's right on*

If this helps you, thank [mighil](https://github.com/mighildotcom) since he did the hard work!

This is based on his [X79 Catalina guide](https://github.com/mighildotcom/X79-Hackintosh-Catalina). Before finding this I had a usable machine but performance wasn't great. I improved things a bit by switching to Virtual SMC and OcQuirks; the X79 guide took me the rest of the way (sans USB 3.0).

# Budget Dell Precision T3610 Xeon Build (~$350)

Clover EFI folder and `config.plist` required for a Dell Precision T3610 hackintosh running macOS Catalina 10.15.4.

![20200320_121001](https://user-images.githubusercontent.com/849044/77206086-17116c80-6aee-11ea-9084-9c27b42e7dae.jpg)

## System Specs

![Screen Shot 2020-04-10 at 12.06.53 PM](https://user-images.githubusercontent.com/849044/79016528-1df73200-7b24-11ea-88cf-55a20f674056.png)

| Part        | Model Number
| ---         | ---
| CPU         | Xeon E5-2637 V2 @ 3.0 GHz (INCLUDE AppleIntelInfo.txt from darwindumper)
| PSU         | ~~Dell 80+ Gold 425W~~
|             | Dell 80+ Gold 685W
| Motherboard | Dell 09M8Y8 Revision 3
| BIOS        | A19
| Chipset     | Intel C602/X79
| Memory      | Micron 8GB DDR3-1333MHz Non-ECC x 4 (PN: 18KSF1G72PDZ-1G4E)
|             | Samsung 8GB DDR3-1333MHz Non-ECC x 4 (PN: M393B1K70DH0-CK0)
| GPU         | ~~HP NVIDIA GK107GL Quadro K2000 2GB (ROM: v80.07.9b.00.07) - slot 1~~
|             | MSI RX 570 GAMING X 8GB - slot 1
| Storage     | PNY CS900 240GB SSD (Revision CS900J13) x2
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
3. Enable VT for Direct I/O disabled (Virtualization Support can be enabled if you need it for Docker, etc)
4. Disks set to AHCI mode (default is RAID)
5. Fast Boot set to 'thorough'
6. CPU XD support enabled
7. TPM disabled
8. Legacy ROM disabled (required for the Quadro but not for the Radeon)

## Readme

- Read everything first and be careful
- Tested on macOS Catalina 10.15.4 (vanilla)

## Differences from the X79 guide

- VirtualSMC
- OCQuirks

## Before You Proceed

You should modify the EFI (a lot) if your system specs are different. I use the settings for my motherboard. My system has a Renesas USB 3.0 controller which is a pain in the ass to get to work (have yet to figure that out but supposedly it's possible). Chances are you'll have a different CPU at the very least which may require some changes. If you're not using an NVIDIA GPU, expect a bunch of changes to be required, too.

## What Does Work

- App Store
- iMessage (works after SMBIOS edits)
- Quicktime (including screen recording)
- ethernet (onboard)
- bluetooth (added via USB dongle)
- GPU
- sound (Intel HDA and ~~NVIDIA~~ Radeon HDMI)
- 4k display
- Docker

## macOS Updates

- 10.15.3 -> 10.15.4 worked without any issues

## What Doesn't Work

- USB 3.0 (XHCI shows up in IOReg but requires work to get Renesas controller working)

## How to create a bootable macOS Catalina USB install drive? (on MacOS)

[Refer to this guide from 9to5mac](https://9to5mac.com/2019/06/27/how-to-create-a-bootable-macos-catalina-10-15-usb-install-drive-video/)


## RX 570 Installation Gotchas

- It's not likely to work if you have the 425W PSU, so make sure to upgrade to the 685W version at least. I paid $20 for the 685W PSU upgrade and the 8-pin PCI express power cable together at a local surplus dealer.
- The side panel won't close until you remove the brace with the rubber strip beneath the latch mechanism.
- You'll probably want to get a PCI express GPU power cable with a 90 degree plug so you have more clearance between the side panel and the cable.
- You'll either need to get the OEM Dell GPU power cable from the T76XX series or if you're like me (single CPU motherboard in the dual CPU case) then you can use an EPS to PCI express cable to power the GPU. I used the 8-pin to 8-pin OEM Dell cable but also bought a Supermicro EPS to 8-pin PCI express GPU cable just in case.
- If you used legacy mode in your BIOS for a Quadro, switching it to UEFI-only makes things look better with the Radeon.
