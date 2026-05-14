815-Troubleshooting-Dom0-startup.md


# Todo For filing

systemd.unit=rescue.target



lvm vgrename vg01 vg0
lvm vgchange -ay
mount /dev/mapper/vg0-qubes-root /sysroot

# Failure to boot Dom0

* Bad or incomplete update:
* Forgotten user password
* systemd failure
* graphics unavailable, no console
* end up at a rescue prompt, but did not set a root password in Dom0
     * e.g. ```Failed to mount boot-efi.mount - /boot/efi
Dependency failed for local-fs.target - Local File System```
    * Some other prompt like: ```Press Enter for maintenance (or press Control-D to continue):```
         
* 
* ...

Solutions


    

* May need something like this ( cite: [mellowpoison](https://forum.qubes-os.org/t/forgot-user-password-no-encryption/36566/2) ):
    * Boot another linux from a USB key
    * [mount Qubes from another OS](https://doc.qubes-os.org/en/latest/user/advanced-topics/mount-from-other-os.html)
    *  [Arch instructions](https://wiki.archlinux.org/title/Chroot#Using_chroot)
    *  Then try to fix the cause.

# Display is dark
* Change of display connections
    * (https://forum.qubes-os.org/t/boot-from-degraded-raid-1-lvm-issue-vg0-renamed-to-vg01/36181/3):
     “nouveau” driver that decided it was time to fully disable both displays. Fixed after disconnecting one of them. For some reason I didn’t see this issue before my NVMe died. So I didn’t see anything on the screen without nomodeset flag after load

## Really deep and low level TS 

### Dom0 and xen console over Serial, USB, network 
https://forum.qubes-os.org/t/getting-a-serial-console-on-usb-only-qubes-laptop/4662/2
