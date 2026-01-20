# change the qubes system startup

etc etc todo


* remove ```quiet rhgb``` :  See output from the boot process
* rd.plymouth=0 plymouth.enable=0   : do not use plymouth

* systemd.mask=        : prevent a systemd service from starting.

* rd.driver.blacklist=nouveau nvidia-drm.modeset=0 : e.g. to prevent gpu drivers from loading. (this one for Nvidia passthrough https://forum.qubes-os.org/t/salt-automating-nvidia-gpu-passthrough/30038/10 )



### kernel debugging

* kernel.panic_on_oops=0
* kernel.panic_on_warn=0 # /etc/sysctl.conf
