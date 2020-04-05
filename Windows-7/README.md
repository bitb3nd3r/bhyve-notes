## These notes are for creating Windows 7 VM on top of FreeBSD/FreeNAS bhyve
Tested on FreeNAS 11.2/11.3 and Windows 7 Pro SP1 x64

----

## Virtual CPUs

I gave it 2 virtual CPUs. Since Windows 7 needs those cores to be on same package, following sysctl value has to be changed in either /boot/loader.conf under FreeBSD or System>Tunables under FreeNAS
```
hw.vmm.topology.cores_per_package="2" # Set 2 cores per package for bhyve
```
This change requires a reboot

## Memory Size

I gave it 4GB

## Boot Method

UEFI

## Network

VirtIO.

Intel emulation was unstable for me.

Drivers can be downloaded from <https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso>

More information can be found on <https://docs.fedoraproject.org/en-US/quick-docs/creating-windows-virtual-machines-using-virtio-drivers/index.html>

NetKVM directory contains the VirtIO network driver

## Disk

Sparse Zvol in AHCI mode.

VirtIO failed to work for me. It's important to use 512 sector size, since Windows 7 by default lacks 4k support

## VNC / Serial

I typically use VNC with set resolution of 1024x768
