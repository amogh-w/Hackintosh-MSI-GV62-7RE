# Hackintosh MSI GV62 7RE

I have managed to successfully run macOS Monterey 12.0.1 (21A559) on my MSI GV62 7RE with OpenCore.

Note: Don't copy over my EFI and expect it to boot. Use it as a reference and build your own while referring to the dortania OpenCore Guide linked below. Have fun!

![opencore](https://github.com/acidanthera/OpenCorePkg/raw/master/Docs/Logos/OpenCore_with_text_Small.png)

## Resources:

- [r/Hackintosh](https://www.reddit.com/r/hackintosh/) - A subreddit to learn about Hackintosh-ing
- [OpenCore](https://github.com/acidanthera/OpenCorePkg/) - You can get the Custom Bootloader here
- [dortania OpenCore Guide](https://dortania.github.io/OpenCore-Install-Guide/) - Best guide available on the planet

![desktop](/screenshots/desktop.png)

## Bios

In BIOS, holding **ALT + RIGHT-CTRL + SHIFT** together then press **F2**

| Settings                      |         |
| ----------------------------- | ------- |
| Fast Boot                     | Disable |
| Secure Boot                   | Disable |
| `Intel Speed Shift`(aka. HWP) | Enable  |
| `CFG Lock`                    | Disable |
| DVMT Pre-Allocated            | 64M     |
| `CSM`                         | Disable |
| Enable Hiberation             | Disable |

<pre>
[Advanced] Tab
├─ Power & Performance
│  └─ CPU-Power Management Control
│     ├─ <b>Intel(R) Speed Shift Technology</b>
│     └─ CPU Lock Configuration
│        └─ <b>CFG Lock</b>
├─ System Agent (SA) Configuration
│  └─ Graphics Configuration
│     └─ DVMT Pre-Allocated
├─ CSM Configuration
│  └─ <b>CSM Support</b>
└─ ACPI Settings
   └─ <b>Enable Hibernation</b>
</pre>

[Source](https://github.com/jbwharris/hackintosh-msi-GL72M-7RDX)

## Kexts that I have used:

1. AirportItlwm.kext
2. AppleALC.kext
3. AtherosE2200Ethernet.kext
4. BrightnessKeys.kext
5. IntelBluetoothFirmware.kext (disabled)
6. IntelBluetoothInjector.kext (disabled)
7. Lilu.kext
8. NVMeFix.kext
9. SMCBatteryManager.kext
10. SMCProcessor.kext
11. SMCSuperIO.kext
12. USBInjectAll.kext
13. VirtualSMC.kext
14. VoodooPS2Controller.kext
15. WhateverGreen.kext

## Disclaimer

I have not created any of the above kexts. I have just picked the kexts which were needed for my system and made the necessary changes to the `config.plist` to ensure that my system runs perfectly. Thank you, the wonderful Hackintosh Community! ❤️
