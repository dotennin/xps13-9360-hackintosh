# xps13-9360-hackintosh with OpenCore

## Specs
|    CPU   |   GPU        |  RAM  | STORAGE |    DISPLAY    |
|:--------:|:------------:|:-----:|:-------:|:-------------:|
| i7-7550u | Intel HD 620 | 8 GB  |  256 GB |   1920x1080   |

## POST INSTALL
### Enable Retina / HiDPI scaled resolutions
1. Disable SIP mode in recovery mode `csrutil disable`(Catilina or higher)
2. Unlock file write lock `sudo mount -uw / && killall Finder`
3. Copy xps13 FHD solution plist: 
```
sudo defaults write /Library/Preferences/com.apple.windowserver.plist DisplayResolutionEnabled -bool true
```
2. Run this command: sudo cp ./POST_INSTALL/DisplayProductID-1449.plist /System/Library/Displays/Contents/Resources/Overrides/DisplayVendorID-4d10/DisplayProductID-1449
3. Reboot
4. Install RDM(https://github.com/avibrazil/RDM) app and select a resolution among the ones with a yellow lightning icon next to it.
5. Set RDM to autoboot in Preferences
6. Enable SIP mode in recovery mode (Catilina or higher)
### Hackintosh combojack support
1. put ComboJack_Installer/VerbStub.kext in Clover/kexts/Other
2. Run ComboJack_Installer/install.sh in terminal and reboot
3. Done. When you attach a headphone there will be a popup asking about headphone type.

