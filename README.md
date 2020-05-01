### Why this

If you want to install Archlinux on ZFS, you need to deal with [ZFS licensing problem](https://wiki.archlinux.org/index.php/ZFS). The kernel module isn't included in default archiso, you need to [include it](https://wiki.archlinux.org/index.php/ZFS#Embed_the_archzfs_packages_into_an_archiso) in a custom archiso to be able to install ZFS.

I wrote an article about [archiso netbooting](https://eoli3n.github.io/archlinux/2020/04/25/recovery.html).  
This project lets you include the zfs kernel module on any archiso without creating a custom one.

### Archzfs

The [Archzfs](https://github.com/archzfs/archzfs/wiki) unofficial user repository allows one to install the ZFS kernel module in multiple ways.  
We need to compile zfs module using [DKMS method](https://wiki.archlinux.org/index.php/ZFS#DKMS) for the kernel used by the running archiso.
DKMS needs ``linux-headers`` to be able to build the module.

### How does it work

It uses [Arch Linux Archive](https://wiki.archlinux.org/index.php/Arch_Linux_Archive#How_to_restore_all_packages_to_a_specific_date) to install the matching version of ``linux-headers`` required by DKMS.

### How to use

Boot on any archiso, and use
```
curl -s https://eoli3n.github.io/archzfs/init | bash
```

### Wow, that's slow...

Yes, the Arch Linux Archive have a limited brandwidth, but at least, it is automated.
A better solution would be to store archives on the Archzfs repo.
More details here : https://github.com/archzfs/archzfs/issues/337
