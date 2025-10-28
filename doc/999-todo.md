999-todo.md


## different stub drivers:
useful notes:
https://vfio.blogspot.com/2015/05/vfio-gpu-how-to-series-part-3-host.html?m=1


v4.1 users with exclusively OVMF guests can also add an "options vfio-pci disable_vga=1" line to their modprobe.d which will cause vfio-pci to opt-out devices from vga arbitration if possible.  
