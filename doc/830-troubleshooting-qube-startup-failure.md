830-troubleshooting-qube-startup-failure.md

## A qube has failed to start : cannot connect to qrexec agent for 60 second, see var/log/xenconsole/guest

* When qubes tries to start a qube, it waits for a response indicating that the qube has started correctly.
* If no response comes before the timeout then an error is displayed
* Often this happens due to long housekeeping
    task at startup
  * Often it is solved by a temporary increase     of the timeout.
    * in dom0, qvm-prefs ??

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
