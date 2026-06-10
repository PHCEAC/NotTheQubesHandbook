

## Sources of software

It is possible to install software from different repositories. The ```--enablerepo=``` will install a later version of a package, which will get replaced when one of your active repos gets a later version. ```--action=downgrade``` should allow replacement with your usual version.

Warning: it it possible for unstable or testing packages to make your system very difficult to repair.

* qubes-dom0-unstable repo
  * You probably do not want to use this repo. It is entirely possible that it contains broken packages.
  * [To quote Marek:](https://forum.qubes-os.org/t/latest-version-of-xen-hvm-stubdom-linux-broke-usb-passthrough/10314/5)   "It may be useful **only** for getting specific packages when explicitly requested (and then - enabled only temporarily, with ```--enablerepo``` option)." (my emphasis)
  * if anything breaks with this one, try to downgrade to a stable version: ```qubes-dom0-update --action=downgrade packagename```
