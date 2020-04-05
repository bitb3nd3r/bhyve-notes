## These notes are for creating Windows 10 VM on top of FreeBSD/FreeNAS bhyve
Tested on FreeNAS 11.2/11.3 and Windows 10 1809 x64

----

## Virtual CPUs

I gave it 2 virtual CPUs. Since Windows 7 needs those cores to be on same package, following sysctl value has to be changed in either /boot/loader.conf under FreeBSD or System>Tunables under FreeNAS
```
hw.vmm.topology.cores_per_package="2" # Set 2 cores per package for bhyve
```
This change requires a reboot

## Memory Size

I gave it 8GB

## Boot Method

UEFI

## Network

Intel e1000

## Disk

Zvol in AHCI mode. Default 4k block size worked fine for me since Windows 10 supports it.

## VNC / Serial

I typically use VNC with set resolution of 1024x768
