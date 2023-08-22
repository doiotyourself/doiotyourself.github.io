Wipe the configuration

```console
delete flash:vlan.dat

write erase
```

disable the stack election process to boot the ios faster
```console
conf t

switch 1 priority 15

end
```
