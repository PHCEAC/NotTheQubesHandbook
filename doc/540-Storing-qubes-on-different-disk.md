

It is possible to keep the storage volumes for some qubes on a different disk, partition, or volume. It is documented, but as "Advanced" subject.

There are some slightly old instructions here: https://doc.qubes-os.org/en/latest/user/advanced-topics/secondary-storage.html. I used them a time ago - but only the LVM part, not any btrfs sections. I cannot guarantee them.

The first thing is to back up ALL your qubes/data/system. You should know why - it is because some manual operations on storage is necessary, where a mistake could destroy all your data.

My summary or short version of the procedure is below. If you do not understand some parts, then I would not recommend the procedure for you.

The steps will be:

1. Set up encryption on the new volume.
2. Create a new thin pool using LVM tools.
3. Create a new Qubes "storage pool", using the qvm-pool command.
4. Maybe  "Move" some qubes to the new pool, using qvm-clone - this makes new copies of those qubes, it does not really move them.   When the new clones are working how you want, delete or archive the originals.
5. If you want new qubes to be created on the new volume, change the "default pool" for new qubes setting.
