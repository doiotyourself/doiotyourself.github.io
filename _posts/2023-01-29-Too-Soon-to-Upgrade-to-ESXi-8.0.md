---
layout: post
title: Too Soon to Upgrade to ESXi 8.0
---

## There were a couple of big milestones for ESXi in October 2022

- ESXi 8.0 was released
- ESXi 6.7 End of General Support

I'm running ESXi 6.7 U3 on my main server at home. What does this mean for me? VMware does not offer new hardware support, server/client/guest OS updates, *new security patches* or bug fixes  unless otherwise noted.

## Can I Upgrade to ESXi 8.0

So let's check the [VMware Hardware Compatibility List (HCL)](https://www.vmware.com/resources/compatibility/) for my hardware to see if I can upgrade to the latest and greatest.

| Hardware                         | Supported in ESXi 8.0 |
| -------------------------------- | --------------------- |
| Super Micro X9DR3 Mainboard      | No                    |
| Intel Xeon E5-2600-v2 Series CPU | No                    |
| Mellanox ConnectX-3 10GbE        | No                    |
| Dell 6Gbps SAS HBA               | No                    |

Oh, that's not a good start.

### Super Micro X9DR3 Mainboard

[Devices deprecated and unsupported in ESXi 8.0 (88172)][] tells us Intel C602 and C606 chipsets are no longer supported in 8.0.

### Intel Xeon E5-2600-v2 Series CPU

Intel Xeon E5 2600 v2 Series is based on IvyBridge architecture and were released in 2013/2014. These CPUs are not supported in 8.0 - [there are workarounds](https://williamlam.com/2022/09/homelab-considerations-for-vsphere-8.html) - but I'm not interested. For me, this server is critical for my infrastructure.

### Mellanox ConnectX-3 10GbE

VMware removing [nmlx4_en driver][Devices deprecated and unsupported in ESXi 8.0 (88172)] in ESXi 8.0 outraged [r/homelab](https://www.reddit.com/r/homelab/).

### Dell 6Gbps SAS HBA

My Dell 6Gbps SAS HBA is probably a LSI SAS2008 under the hood and I have a spare HBA with the SAS2108 chip. When they both use the same firmware they can use the same ESXi driver. A quick repair should one fail.

*Alas, these HBA can't even upgrade to ESXi 7.0.*

So another day I may splurge about $140 on a Dell H330 and get one step closer to 8.0 (and 7.0 which is the latest version this machine is going to run). But for now I'll remain with ESXi 6.7 U3.

[Devices deprecated and unsupported in ESXi 8.0 (88172)]: https://kb.vmware.com/s/article/88172