# HACKINTOSH-EFI-INTEL-13TH-13600K-B760M-DDR5-RX5700XT

>⚠️ **In Development** ⚠️

>⛓ [Link to the original repository](https://github.com/luchina-gabriel/BASE-EFI-INTEL-DESKTOP-13THGEN-RAPTOR-LAKE)

>🔧 _Based on Opencore 0.9.2_

> 🖥️ SmBIOS - MacPro7,1

This EFI was developed for the following hardware:
- **CPU**: Intel Core i5 13th - 13600k
- **Mainboard**: Gigabyte B760M Aorus Elite DDR5 (rev. 1.0)
- **GPU**: AMD Radeon RX5700 XT - 8GB (Asus TUF)
- **Memory**: XPG Lancer DDR5@5200 MHz - (2x16Gb) 
- **Wireless Card**: Fenvi t919 (bcm94360)
- **Storage**: KingSpec NMVE NE2280 PCIe Gen3 x4

## Basic Steps

## Kexts used (included)

## Boot Args used

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
