## These notes are for creating OpenWRT 19.07.x VM on top of FreeBSD/FreeNAS bhyve
Tested on FreeNAS 11.2/11.3 and withopenwrt-19.07.2-x86-64-combined-ext4.img

----

## Virtual CPUs

1 core is enough

## Memory Size

512MB is just fine

## Boot Method

UEFI-CSM

## Network

VirtIO

## Disk

Sparse Zvol in AHCI mode. Default 4k block size worked fine for me

## VNC / Serial

Serial console works fine

## Installation

Write image file to the block device
```bash
sudo gzcat openwrt-19.07.2-x86-64-combined-ext4.img.gz > /dev/zvol/...
```
