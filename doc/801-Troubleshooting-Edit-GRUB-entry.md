

​

# Troubleshooting: Using grub: modify a grub entry, change Dom0 kernel parameters

Was here:
https://forum.qubes-os.org/t/troubleshooting-using-grub-modify-a-grub-entry-change-dom0-commandline-add-or-remove-kernel-parameters/39265

ToDo:
* Unsafe shutdowns comment here https://forum.qubes-os.org/t/troubleshooting-using-grub-modify-a-grub-entry-change-dom0-commandline-add-or-remove-kernel-parameters/39265/2

Troubleshooting: Use grub for temporary changes when Qubes-OS is booting

For some problems, it can be useful to change the way Qubes starts at boot time.

This guide is about changing the very first part of boot, when xen and the Dom0 kernel are being started. In most cases, they are started by the grub bootloader.

## Interrupt grub

* Restart your computer, and watch the screen, waiting for the grub to display
    * Normally this is a blue screen, saying "Select operating system"
    * It shows some different “entries”
* There is a short time when you can interrupt it, using the keyboard...
    * If you do nothing, the default entry is automatically started
* To interrupt, you can do one of these:
    * press the key ‘e’ to edit the “default” entry. You can press “Esc” or “Escape” to return to the menu.
    * Press or hold SHIFT to stop the timer and go to the menu.

In the menu, you can select a different “entry”, using the Up and Down arrow keys. There may be troubleshooting entries, or ones to use different kernels. Press 'e' to edit an entry.
After booting, you can verify which kernel was used in Dom0 terminal, by typing uname -a.

In the edit mode, can modify the entry to have different kernel parameters.

## Change the Dom0 kernel parameters

This is almost always why we are here.

In the GRUB edit mode:

* Each item can be quite long, and may be split over several lines, or have the end hidden off the screen.
* Find the item that begins like this: ```module2  /vmlinuz```
* Use the Up/Down arrow keys to go to it.
* Go to the very end of the item, using right arrow.
* To add a parameter, type a space, then add the parameter. See below for some examples.
* To remove a parameter, Go to the end of it, and use “Backspace” key to delete characters.
* When you have finished:
     * Press the F10 key, to continue the boot, using your changes. Remember that the changes are temporary. They will not be there next time you restart.
     * Press "Esc" or “Escape” to cancel all changes and returns to the grub menu, where you can press 'e' and try again.
* If necessary, you can press Ctrl-Alt-Delete to reboot your computer without continuing the boot.


You can verify changes to the kernel parameters in a Dom0 terminal, after Qubes has started, by typing:
```cat /proc/cmdline```

If you find a good setting, make a careful note of the changes, because you may want to use the same changes again, or you may want to add some of them permanently.

Some typical parameters we might add or remove

USB keyboard problems

Add qubes.skip_autostart : prevents all qubes from automatic starting. This is useful when sys-usb has a problem and does not send keyboard/mouse data to Dom0. Normally, the next two items are used at the same time.

Remove rd.qubes.hide_all_usb : makes the USB controllers be visible to Dom0. It may not be enough to allow use of a USB keyboard

Add usbcore.authorized_default=0 : if Dom0 can see a USB controller, then only mouse and keyboard devices will be usable.

* Get better information for debugging
    * Remove “rhgb” and “quiet” : you will see lots of progress messages scroll past as the system starts up. This is often useful to see the last few messages before it stops.
* Prevent some drivers from loading
    * blacklist a kernel module

ToDo
Display is black or corrupted
nomodeset or modeset=0 : prevent Kernel Mode Setting from using GPU drivers
… ToDo more to add here.
Some more technical changes used in rare cases
Boot the Dom0 kernel without xen. Why…?
Hide some devices for Passthrough
Todo…

