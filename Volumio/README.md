## These notes are for creating Volumio VM on top of FreeBSD/FreeNAS bhyve
Tested on FreeNAS 11.2/11.3 and volumio-2.729-2020-03-18-x86

----

## Virtual CPUs

1 core should be enough

## Memory Size

1GB should be enough

## Boot Method

UEFI

## Network

Intel e1000. Doesn't look like volumio has VirtIO driver

## Disk

5GB should be enough

Sparse Zvol in AHCI mode. VirtIO didn't work. Default sector size since my pool is already running 4k sectors

## VNC / Serial

I typically use VNC with set resolution of 1024x768

## Installation

Write image file to the block device
```bash
unzip -p volumio-2.729-2020-03-18-x86.img.zip > /dev/zvol/...
```
