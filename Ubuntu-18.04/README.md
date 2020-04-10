## These notes are for creating Ubuntu 18.04 LTS VM on top of FreeBSD/FreeNAS bhyve
Tested on FreeNAS 11.2/11.3

----

## Virtual CPUs

Ubuntu recommends 2+

## Memory Size

Ubuntu recommends 2GB+

## Boot Method

UEFI

No issues with booting Ubuntu 18.04 on FreeNAS 11.3

## Network

VirtIO

For some reason Ubuntu assigned network configuration to enp0s5 so I had to change it to enp0s4
```
$ cat /etc/netplan/50-cloud-init.yaml 
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        enp0s4:
            dhcp4: true
    version: 2
```

## Disk

Ubuntu recommends 25GB

Sparse Zvol in VirtIO mode. Default sector size since my pool is already running 4k sectors

## VNC / Serial

I typically use VNC with set resolution of 1024x768
