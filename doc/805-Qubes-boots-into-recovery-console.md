

​
# Boot error: stuck in recovery console

## LVM Problems: I/O Errors make dom0 volume be read-only
​
This can happen when one of the thin pools has no free space. It prevents the filesystem check from completing during boot. It shows as `fsck`

If you hit this: check lvm lvs -a -o+lv_when_full,data_percent,metadata_percent qubes_dom0 first to see which specific pool is actually full before touching anything — don’t assume it’s vm-pool just because that’s the “main” one, since dom0’s own root filesystem has its own separate pool too.


Laptop won’t boot after dom0 update got interrupted, stuck in emergency mode, fsck shows I/O error 

(https://forum.qubes-os.org/t/laptop-wont-boot-after-dom0-update-got-interrupted-stuck-in-emergency-mode-fsck-shows-i-o-error/43131/5)

post by Martin32

Fixed it, turned out to be exactly what a couple of people suspected: the LVM thin pool ran out of space and locked itself read-only, which is why fsck kept throwing “Input/output error” instead of actually repairing anything.

For anyone else who hits this, here’s what worked:

1. Boot into the dracut emergency shell you’re already dropped into (no separate rescue USB needed).
2. Activate the volume group (note: this minimal shell doesn’t have separate vgchange/lvs/etc. commands, everything has to go through the combined lvm binary):

    lvm vgchange -ay
3. Check actual free space on the drive:

    lvm vgs qubes_dom0

    I had ~42GB sitting unallocated (VFree) that wasn’t assigned to either pool.
4. Important: there are two separate pools — vm-pool (your qubes) and root-pool (dom0’s own root filesystem). Figure out which one is actually backing the volume that’s failing. My root filesystem lives on root-pool, so I had to fix that one specifically, not just vm-pool.
5. Deactivate the whole volume group first (deactivating just the pool fails while thin volumes on top of it are still active):

    lvm vgchange -an qubes_dom0
6. Extend the pool that’s actually short on space:

    lvm lvextend -L +5G qubes_dom0/root-pool
    lvm lvextend -L +5G qubes_dom0/vm-pool
7. Repair it:

    lvm lvconvert --repair qubes_dom0/root-pool    
    lvm lvconvert --repair qubes_dom0/vm-pool
8. Reactivate everything:

    lvm lvchange -ay qubes_dom0/root-pool
   
    lvm lvchange -ay qubes_dom0/vm-pool
   
    lvm lvchange -ay qubes_dom0/root
10. Then finally run fsck:

    fsck -y /dev/mapper/qubes_dom0-root
    
    It fixed a bunch of inode ref-count errors and finished clean with no I/O error this time. Rebooted normally and everything came back up.



Also worth doing afterward: set thin_pool_autoextend_threshold in /etc/lvm/lvm.conf so pools grow automatically before hitting 100% again.

