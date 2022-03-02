# ThinkPad W540

```sh
# Windows 10 Pro serial number
NCPBD-TMT6G-BK8MY-4KQVJ-82KV2
```

Decrypt and mount fs

```sh
encfs ~/Dropbox/Mulder/Private/ ~/Private/
```

Keymaps

```sh
# US
localectl set-keymap us
localectl set-x11-keymap us

# UK
localectl set-keymap gb
localectl set-x11-keymap uk

openbox --exit
```

## Disks

Boot and LVM for rest.

> The overlay and overlay2 drivers are supported on xfs backing filesystems, but only with d_type=true enabled.

```sh
# docker lv
mkfs.xfs -n ftype=1
xfs_info
```

## Make

```
COMMON_FLAGS="-march=haswell -O2 -pipe"
CFLAGS="${COMMON_FLAGS}"
CXXFLAGS="${COMMON_FLAGS}"
MAKEOPTS="-j8"
```

```sh
genkernel --lvm --microcode=intel --install --kernel-config=/usr/src/linux/.config initramfs
# https://wiki.gentoo.org/wiki/NVIDIA/nvidia-drivers#Drivers
emerge @module-rebuild
```

- [Intel microcode](https://wiki.gentoo.org/wiki/Intel_microcode)
- [Safe CFLAGS](https://wiki.gentoo.org/wiki/Safe_CFLAGS#Haswell)
- [Intel® Core™ i7-4800MQ Processor (6M Cache, up to 3.70 GHz)](https://www.intel.com/content/www/us/en/products/sku/75128/intel-core-i74800mq-processor-6m-cache-up-to-3-70-ghz/specifications.html?wapkw=Intel%28R%29%20Core%28TM%29%20i7-4800MQ)


## Resources

- [Gentoo Encrypted Root, with LUKS and LVM](https://linux.arantius.com/gentoo-encrypted-root-with-luks-and-lvm)
- [Gentoo LVM](https://wiki.gentoo.org/wiki/LVM)
- [Gentoo Handbook](https://wiki.gentoo.org/wiki/Handbook:AMD64)
- [Docker use the OverlayFS storage driver](https://docs.docker.com/storage/storagedriver/overlayfs-driver/)

- [Official drivers](https://pcsupport.lenovo.com/ie/en/products/laptops-and-netbooks/thinkpad-w-series-laptops/thinkpad-w540/downloads/ds039077)
- [ThinkWiki](https://www.thinkwiki.org/wiki/Category:W540)
- [ThinkPad with Linux](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit#)
- [Gento ThinkPad W540](https://wiki.gentoo.org/wiki/Lenovo_Thinkpad_W540)

