# ASUS ZENBOOK
Clover hotpatches and tools for the Asus Zenbook laptop on macOS 10.13.6. 

#### Supported models:

* UX410
* UX430

#### What you should expect works

* Audio
* Keyboard
* Trackpad
* Battery
* Fn-keys
* Brightness
* Sleep
* HDMI

#### Will never work

* Factory Intel WiFi card.

## Basic Instruction

### 1. BIOS Settings

* Activate Advanced Mode
* Set DVMT to 64M
* Disable Secure Boot

### 2. Preparing USB

* Follow this [guide](https://www.tonymacx86.com/threads/guide-booting-the-os-x-installer-on-laptops-with-clover.148093/)
* For the drivers, don't forget AptioMemoryFix.efi, ApfsDriverLoader.efi, HFSPlus.efi

### 3. Post Installation

* Install Clover UEFI as described in the guide linked by the previous section.
* In Terminal:
```
mkdir ~/hackintosh
cd ~/hackintosh
git clone https://github.com/hieplpvip/ASUS-ZENBOOK-HACKINTOSH.git zenbook
cd zenbook
sudo ./download.sh && sudo ./install_downloads.sh
sudo ./make_acpi.sh && sudo ./install_acpi.sh
```

## Notes
- Trackpad: VoodooI2C has two modes: GPIO pinning and polling. For better performance, GPIO pinning mode should be used. However, ASUS laptops (UX410, UX430, etc) have problems with GPIO pinning. Therefore, polling mode is used. New ASUS laptops seem to fix this. If you want to test, compile SSDT-ELAN with your custom pin (follow [this guide](https://voodooi2c.github.io/#GPIO%20Pinning/GPIO%20Pinning) to know) and enable these 2 patch in config.plist: "change Method(_STA,0,NS) in GPI0 to XSTA" and "change Method(_CRS,0,S) in ETPD to XCRS".
- SSDT-UIAC is made specially for my laptop. On yours USB ports may be different. See [this guide](https://www.tonymacx86.com/threads/guide-creating-a-custom-ssdt-for-usbinjectall-kext.211311/) for how to create one for yours.

## WIP

* [VoodooI2C](https://github.com/hieplpvip/VoodooI2C/tree/native)
* [AsusFnKeys](https://github.com/hieplpvip/AsusFnKeys)

## To-Do

* Bluetooth & WiFi (just need to replace Intel card with DW1560, but I don't have money now :(( )
* Create automatic scripts
* Post a full guide on Tonymacx86
* CREATE A BUILD THAT WORKS FOR ALL ZENBOOKS (far future)

## Credits

@gulios (see https://www.tonymacx86.com/threads/asus-ux430ua-kaby-lake-intel-hd-graphics-620.225847) 

@Shinji3rd (see https://www.tonymacx86.com/threads/guide-asus-zenbook-ux310uak-macos-sierra-installation-guide.224591)

@alexandred for the the touchpad driver.

@RehabMan for everything else

## [Donate me](https://paypal.me/hieplpvip)
Any donation is highly appreciated
