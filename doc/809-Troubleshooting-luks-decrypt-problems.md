First thing: did you do a backup of the full disk yet? I recommend the full device, including boot and efi partitions. Everything!

[quote="phceac, post:8, topic:43420"]
Have you looked at the password you are typing?
[/quote]

If you did that during recent tries, then did do it before, when the unlock was working?

I am still thinking of keyboard layout... default for early boot is en_us, but it can be changed.

After that backup, you can make a backup of the header using 
```cryptsetup luksHeaderBackup --header-backup-file a_filename.img /dev/your-disk```
(Of course, put a useful filename and device)

Then you can take the file to any linux with recent cryptsetup for testing with 
```cryptsetup luksOpen --test-passphase  a_filename.img```

At least it lets you play with kb layout, and other things, without waiting for a whole reboot!


