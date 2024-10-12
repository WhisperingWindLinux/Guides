# These are brief notes on kernel compilation in Manjaro

1) Save this text file to the following path /etc/mkinitcpio.d/linux610.preset

```bash
# mkinitcpio preset file for the ‘6.10-x86_64’ package

#ALL_config=“/etc/mkinitcpio.conf”
ALL_kver=“/boot/vmlinuz-6.10-x86_64”

PRESETS=(‘default’ ‘fallback’)

#default_config=“/etc/mkinitcpio.conf”
default_image=“/boot/initramfs-6.10-x86_64.img”
#default_uki=“/efi/EFI/Linux/manjaro-6.10-x86_64.efi”
#default_options=“—splash /usr/share/systemd/bootctl/splash-manjaro.bmp”

#fallback_config=“/etc/mkinitcpio.conf”
fallback_image=“/boot/initramfs-6.10-x86_64-fallback.img”
#fallback_uki=“/efi/EFI/Linux/manjaro-6.10-x86_64-fallback.efi”
fallback_options=“-S autodetect”
```

2) Installing dependencies:

sudo pacman -Sy
sudo pacman -S mc gcc make flex bison cpio bison meson llvm14 python-mako pkg-config cmake python-packaging python-setuptools

3) Building the kernel (you can keep the default configuration and save it as is):

zcat /proc/config.gz >> .config
make menuconfig
make -j$(nproc)
sudo make modules_install
sudo make install
sudo cp /boot/vmlinuz /boot/vmlinuz-6.10-x86_64
sudo mkinitcpio -p linux610

4) Rebooting, we need to make sure the new kernel is loaded, this can be done with the command

uname -a
