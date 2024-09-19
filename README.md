# ThinkPad W540

```sh
# Windows 10 Pro serial number
NCPBD-TMT6G-BK8MY-4KQVJ-82KV2
```

Bela 

```
modprobe rndis_host
```

Decrypt and mount fs

```sh
encfs ~/Dropbox/Mulder/Private/ ~/Private/
```

Wifi

```sh
# list network devices
nmcli dev status
# check wifi is on
nmcli radio wifi
nmcli radio wifi on

# list wifi networks
nmcli dev wifi list
# connect to wifi network
# nmcli dev wifi connect $ssid password "secret"
nmcli --ask dev wifi connect $ssid
```

When some wifi networks aren't showing rebuild wpa_supplicant with tkip enabled.

```
# /etc/portage/package.use/wpa_supplicant
net-wireless/wpa_supplicant tkip
```

Redshift

```sh
# ~/.config/redshift.conf
[redshift]
location-provider=manual
[manual]
lat=52.6477
lon=7.2561
```

Skype

```sh
apulse skypeforlinux %U
```

Spotify

[librespot](https://github.com/librespot-org)

Build librespot with ALSA backend

```
cargo build --release --no-default-features --features "alsa-backend"
mv target/releases/librespot ~/bin/

# oauth authentication
rm -r /home/cm/.cache/kraxarn
librespot -u e7z4uojse@mozmail.com -c /home/cm/.cache/kraxarn/spotify-qt/librespot -j
librespot --bitrate 320 --username e7z4uojse@mozmail.com --name "spotify-qt (librespot)" --initial-volume 100 --cache /home/cm/.cache/kraxarn/spotify-qt/librespot --autoplay on --backend alsa --device-type computer
```

[spotify-tui](https://github.com/Rigellute/spotify-tui)

[spotify-qt](https://github.com/kraxarn/spotify-qt)

`spotify-qt` can be configured to autostart `librespot` on start.

To start in debug mode try `spotify-qt --dev`

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

## ALSA

```sh
cat /proc/asound/cards
```

```sh
aplay -L
speaker-test -Ddefault:PCH -c 2
speaker-test -Ddefault:USB -c 2
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

## Audio Production

- [qjackctl]()https://qjackctl.sourceforge.io/
- [Jack Wiki](https://github.com/jackaudio/jackaudio.github.com/wiki)
- [Jack apps](https://jackaudio.org/applications/)
- [JAMin Mastering Suite](http://jamin.sourceforge.net/en/about.html)
- [Audacity](https://manual.audacityteam.org/)
- [Ardour 6](https://ardour.org/)

## Resources

- [Nvidia Optimus](http://us.download.nvidia.com/XFree86/Linux-x86_64/331.79/README/optimus.html)
- [ALSA .asoundrc syntax](https://www.alsa-project.org/alsa-doc/alsa-lib/conf.html)
- [Gentoo Encrypted Root, with LUKS and LVM](https://linux.arantius.com/gentoo-encrypted-root-with-luks-and-lvm)
- [Gentoo LVM](https://wiki.gentoo.org/wiki/LVM)
- [Gentoo Handbook](https://wiki.gentoo.org/wiki/Handbook:AMD64)
- [Docker use the OverlayFS storage driver](https://docs.docker.com/storage/storagedriver/overlayfs-driver/)

- [Official drivers](https://pcsupport.lenovo.com/ie/en/products/laptops-and-netbooks/thinkpad-w-series-laptops/thinkpad-w540/downloads/ds039077)
- [ThinkWiki](https://www.thinkwiki.org/wiki/Category:W540)
- [ThinkPad with Linux](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit#)
- [Gento ThinkPad W540](https://wiki.gentoo.org/wiki/Lenovo_Thinkpad_W540)

