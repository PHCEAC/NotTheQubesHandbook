
## Non sys-net qubes

easiest approach is to attach it (the USB device, using devices widget) to the VM where you want to use it (from where you’ll SSH into it etc). And then you need to configure it (by default NetworkManager is running only in sys-net, so it doesn’t happen automatically elsewhere), easiest by simply calling dhclient enu1 (where enu1 is the actual interface name). You may need to install dhclient first (dhcp-client package on Fedora, likely similar on Debian).



## USB network devices

### use without providing network to other qubes

"easiest approach is to attach it (the USB device, using
devices widget) to the VM where you want to use
it (from where you’ll SSH into it etc). And then 
you need to configure it (by default NetworkManager 
is running only in sys-net, so it doesn’t happen
automatically elsewhere), easiest by simply calling dhclient 
enu1 (where enu1 is the actual interface name). You 
may need to install dhclient first (dhcp-client package on Fedora, likely similar on Debian).

