# Installation

Stages:

* get an iso
* make sure it is complete and not corrupted
* make sure it is correctly signed
* install it on a bootable usb key
* boot the computer with it.
* Choose language(s), keyboard layout, select destination disk & other setup
* Begin installation - It will install Dom0, and then ask for reboot
* Reboot, and start from destination disk
* After reboot, Initial Setup should run, and allow to choose templates and initial qubes.

## Verify system requirements

* https://www.qubes-os.org/doc/system-requirements/
* 

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



# Installation Troubleshooting

* media problems
* initial boot failure


If the installation shows unexpected failures, first of all:

* Verify the downloaded ISO file : https://www.qubes-os.org/security/verifying-signatures/#how-to-verify-the-cryptographic-hash-values-of-qubes-isos
* Verify the ISO after writing to the media:  https://www.qubes-os.org/security/verifying-signatures/#how-to-re-verify-installation-media-after-writing
* If they are both correct, then read on.



## Initial setup failure

Initial setup is done by initial-setup-graphical

*    /usr/libexec/initial-setup/initial-setup-graphical
*    /usr/libexec/initial-setup/initial-setup-text
* If the setup fails, or is incomplete, then it may be possible to start the script manually.
* Seen here: https://forum.qubes-os.org/t/docs-should-mention-initial-setup/29461

### Qubes initial configuration failed.

* Error message : "Qubes initial configuration failed. Login to the system and check /var/log/salt/minion for details. You can retry configuration by calling 'sudo qubesctl --all state.highstate' in dom0 (you will get detailed state there)."
* suspect bad media
* Seen here: https://forum.qubes-os.org/t/qubes-4-2-initial-configuration-failed/24168
  


