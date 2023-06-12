# HACKINTOSH-EFI-INTEL-13TH-13600K-B760M-DDR5-RX5700XT

>⛓ [Link to the original repository](https://github.com/luchina-gabriel/BASE-EFI-INTEL-DESKTOP-13THGEN-RAPTOR-LAKE)

>🔧 _Based on Opencore 0.9.2_

> 🖥️ SmBIOS - iMacPro1,1

This EFI was developed for the following hardware:
- **CPU**: Intel Core i5 13th - 13600k
- **Mainboard**: Gigabyte B760M Aorus Elite DDR5 (rev. 1.0)
- **GPU**: AMD Radeon RX5700 XT - 8GB (Asus TUF)
- **Memory**: XPG Lancer DDR5@5200 MHz - (2x16Gb) 
- **Wireless Card**: Fenvi t919 (bcm94360)
- **Storage**: KingSpec NMVE NE2280 PCIe Gen3 x4

## Features
- [x] USB Map
- [x] Custom ACPI Tables
- [x] Boot Shine
- [x] Built-in Network cards
- [x] Built-in Sound cards
- [x] CPU Name
- [x] GPU Name
- [ ] Sleep crashs ``in Progress``

## Kexts used (included)
Kext|Description
:----|:----
[Lilu.kext](https://github.com/acidanthera/Lilu/releases)|Patch many processes, required for AppleALC, WhateverGreen, VirtualSMC and many other kexts.
[SMCProcessor.kext](https://github.com/acidanthera/VirtualSMC/releases)|Used for monitoring CPU temperature, doesn't work on AMD CPU based systems.
[SMCSuperIO.kext](https://github.com/acidanthera/VirtualSMC/releases)|Used for monitoring fan speed, doesn't work on AMD CPU based systems.
[VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases)|Emulates the SMC chip found on real macs, without this macOS will not boot.<br>Alternative is FakeSMC which can have better or worse support, most commonly used on legacy hardware.
[WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)|Used for graphics patching, DRM fixes, board ID checks, framebuffer fixes, etc; all GPUs benefit from this kext.
[AppleALC.kext](https://github.com/acidanthera/AppleALC/releases)|Used for AppleHDA patching, allowing support for the majority of on-board sound controllers.<br>AMD 15h/16h may have issues with this and Ryzen/Threadripper systems rarely have mic support.
[LucyRTL8125Ethernet.kext](https://www.insanelymac.com/forum/files/file/1004-lucyrtl8125ethernet/)|For Realtek's 2.5Gb Ethernet.
[NVMeFix.kext](https://github.com/acidanthera/NVMeFix/releases)|Used for fixing power management and initialization on non-Apple NVMe.
[RestrictEvents.kext](https://github.com/acidanthera/RestrictEvents/releases)|Better experience with unsupported processors like AMD, Disable MacPro7,1 memory warnings and provide upgrade to macOS Monterey via Software Updates when available.
[CpuTscSync.kext](https://github.com/acidanthera/CpuTscSync/releases)|It is a Lilu plugin, combining functionality of VoodooTSCSync and disabling xcpm_urgency if TSC is not in sync. It should solve some kernel panics after wake.
[USBWakeFixup.kext](https://github.com/osy/USBWakeFixup)|This extension is a workaround for that issue by creating a fake ACPI device with the right wakeup params.
USBMap.kext|Kext generated after mapping the USB ports

## Tools

Tool|Description
:----|:----
[ProperTree](https://github.com/corpnewt/ProperTree) | Configure config.plist
[USBMap](https://github.com/corpnewt/USBMap) | Making the USB Map
[gibMacOS](https://github.com/corpnewt/gibMacOS) | Download and create macOS images
[SSDTTime](https://github.com/corpnewt/SSDTTime) | M ake creating SSDTs simple
[CPU-Name](https://github.com/corpnewt/CPU-Name) | Fix the cpu name
[MountEFI](https://github.com/corpnewt/MountEFI) | Shortcut to Mount the EFI Driver
[gibMacRecovery](https://github.com/corpnewt/gibMacRecovery) | Download and create macOS recoverys
[gebSMBIOS](https://github.com/corpnewt/GenSMBIOS) | Generate information from SMBIOS
[IORegistryExplorer](https://github.com/vulgo/IORegistryExplorer) | Validate information regarding hardware power management
[iASL](https://www.acpica.org/downloads) | Change and convert SSDTs (for Windows)
[Mac iASL](https://github.com/acidanthera/MaciASL) | Change and convert SSDTs (for MAC)
[OpenCore-Packager](https://github.com/chris1111/OpenCore-Packager) | Tool that assists in the installation of the EFI in a simple way

## Softwares

- [Stats](https://github.com/exelban/stats)
- [Hackintool](https://github.com/benbaker76/Hackintool)

## BIOS Settings
> Bios Version: **F11a**
* **Tweaker**
  * Advanced CPU Settings
    * Hyper Threading Technology - ``Enabled``
* **Settings**
  * Plataform Power
    * PEG ASPM - ``Enabled``
    * PCH APSM - ``Enabled``
    * DMI ASPM - ``Enabled``
    * Native ASPM - ``Enabled``
    * Power Loading - ``Enabled``
  * IO Ports
    * Internal Graphics - ``Disabled``
    * Above 4G Decoding - ``Enabled``
    * Above 4GB MMIO Bios Assignment - ``Enabled``
    * Re-Size Bar Support - ``Disabled``
    * USB Configuration
      * XHCI Hand-Off - ``Enabled``
    * VMD Setup Menu
      * VMD Controller - ``Disabled``
  * **Miscellaneous**
    * Intel Plataform Trust Technology (PTT) - ``Enabled``
    * VT-d - ``Enabled``
* **Boot**
  * CFG Look - ``Disabled``
  * Fast boot - ``Enabled``
  * Windows 10 Features - ``Windows 10``
  * CSM Support - ``Enabled``

## Useful Links
- [Dortania Getting Started](https://dortania.github.io/getting-started/)
- [Dortania Troubleshooting](https://dortania.github.io/troubleshooting/)
- [Dortania Post Install](https://dortania.github.io/OpenCore-Post-Install/)
- [Dortania Documentation](https://dortania.github.io/docs/)
