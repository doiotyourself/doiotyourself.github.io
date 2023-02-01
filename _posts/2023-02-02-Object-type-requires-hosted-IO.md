---
layout: post
title: Object type requires hosted I/O
---

See: https://tklaassens.wordpress.com/2019/05/13/object-type-requires-hosted-i-o/

VM will not power on and throws the following error:

![Object type requires hosted I/O](/../images/doiotyourself.com_2023-02-02-Object-type-requires-hosted-IO_error.png)

SSH into the ESX-host that’s hosting the VM.

Run the following command:

```console
vmkfstools -x check /vmfs/volumes/1b0d5392-52f42ee8/hass/haos_ova-6.2.vmdk
Disk needs repair.
vmkfstools -x repair /vmfs/volumes/1b0d5392-52f42ee8/hass/haos_ova-6.2.vmdk
Disk was successfully repaired.
```
