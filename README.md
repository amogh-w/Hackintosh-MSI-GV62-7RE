# Hackintosh MSI GV62 7RE

I have managed to successfully run Catalina 10.15.6 on my MSI GV62 7RE with OpenCore.

Note: Don't copy over my EFI and expect it to boot. Use it as a reference and build your own while referring to the dortania OpenCore Guide linked below. Have fun!

![opencore](https://github.com/acidanthera/OpenCorePkg/raw/master/Docs/Logos/OpenCore_with_text_Small.png)

## Resources:

- [r/Hackintosh](https://www.reddit.com/r/hackintosh/) - A subreddit to learn about Hackintosh-ing
- [OpenCore](https://github.com/acidanthera/OpenCorePkg/) - You can get the Custom Bootloader here
- [dortania OpenCore Guide](https://dortania.github.io/OpenCore-Install-Guide/) - Best guide available on the planet

![desktop](/screenshots/desktop.png)

## Kexts that I have used:

1. SMC: `VirtualSMC.kext`
2. Ethernet: `AtherosE2200Ethernet.kext`
3. USB: `USBInjectAll.kext`
4. Audio: `AppleALC.kext` with `Lilu.kext` companion
5. Graphics: `WhateverGreen.kext` with `Lilu.kext` companion
6. PS2 Controller: `VoodooPS2Controller.kext`

<details>
  <summary>Unneeded Clover Fixes</summary>

## Laptop Specific Fixes

**Laptop backlight control**
SSDT-PNLF.aml in ACPI/patched and AppleBacklightFixup.kext
https://www.tonymacx86.com/threads/guide-laptop-backlight-control-using-applebacklightfixup-kext.218222/

**Battery Status and Power Management**
ACPIBatteryManager.kext
https://www.tonymacx86.com/threads/guide-how-to-patch-dsdt-for-working-battery-status.116102/

**Audio**

```
<string>The following fixes may be needed for onboard audio/USB/etc</string>
<key>FixHPET</key>
<true/>
<key>FixIPIC</key>
<true/>
<key>FixRTC</key>
<true/>
<key>FixTMR</key>
<true/>

===

<key>PciRoot(0)/Pci(0x1f,3)</key>
<dict>
    <key>PinConfigurations</key>
    <data>
    </data>
    <key>hda-gfx</key>
    <string>onboard-1</string>
    <key>layout-id</key>
    <integer>99</integer>
    <key>no-controller-patch</key>
    <integer>1</integer>
```

**HDMI**

```
<key>framebuffer-con1-enable</key>
<integer>1</integer>
<key>framebuffer-con1-type</key>
<data>AAgAAA==</data>
```

**Disabling the Discrete GPU**
https://www.tonymacx86.com/threads/guide-disabling-discrete-graphics-in-dual-gpu-laptops.163772/

**DSDT Patches used**
https://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/

```
[syn] Fix ADBG Error     syntax/fix_ADBG.txt
[syn] Rename _DSM methods to XDSM     yntax/rename_DSM.txt
[sys] Fix _WAK Arg0 v2     system/system_WAK2.txt
[sys] HPET Fix     ystem/system_HPET.txt
[sys] SMBUS Fix     system/system_SMBUS.txt
[sys] IRQ Fix     system/system_IRQ.txt
[sys] RTC Fix     system/system_RTC.txt
[sys] OS Check Fix (Windows 10)     system/system_OSYS_win10.txt
[sys] Fix Mutex with non-zero SyncLevel     system/system_Mutex.txt
[usb] USB3 _PRW 0x6D (instant wake)     usb/usb_prw_0x6d_xhc.txt
[bat] MSI CX61 2PC     battery/battery_MSI-CX61-2PC.txt
[gfx0] Cleanup/Fix Errors (SSDT)     graphics/graphics_SSDT-disable-cleanup.txt
[gfx0] Disable from _REG (DSDT)     graphics/graphics_REG-disable.txt
[gfx0] Disable/Enable on _WAK/_PTS (DSDT)     graphics/graphics_PTS_WAK-disable.txt
```

</details>

## Disclaimer

I have not created any of the above kexts. I have just picked the kexts which were needed for my system and made the necessary changes to the `config.plist` to ensure that my system runs perfectly. Thank you, the wonderful Hackintosh Community! ❤️
