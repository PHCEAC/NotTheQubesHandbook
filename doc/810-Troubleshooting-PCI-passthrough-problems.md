


## When Dom0 kernel update causes  PCI device identifiers to change.

It is probable that only three simple steps are necessary to resolve this problem.

1.  Use the solution in the second thread to prevent sys-net autostart (see below for a summary)
2. Remove attached PCI devices from qubes that fail to start, using the Settings for the qubes.
3. When it is possible to reboot the whole machine with no PCI-related failures and without disabling of autostart, add only the single device to sys-net, using the recommendation of @mnfTgh in this first thread [at comment 12](https://forum.qubes-os.org/t/major-qubes-malfunction-pci-device-not-available-wont-boot-on-certain-laptop-backup-vms/40038/12).

In previous cases, I have found that those are the correct solution when kernel updates cause problems like this.

If you try them, make careful notes of every step you do, in case you get blocked. 

For 1, follow the [Autostart troubleshooting instructions](https://doc.qubes-os.org/en/latest/user/troubleshooting/autostart-troubleshooting.html)

1. Press the `E` key on the first prompt (or your custom prompt). It may say "Select operating system". 
2. Then, press the down arrow key multiple times to reach the line starting with ```module2 /vmlinuz```
4. Use the right arrow to go to the end of the line, which might be off the screen.
5. add a space and then  ```qubes.skip_autostart``` at the end of the line
6. Press Ctrl-x or F10 to boot

For 2. the Settings app is simple. ```sudo qvm-pci unassign sys-net``` can also work to remove attachment of wrong devices.

For 3. take care at first only to add the necessary devices to sys-net. ```qvm-start sys-net``` can be used to test. 

If there is a problem, then it will be necessary to troubleshoot. 
* Maybe it will be necessary to use "qubes.skip_autostart" again. 
* There are some ideas [in the pci troubleshooting document.](https://doc.qubes-os.org/en/latest/user/troubleshooting/pci-troubleshooting.html)  
* If something is not clear, then get help before making big changes.
