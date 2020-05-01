### Why this

If you want to install Archlinux on ZFS, you need to deal with [ZFS licensing problem](https://wiki.archlinux.org/index.php/ZFS). Kernel module isn't included in default archiso, you need to [include it](https://wiki.archlinux.org/index.php/ZFS#Embed_the_archzfs_packages_into_an_archiso) in a custom archiso to be able to install ZFS.

I wrote an article about [archiso netbooting](https://eoli3n.github.io/archlinux/2020/04/25/recovery.html).  
This project let you include zfs kernel module on any archiso without creating a custom one.

### Archzfs

Archzfs unofficial user repository allows one to install ZFS kernel module in multiple ways.  
We will compile current kernel zfs module using DKMS method.
DKMS needs ``linux-headers`` of the currently booted system to be able to build the module.

### How does it work

It uses [Arch Linux Archive](https://wiki.archlinux.org/index.php/Arch_Linux_Archive#How_to_restore_all_packages_to_a_specific_date), to be able to install ``linux-headers`` required by DKMS.

### How to use

Boot on any archiso, and use
```
curl -s https://eoli3n.github.io/archzfs/init | bash
```
This is a mirror with an easier url. Instead you can use a more hacky way

```
```

### Wow, that's slow...

Yes, Arch Linux Archive have a limited brandwidth, but at least, it is automated.
A better solution would be to store archives on Archzfs repo.
More details here : https://github.com/archzfs/archzfs/issues/337
