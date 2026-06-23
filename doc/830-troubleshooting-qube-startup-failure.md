830-troubleshooting-qube-startup-failure.md

## A qube has failed to start : cannot connect to qrexec agent for 60 second, see var/log/xenconsole/guest

* When qubes tries to start a qube, it waits for a response indicating that the qube has started correctly.
* If no response comes before the timeout then an error is displayed
* First thing: look at the qube console fole indicated:
     * does it end with "JOB xxxxxxx Running"?
     * if yes, see "extend qrexec timeout"
* Often this happens due to long housekeeping
    task at startup
  * Often it is solved by a temporary increase     of the timeout.
    * see next:


* qrexec: increase the timeout
  *  using a command in Dom0 :
     `qvm-prefs <vmname> qrexec_timeout 3600`
   * start the qube again, tail -f the console logfile.
  * if the job succeeds, put the timeout back to default: ```qvm-prefs VMNAME -D``` and verify the template of your qube.
  * if still timeout: is it logical?

* typical long jobs:
  * this: Job qubes-rootfs-resize.service/start running (57s / no limit)
  * 


## is the failure for ALL qubes?

* Can you start a qube with no netvm=='' ?
  * For example, try ```Vault``` qube
  * Try your main template
  * Try the template of mgmt qubes
* if it is an appvm, try to start the template of the appvm.  same error?
   * yes: try to start different templates
* can you start sys-net? sys-whonix?

## all qubes fail to start 

What is the error message?

* "QUBESD_SOCKET"... qubesd not running?
*  qubesd not running
* lvm problems
* virt not enabled

* Check qube console for  ‘dependency failed’ errors, “qubes-db.service: Unable to locate executable ‘/usr/bin/qubesdb-daemon’: Permission denied”. 

    [quote="Atrate, post:3, topic:39501, full:true"][/quote]



* in `dom0` run: ```sudo systemctl status --failed```
* for each failed unit from that output, please run: 

``` sudo systemctl status UNITNAME```


## hardware does not support IOMMU/VT-d/AMD-Vi”

```
Failed to start an HVM qube with PCI devices assigned. hardware does not support IOMMU/VT-d/AMD-Vi”
```
* Possibly an error in BIOS configuration.
    * If the problem appeared suddenly, verify the age of the CMOS battery.


## qubesd

* journalctl -xeu qubesd
    
     https://forum.qubes-os.org/t/no-qubes-launch-after-booting-qubes-4-3-menu-doesnt-work-qubes-domains-doesnt-work/39501/9

* Check qube console for  ‘dependency failed’ errors, “qubes-db.service: Unable to locate executable ‘/usr/bin/qubesdb-daemon’: Permission denied”.
    * “SELINUX: Context system_u:object_r:qubes_qubesdb_daemon_exec_t:s0 is not valid (left unmapped).”
         * #dom0 ```qvm-features fedora-41-xfce-EXTRAS selinux 0``` to temporarily disable.

It appears

## Cannot set template to nonexistent qube

This should be impossible.

https://forum.qubes-os.org/t/no-qubes-launch-after-booting-qubes-4-3-menu-doesnt-work-qubes-domains-doesnt-work/39501/10

You can fix this issue by:
```
sudo systemctl stop qubesd
sudo cp /var/lib/qubes/qubes.xml /var/lib/qubes/qubes.xml.manual-bak
sudo nano /var/lib/qubes/qubes.xml
sudo systemctl start qubesd
```
When opening the editor, search for default-dvm-Fedora-43 entries and substitute it for another valid qube, which, I suppose, should be default-dvm.

# disposable 

# AppVM


# HVM

if has passed-through devices:

* Check logs (path?), look for:
* Wrong device

# Standalone

* trying to use kernel provided by Dom0

 # sys-usb fauls to start

 maybe:

[quote="SteveC, post:5, topic:42145"]
```
Jun 20 16:57:22 dom0 qvm-start[3868]: Error: Cannot connect to qrexec agent for 60 seconds, see /var/log/xen/console/guest-sys-usb.log for details
```
[/quote]

Make a copy of this file for each boot. Compare the good and bad ones... especially the last parts. You are either looking for error/fail/timeout/etc or for some long process that does not complete.

[quote="phceac, post:6, topic:42145"]
did you possibly keep your sys-usb from 4.2, and make a new one? If both are on AutoStart, then they will race to win the USB controller, but only one named"sys-usb" can be useful. So works/not works depends on who wins.

[added in edit…]
Another idea: if you see sys-usb runs until qrexec-timeout, is it doing some housekeeping? You can increase the timeout, so it gets to finish:

[quote="phceac, post:2, topic:37296"]
Try in a Dom0 terminal to run: `qvm-prefs $vm_name qrexec_timeout`

If the value is equal to the delay you see before the startup error then make the value longer: ` qvm-prefs $vm_name `
[/quote]

https://forum.qubes-os.org/t/cant-start-appvm-after-shutdown/37296/2

[quote="Tranquility, post:7, topic:42145"]
increasing the ram of the sys-usb qubes for about 50 MiB to 100. i had the same qrexec error
[/quote]


[quote="corny, post:10, topic:42145"]
cloning sys-usb and changing the kernel in advanced
[/quote]



 [quote="corny, post:10, topic:42145"]
issue where my usb 2.0 port combined with newer kernel gave autostart issues
[/quote]
* 


[quote="corny, post:10, topic:42145"]
addtl pci USB card if you have one
[/quote]








