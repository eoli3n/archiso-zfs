### Why this

If you want to install Archlinux on ZFS, you need to deal with the [ZFS licensing problem](https://wiki.archlinux.org/index.php/ZFS). The kernel module isn't included in the default archiso image, you need to [include it](https://wiki.archlinux.org/index.php/ZFS#Embed_the_archzfs_packages_into_an_archiso) into a custom archiso image to be able to install ZFS.

I wrote an article about [archiso netbooting](https://eoli3n.github.io/archlinux/2020/04/25/recovery.html).  
This project lets you include the zfs kernel module on any archiso image without creating a custom one.

### Archzfs

The [Archzfs](https://github.com/archzfs/archzfs/wiki) unofficial user repository offers multiple ways to install the ZFS kernel module.  
We need to compile the zfs module using [DKMS method](https://wiki.archlinux.org/index.php/ZFS#DKMS), so it will work with the running kernel.  
In order to build the module, DKMS needs the ``linux-headers`` package for the running kernel.

### How does it works

The script uses [Arch Linux Archive](https://wiki.archlinux.org/index.php/Arch_Linux_Archive#How_to_restore_all_packages_to_a_specific_date) to install the ``linux-headers`` package required for DKMS. 

### How to use

Boot on any archiso system, and run:
```
curl -s https://eoli3n.github.io/archzfs/init | bash
```

### Wow, that's slow...

Yes, the Arch Linux Archive has a limited brandwidth, but at least, it is automated.
A better solution would be to store archives on the Archzfs repo.
More details here: https://github.com/archzfs/archzfs/issues/337
