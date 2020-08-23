This is a hook for `mkinitcpio` in ArchLinux when using Plymouth and ZFS with native encryption.



## Usage

!!! Make sure `plymouth-zfs` is **NOT** installed !!!

1. Download `plymouth-zfs.install` and `plymouth-zfs.hook`.
2. Place `plymouth-zfs.install` at `/etc/initcpio/install/plymouth-zfs`.
3. Place `plymouth-zfs.hook` at `/etc/initcpio/hooks/plymouth-zfs`.
4. Update the *HOOKS* array in `/etc/mkinitcpio.conf` as per the [docs](https://wiki.archlinux.org/index.php/Plymouth#The_plymouth_hook).
5. Rebuid the initrams (`mkinitcpio -P`) and sign it if needed.


Example *HOOKS* array:

```
HOOKS=(base udev plymouth autodetect modconf block keyboard plymouth-zfs filesystems)
```



## Status

The hook works for me but YMMV. My goal is to setup an AUR package that automatically patches the hook from the ArchZFS repository.



## Motivation

This is a replacement for [plymouth-zfs](https://aur.archlinux.org/packages/plymouth-zfs).

That package seems unmaintained and there's a bug in the handling of the file systems: it ignores filesystems with `canmount=off`.

The scripts here are based on up-to-date ones from ArchZFS with minimal changes inspired by *plymouth-zfs*.



## Contributing

Feel free to open an issue or send a pull request. Note that as this is a tiny modification over the upstream, the issue is likely to come from there.



## License

This code is distributed under the terms of the MIT License, like the upstream project ArchZFS.



## See also

* [ArchZFS](https://github.com/archzfs/archzfs)
* [Install ArchLinux on ZFS](https://wiki.archlinux.org/index.php/Install_Arch_Linux_on_ZFS)
* [ArchLinux mkinitcpio](https://wiki.archlinux.org/index.php/Mkinitcpio)
* [Plymouth on ArchLinux](https://wiki.archlinux.org/index.php/Plymouth)
