999-todo.md

## prefs and features

qvm-create -l red -t <NEW_TEMPLATE> <NEW_DISPOSABLE_TEMPLATE>
* qvm-prefs <DISP_TPL> template_for_dispvms True
* qvm-features <DISP_TPL> appmenus-dispvm 
* qubes-prefs default-dispvm <DISP_TPL>


## different stub drivers:
useful notes:
https://vfio.blogspot.com/2015/05/vfio-gpu-how-to-series-part-3-host.html?m=1


v4.1 users with exclusively OVMF guests can also add an "options vfio-pci disable_vga=1" line to their modprobe.d which will cause vfio-pci to opt-out devices from vga arbitration if possible.  

## config...

forum.qubes-os.org/t/qubes-user-data-utilize-vm-config-to-execute-scripts-at-qube-launch-even-in-dispvms/34602


