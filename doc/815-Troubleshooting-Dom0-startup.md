815-Troubleshooting-Dom0-startup.md




systemd.unit=rescue.target



lvm vgrename vg01 vg0
lvm vgchange -ay
mount /dev/mapper/vg0-qubes-root /sysroot


# Display is dark
* Change of display connections
    * (https://forum.qubes-os.org/t/boot-from-degraded-raid-1-lvm-issue-vg0-renamed-to-vg01/36181/3):
     “nouveau” driver that decided it was time to fully disable both displays. Fixed after disconnecting one of them. For some reason I didn’t see this issue before my NVMe died. So I didn’t see anything on the screen without nomodeset flag after load

## Really deep and low level TS 

### Dom0 and xen console over Serial, USB, network 
https://forum.qubes-os.org/t/getting-a-serial-console-on-usb-only-qubes-laptop/4662/2
