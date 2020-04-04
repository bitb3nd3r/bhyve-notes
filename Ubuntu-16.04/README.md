These notes are for creating Ubuntu 16.04 LTS VM on FreeBSD/FreeNAS bhyve
Tested on FreeNAS 11.2/11.3

[[_TOC_]]

## Virtual CPUs

Ubuntu recommends 2+

## Memory Size

Ubuntu recommends 2GB+

## Boot Method

UEFI

First boot might fail. In which case ...
```bash
sudo mkdir -p /boot/efi/EFI/BOOT/
cp /boot/efi/EFI/ubuntu/grubx64.efi /boot/efi/EFI/BOOT/bootx64.efi
```

## Network

VirtIO

I had trouble with my OpenWRT dnsmasq setting up Ubuntu default gateway at one point. (sudo route add default gw x.x.x.x)

## Disk

Ubuntu recommends 25GB

Zvol in AHCI mode. VirtIO might work better. Default sector size since my pool is already running 4k sectors

## VNC / Serial

I typically use VNC with set resolution of 1024x768
