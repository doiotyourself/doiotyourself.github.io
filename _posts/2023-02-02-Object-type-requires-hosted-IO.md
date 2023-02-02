---
layout: post
title: Object type requires hosted I/O
---

I have a reoccurring issue with my Home Assistant VM on ESXi. After the host is powered off ungracefully the VM will not power on, it errors: 

![Object type requires hosted I/O](/../images/doiotyourself.com_2023-02-02-Object-type-requires-hosted-IO_error.png)

The VMDK is version 6.2 and ESXi version 6.7. 

### tklaassens workaround 

I have been using [Tim's workaround](https://tklaassens.wordpress.com/2019/05/13/object-type-requires-hosted-i-o/) for too long:

SSH into the ESX host.

Run the following commands:

```console
[josh@esxi:~] vmkfstools -x check /vmfs/volumes/1b0d5392-52f42ee8/hass/haos_ova-6.2.vmdk
Disk needs repair.
[josh@esxi:~] vmkfstools -x repair /vmfs/volumes/1b0d5392-52f42ee8/hass/haos_ova-6.2.vmdk
Disk was successfully repaired.
```

### TriplusTutorials fix

This post claims to fix it permanently: [Running Hass.IO & Hass OS on VMWare ESXI 7.0](https://www.triplustutorials.be/homeassistant/running-hass-io-hass-os-on-vmware-esxi-7-0/)

## Let's go

1. Download the latest version of haos from [https://github.com/home-assistant/operating-system/releases](https://github.com/home-assistant/operating-system/releases). 
    
    The version I'm downloading is `haos_ova-9.5.vmdk.zip `

2. Extract the VMDK and upload it to your ESXi datastore.
3. Enable SSH on the host and navigate to the directory with the VMDK. 
    
    ```console
    [josh@esxi:~] cd /vmfs/volumes/1b0d5392-52f42ee8
    ```

4. Clone the virtualdisk to the permanent datastore
    
    ```console
    [josh@esxi:/vmfs/volumes/1b0d5392-52f42ee8] mkdir haos-9.5
    [josh@esxi:/vmfs/volumes/1b0d5392-52f42ee8] vmkfstools -i tmp/haos_ova-9.5.vmdk haos-9.5/haos_ova-9.5.vmdk
    Cloning disk 'tmp/haos_ova-9.5.vmdk'...
    Clone: 100% done.
    ```

5.  Create the VM
    
    | Hardware                  | Configuration                     |
    | ------------------------- | --------------------------------- |
    | Name                      | `haos-9.5`                          |
    | Datastore                 | `datastore2`                        |
    | Guest OS name             | Other 4.x or later Linux (64-bit) |
    | Compatibility             | ESXi 6.7 U2 virtual machine       |
    | vCPUs                     | 2                                 |
    | Memory                    | 16 GB                             |
    | Network adapters          | 1                                 |
    | Network adapter 1 network | `vm_vlan100 User`                   |
    | Network adapter 1 type    | E1000e                            |
    | IDE controller 0          | IDE 0                             |
    | IDE controller 1          | IDE 1                             |
    | Hard disk 1               |
    | Capacity                  | 0GB                               |
    | Datastore                 | `[datastore2] haos-9.5/`          |
    | Mode                      | `Dependent                        |
    | Provisioning              | Thick provisioned, lazily zeroed  |
    | Controller                | IDE controller 0 : 0              |
    | USB controller 1          | USB 2.0                           |
    
6. Disable UEFI secure boot.
7. boot the VM
    
    ![](/../images/doiotyourself.com_2023-02-02-Object-type-requires-hosted-IO_preparing-home-assistant.png)
    
8. Complete the setup process. 
9. Create a backup within Home Assistant
10.   Take snapshot of the VM.
11.   **play**
