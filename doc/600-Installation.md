# Installation

Stages:

* get an iso
* make sure it is complete and not corrupted
* make sure it is correctly signed
* install it on a bootable usb key
* boot the computer with it.

## Checking the download 

## Checking the media

### media built-in self test 

I see a report for 4.2.4 in qubes forum, indicating a "brief flash" of failed media test, followed by black screen ( https://forum.qubes-os.org/t/fatal-cd-check-failed/34286 )
From FranklyFlawless: try commands systemctl status checkisomd5@dev-sda.service and journalctl -xeu checkisomd5@dev-sda.service

## Booting from USB 

* Probably need to access the boot menu:
    * press f11 during boot to select boot device 
* if the key does not appear as a boot selection, it may be necessary to use F2, or Del key to enable usb key or uefi usb key.
* Legacy usb support may be necessary 
