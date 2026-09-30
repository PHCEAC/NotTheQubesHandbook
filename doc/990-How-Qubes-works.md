A bit ambitious this one...

# how Qubes works...

* Memory ballooning


## dom0

AKA domain-zero, domzero...

## what is a qube

## qubesd

## RPC

## qubes services



## Memory ballooning

This is a system which allows dom0 to reclaim memory from one qube to give it to another.

* Each qube either:
    * can have fixed amount of allocated memory, or
    * it has a minimum and a maximum amount of memory, which is provided according to need.
* Inside a qube, a daemon sends memory usage information to dom0
    * For linux qubes, this is done by the
      meminfo-writer service. (see [meminfo-writer](https://github.com/QubesOS/qubes-linux-utils/tree/main/qmemman)
    * For windows...? QWT?
    * this information is only useful if the memory balloning is active.
* Inside dom0:
     * TODO: when memory is needed by a qube... some magic
 


