
# Hardware

## PCI Passthrough

### IOMMU groups 

TODO: make it create a file with a dated filename.

Launch the Dom0 as a regular linux kernel. then run:

for d in /sys/kernel/iommu_groups/*/devices/*; do n=${d#*/iommu_groups/*}; n=${n%%/*}; printf 'IOMMU group %s ' "$n"; lspci -nns "${d##*/}"; done



### misc note on starting a second x server 

All the following may already be obvious to you, and it is all from memory, so there might be mistakes...

If you are using an AppVM, then the ```:0``` X server is the QubesOS one, which uses software rendering.

To use your passed-through card, you can create a second server. To make it use a second device (your Radeon), I think you must make an xorg.conf with the BusID parameter, which must point to the PCI device in the qube. I have previously used one something like in the link of @neowutran (above), where there are:
* A bare-bones xorg.conf [here](https://git.sr.ht/~yukikoo/gpu_template/tree/master/item/xorg.conf)
* and a script to keep it up-to-date and run the server [here](https://git.sr.ht/~yukikoo/gpu_template/tree/master/item/xorgX1.sh)

I did not use either of those files exactly, but maybe they will show you the idea, to create a second server called ```:1```

At the end of the xorgX1.sh script, ```startx``` is used - this is what actually creates a new server.

To make applications use the :1 server, it is normally enough to set the DISPLAY environment variable. For example:

```DISPLAY=":1" glxinfo```

Any graphics will go to the screen connected to the passed through GPU. It is also possible to:

```export DISPLAY=":1"```

so it is set for all applications you launch in the current terminal.
