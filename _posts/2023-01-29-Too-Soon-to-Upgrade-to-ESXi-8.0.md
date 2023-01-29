---
layout: post
title: Too Soon to Upgrade to ESXi 8.0
---

## There were a couple of big milestones for ESXi in October 2022

- ESXi 8.0 was released
- ESXi 6.5 and 6.7 end of support

What does this mean for me?

I'm running ESXi 6.7 U3 on my main server at home. So let's check the HCL and see if I can upgrade to the latest and greatest.

| Hardware                     | Hardware supported in ESXi 8.0 |
| ---------------------------- | ------------------------------ |
| Super Micro X9DR3            | No                             |
| Intel Xeon E5-2600-v2 Series | No                             |
| Mellanox Connectx-3          | No                             |
| Intel I350                   | Yes                            |
| Dell 6Gbps SAS HBA           | No                             |

Ohh, that's not a good start. Maybe this my hardware may be too old for VMware and the hardware manufacturers to bother testing on ESXi 8.0. I'd better put some extra time aside to try this out.

For interest's sake, let's have a look at ESXi 7.0 U3. 

| Hardware                     | Hardware supported in ESXi 7.0 U3 |
| ---------------------------- | --------------------------------- |
| Super Micro X9DR3            | Yes                               |
| Intel Xeon E5-2600-v2 Series | Yes                               |
| Mellanox Connectx-3          | Yes                               |
| Intel I350                   | Yes                               |
| Dell 6Gbps SAS HBA           | No                                |

That HBA is fairly important.

I'll put this project on the back burner.
