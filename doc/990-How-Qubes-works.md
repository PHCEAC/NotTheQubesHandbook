A bit ambitious this one...

# How does Qubes OS work?

## What is Qubes OS?

* A collection of "qubes", each of which gives the user access to some resources.
* By default, all qubes are heavily isolated:
  * from each other
  * from the hardware devices
  * Shared user interfaces allow the user to interact with one qube at a time, while maintaining the isolation from other qubes.
* A controller qube, named **dom0** manages the system:
  *  creating new qubes
  *  giving out access to some parts of the hardware
  *  allowing each qube to have access to the functions and interfaces it is allowed
  *  providing interfaces for each qube to send data to other qubes


## what is a qube?

In qubes-OS, each qube:

* is a **Virtual Machine**, or **VM**
* is allocated some part of the computer memory, and part of the CPU time, so that it can run.
* has access to a minimal display, which can create windows by using a very simple framebuffer interface, with some very simple window controls.
* has some inputs from the user - normally at least a mouse and keyboard, which only receive input when a window of that qube is focussed.
* *may* be given access to some other hardware, like a network or USB controller

The isolation and access to hardware are assured by  a  **hypervisor**. Qubes-OS uses the Xen hypervisor, which is a separate layer, in between dom0 and the real hardware.pà


## What is a VM?

## What does xen do?

* Starts the dom0 virtual machine
* Starting and stopping virtual machines
* Give direct hardware access to some VMs
* Grant tables
    * provide shared memory, so that some VMs can communicate
    * tech doc here: https://xcp-ng.org/blog/2022/07/27/grant-table-in-xen/

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
 


