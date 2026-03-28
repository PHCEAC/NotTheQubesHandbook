830-troubleshooting-qube-startup-failure.md

## A qube has failed to start : cannot connect to qrexec agent for 60 second, see var/log/xenconsole/guest

* When qubes tries to start a qube, it waits for a response indicating that the qube has started correctly.
* If no response comes before the timeout then an error is displayed
* Normally happens due to long housekeeping
    task at startup
* Often it is solved by a temporary increase of the timeout.
    * qvm-pref??

## is the failure for ALL qubes?

* Can you start a qube with netvm=='' ?
     * For example, try ```Vault``` qube
    * Try your main template
    * Try template of mgmt qubes

## all qubes fail to start 

What is the error message?

* "QUBESD_SOCKET"... qubesd not running?
*  qubesd not running
* lvm problems
* virt not enabled

[quote="Atrate, post:3, topic:39501, full:true"]
Please paste the output of running

```
sudo systemctl status --failed
```

in `dom0`. Also, for each failed unit from that output, please run

```
sudo systemctl status UNITNAME
```

and paste the output here.
[/quote]

## hardware does not support IOMMU/VT-d/AMD-Vi”

```
Failed to start an HVM qube with PCI devices assigned. hardware does not support IOMMU/VT-d/AMD-Vi”
```
* Possibly an error in BIOS configuration.
    * If the problem appeared suddenly, verify the age of the CMOS battery.


## qubesd

* journalctl -xeu qubesd
    
     https://forum.qubes-os.org/t/no-qubes-launch-after-booting-qubes-4-3-menu-doesnt-work-qubes-domains-doesnt-work/39501/9

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
