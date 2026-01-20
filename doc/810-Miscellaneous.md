# Miscellaneous

* livecd: add rd.live.check  to vmlinuz line.

Troubleshooting Dom0 kernel

* increase/decrease number of retined kernels : installonly_limit=3 (in /etc/dnf/dnf.conf )
* (old) https://forum.qubes-os.org/t/qubes-users-qubes-update-how-to-hold-an-old-kernel/11909/10



## Transfer or duplicate to another computer 

See [https://www.qubes-os.org/doc/how-to-back-up-restore-and-migrate/]

* Before you re-use the disk of original installation, make sure to verify that all data are backed up. see note on **Verify backup integrity, do not restore the data**
* Make sure that Qubes is running correctly on the new machine before
    you try to restore any data.
* If the hardware is not identical, do not restore the qubes with PCI
    devices, or make sure to verify that the assignments are correct.

## misc 4.3 related 

* https://forum.qubes-os.org/t/r4-3-rc2-sys-usb-stopped-working-after-dist-upgrade/36410/
