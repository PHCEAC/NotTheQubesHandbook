# About storage for VMs

Possible storage backends: lvm vs btrfs? Others?

# LVM volume group is full, prevents startup of any vm

Message: Cannot create new thin volume, free space in thin pool <qubes/poolhd0> reached threshold.

Possible solutions :

* delete unused qube(s)
* delete backup volume(s)
* mount a volume on a disposable and remove files to shrink it.
* Questions:
     * Can we back up a qube without being able to run it?
     * Can we move a qube to another VG?
     * Is it best practise to keep a 'rescue' vg with some spare qubes ? also for essential service qubes?


See 
https://forum.qubes-os.org/t/how-can-i-delete-all-names-with-the-file-extension-iso-and-img-from-dom0-terminal-in-the-vm10/

https://www.qubes-os.org/doc/mount-lvm-image/


