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
[NVMeFix](https://github.com/acidanthera/NVMeFix/releases)|Used for fixing power management and initialization on non-Apple NVMe.
[RestrictEvents](https://github.com/acidanthera/RestrictEvents/releases)|Better experience with unsupported processors like AMD, Disable MacPro7,1 memory warnings and provide upgrade to macOS Monterey via Software Updates when available.
[CpuTscSync](https://github.com/acidanthera/CpuTscSync/releases)|It is a Lilu plugin, combining functionality of VoodooTSCSync and disabling xcpm_urgency if TSC is not in sync. It should solve some kernel panics after wake.
[USBWakeFixup](https://github.com/osy/USBWakeFixup)|This extension is a workaround for that issue by creating a fake ACPI device with the right wakeup params.
USBMap|Kext generated after mapping the USB ports

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
