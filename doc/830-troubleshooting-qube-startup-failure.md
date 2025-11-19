830-troubleshooting-qube-startup-failure.md

## A qube has failed to start : cannot connect to qrexec agent for 60 second, see var/log/xenconsole/guest

* When qubes tries to start a qube, it waits for a response indicating that the qube has started correctly.
* If no response comes before the timeout then an error is displayed
* Normally happens due to long housekeeping
    task at startup
* Often it is solved by a temporary increase of the timeout.
    * qvm-pref??


# disposable 

# AppVM


# HVM

if has passed-through devices:

* Check logs (path?), look for:
* Wrong device

# Standalone

* trying to use kernel provided by Dom0 
