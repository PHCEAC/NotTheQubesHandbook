

# Services and qrexec

## qrexec

In short:

qrexec is a "remote procedure call" (RPC) framework for Qubes.

qrecec-client contacts daemon, communicates with agent



* code : https://github.com/QubesOS/qubes-core-qrexec
* docs: https://doc.qubes-os.org/en/latest/developer/services/qrexec.html

## qrexec troubleshooting

### qrexec timeout

solution is here:

 In dom0: ```qvm-prefs <qube name> qrexec_timeout 300```
 
 <!-- Another way is to tell systemd not to start the problem service using the kernelopts option, and to do the resizing manually after: qvm-prefs <qube name> kernelopts systemd.mask=qubes-rootfs-resize.service-->

### services do not run...
* The scripts in /etc/qubes-rpc need to be proper scripts, with executable bit set (chmod 0755) and proper shebang (#!/bin/sh for example).
    * see https://forum.qubes-os.org/t/problems-with-qrexec-after-an-update/40486/2
