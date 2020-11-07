# xps13-9360-hackintosh with OpenCore

## Specs
|    CPU   |   GPU        |  RAM  | STORAGE |    DISPLAY    |
|:--------:|:------------:|:-----:|:-------:|:-------------:|
| i7-7550u | Intel HD 620 | 8 GB  |  256 GB |   1920x1080   |

## Results to expect
### Working:
- CPU power management [909|1941 GeekBench5 score]
- GPU Power management [4587|4015 GeekBench5 OpenCL|Metal score]
- Sleep/wake [no hibernate mode]
- Shutdown
- Webcam with LED on-off switching properly working
- Microphones
- Speakers
- Headphone jack (with jack sense)
- Touchpad with semi-advanced multitouch gestures
- USB A 3.0 ports
- USB C 3.1 port (no hotplug)
- Prev/Play/Next keys
- Volume keys with OSD
- Brightness slider and OSD
- Brightness keys with smooth and full range of brightness + level persistence after reboot
- Keyboard backlighting with keyboard activation key and with custom timeout
- Wifi 2.4GHz + 5GHz as native AirPort (AC-7265 swap)
- Bluetooth
- Perfect-match keyboard layout (for USA-Intl keyboards) via custom keyboard layout
- Battery / AC status
- NVME SSD with native Trim
- USB-A high-current output (1A max on the left, 2.4A max on the right)
- Retina / HiDPI scaled resolutions
- USB-C Power Delivery battery charging (20V@1.5A minimum)

### Not working
- Airdrop (not confirmed)
- External HDMI video+audio output

## UEFI Variables
DVMT.efi can be launched from OpenCore
|Variable|Offset|Default value|Desired value|Comment|
|:------:|:------:|:------:|:------:|:------:|
|CFG Lock|	0x4de	|0x01 (Enabled)|	0x00 (Disabled)|	Disable CFG Lock to prevent MSR 0x02 errors on boot setup_var 0x4de 0x00|
|DVMT Pre-allocation	|0x785	|0x01 (32M)|	0x02 (64M)|	Increase DVMT pre-allocated size to 64M setup_var 0x785 0x02|
|DVMT Total Gfx Memory	|0x786|	0x02 (???M)|	0x03 (MAX)|	Increase total gfx memory limit to maximum setup_var 0x786 0x03|


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
4. Enable SIP mode in recovery mode (Catilina or higher)
5. Run the following command this enable macOS HiDPI: 
```
sudo bash -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"
```
### Hackintosh combojack support
1. put ComboJack_Installer/VerbStub.kext in Clover/kexts/Other
2. Run ComboJack_Installer/install.sh in terminal and reboot
3. Done. When you attach a headphone there will be a popup asking about headphone type.

## Credits
- [Dell XPS 13 9360 on MacOS Sierra 10.12.x - LTS (Long-Term Support) Guide](https://www.tonymacx86.com/threads/guide-dell-xps-13-9360-on-macos-sierra-10-12-x-lts-long-term-support-guide.213141/)
- [one-key-hidpi](https://github.com/xzhih/one-key-hidpi)
- [XPS9360-macOS](https://github.com/the-darkvoid/XPS9360-macOS)
