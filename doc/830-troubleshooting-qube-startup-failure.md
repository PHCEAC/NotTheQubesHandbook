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

## qubesd

* journalctl -xeu qubesd
    
     https://forum.qubes-os.org/t/no-qubes-launch-after-booting-qubes-4-3-menu-doesnt-work-qubes-domains-doesnt-work/39501/9



# disposable 

# AppVM


# HVM

if has passed-through devices:

* Check logs (path?), look for:
* Wrong device

# Standalone

* trying to use kernel provided by Dom0 
