# xps13-9360-hackintosh with OpenCore

## Specs
|    CPU   |   GPU        |  RAM  | STORAGE |    DISPLAY    |
|:--------:|:------------:|:-----:|:-------:|:-------------:|
| i7-7550u | Intel HD 620 | 8 GB  |  256 GB |   1920x1080   |

## Enable Retina / HiDPI scaled resolutions
1. Enable HiDPI mode: 
```sudo defaults write /Library/Preferences/com.apple.windowserver.plist DisplayResolutionEnabled -bool true
```
2. Run this command: sudo cp ./POST_INSTALL/DisplayProductID-1449.plist /System/Library/Displays/Contents/Resources/Overrides/DisplayVendorID-4d10/DisplayProductID-1449
3. Reboot
4. Install RDM(https://github.com/avibrazil/RDM) app and select a resolution among the ones with a yellow lightning icon next to it.
5. set RDM to autoboot in Preferences
