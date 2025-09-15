
## Getting the installation ISO file and the checksums and the signature

## Verify the signature of the ISO file

## Choose the installation medium

## Write the ISO to the installation medium


## Verify the installation medium

This is to make sure that the data we read from the medium is identical to the original ISO file.

### dd and XXXsum

### Find the position of errors on the medium

Trick to find where on your key are the error(s) seen, in this fine post by @apparatus :
[https://forum.qubes-os.org/t/an-unknown-error-ocurred-during-installation-on-empty-partition/28811/4](https://forum.qubes-os.org/t/an-unknown-error-ocurred-during-installation-on-empty-partition/28811/4)
You will need to run the command on a machine where you have both access to the full USB device, and the original good iso file. Change '/dev/sdd' to match the device of your USB key.
If the output is impossibly long, the following post shows use of ```head``` and ```tail``` to cut it down.
