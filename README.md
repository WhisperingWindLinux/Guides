# This guide contains a description of applying the fix that disables dithering in 6-bit mode for Intel iGPU/GPU in Linux

## This is very important information, do not skip this section!

The i915 module in the Linux kernel is responsible for managing Intel iGPU/GPU. Dithering is disabled here for modes of 8 bits and above, but for 6-bit mode, it is enabled (spatial dithering). 
This fix disables dithering in 6-bit mode. This fix may be useful only for those who use 6bit+FRC monitors and want to enable 6-bit in Linux, as spatial dithering can lead to more active FRC module operation on the monitor and cause eye strain in 6-bit mode.</p>
**The monitor must be connected via DisplayPort to your Intel iGPU/GPU. Exceptions may include Intel Arc, where the HDMI port is routed internally through DisplayPort. Alternatively, your motherboard might be designed similarly for the iGPU, but this is unlikely.**</p>
**X11 provides an easy way to switch between 6, 8, 10, etc., bit modes using the xrandr command. Other environments may not support color depth selection (for example, Wayland). Use X11.**

The fix have been made in linux kernel version 6.10. I haven't checked the minimum version of the distro required for this kernel. But if you want to try building a different version of the kernel, you'll need [these changes in your kernel version](https://github.com/WhisperingWindLinux/linux/commit/fba72946743be6f30d426db3eb17b1f4ff6af509). Alternatively, you can ask me to apply the changes to the kernel version you need on the forum.

This guide has been tested on Ubuntu 24.04.1 LTS. In theory, it should work on other Debian-based distros, but I haven't tested it in practice.
If your distro is not based on Debian, some of the commands presented here will not work. You will need to find a kernel compilation guide for your distro.

The fix has been tested on Intel Alder Lake UHD 48EU (Xe) i5-12450h and Intel Arc A770, but it should work for all Intel iGPU/GPU. However, for understandable reasons, there is no 100% guarantee here.

**This fix, unfortunately, does not guarantee that eye strain will stop during work, as iGPU/GPU dithering is not the only cause.**

## How to build the kernel

This is not the most comprehensive guide for building a kernel. For example, it omits issues related to digital signatures. However, what is described here is a minimally functional version that will allow you to build and use a new kernel.

**1) Before starting the build, you need to install dependencies and tools for building**

```bash
sudo apt update
sudo apt install git libncurses-dev gawk flex bison openssl libssl-dev dkms libelf-dev libudev-dev libpci-dev libiberty-dev autoconf llvm intel-gpu-tools
```

**2) Download the modified kernel code**

```bash
git clone --depth 1 --branch 6bit_nodither_v610 https://github.com/WhisperingWindLinux/linux.git
```

**3) The kernel configuration before building**

```bash
cd linux
```
```bash
cat /boot/config-$(uname -r) >> .config
```
```bash
make menuconfig  # In the opened "window," the sequence of buttons is "Save – OK – Exit – Exit," meaning we save the configuration without changing anything and exit.
```
```bash
scripts/config --disable SYSTEM_TRUSTED_KEYS
scripts/config --disable SYSTEM_REVOCATION_KEYS
```

**4) Building the kernel**

```bash
make -j$(nproc)  # For any questions from the builder that appear in the terminal, press "Enter"
```
```bash
sudo make modules_install
```
```bash
sudo make install
```

**5) Restart**

If you select "Advanced option for Ubuntu" in the boot menu, you will see the option to boot kernel 6.10.0+. Choose it. After booting, check that the correct kernel has loaded with the command:

```bash
uname -r
```

The result of the command should be:

```bash
6.10.0+
```

# Useful commands

## How to switch to 6-bit mode

Note: xrandr uses X11, so it will not work fully in other environments. For example, the Wayland architecture does not allow changing the color depth in the OS as easily.

You can switch to 6-bit mode with the command:

```bash
xrandr --output DISPLAY_NAME --set "max bpc" 6
```

You can find DISPLAY_NAME by running the command:

```bash
xrandr --listmonitors
```

In my case, DISPLAY_NAME is DP-1

```bash
Monitors: 1
 0: +*DP-1 1920/531x1080/298+0+0  DP-1
```

## If you feel that the brightness of the white field is straining your eyes

Try switching between Limited Range / Full Range and decide which one is better

```bash
xrandr --output DISPLAY_NAME --set "Broadcast RGB" "Limited 16:235"
```

```bash
xrandr --output DISPLAY_NAME --set "Broadcast RGB" Full
```

Try adjusting brightness

```bash
xrandr --output DISPLAY_NAME --brightness VALUE
```

where VALUE is the brightness level; the default value is 1, but you can set other values. Decimal values are specified with a dot, for example, 0.9.

Adjusting Gamma

```bash
xrandr --output DISPLAY_NAME --gamma R:G:B
```
or 
```bash
xrandr --output DISPLAY_NAME --gamma RGB
```

Here you can set individual values for each component (R, G, B) or one value for all at once. The default value is 1; decimal values are specified with a dot, for example, 0.9.


## How to check if dithering is present or not

For Intel Arc and Intel UHD (11th generation and above), you can check for dithering by reading register 0x70030. In fact, it might be a different register if you have multiple monitors, but for simplicity, you should have only one monitor connected to the graphics card while reading the register.

```bash
sudo apt update
sudo apt install intel-gpu-tools
```

```bash
sudo intel_reg read 0x70030
```

My result is [0x00800140](https://www.rapidtables.com/convert/number/hex-to-binary.html?x=00800140), and we need the 5th bit from the right, so let's convert it to binary representation:</p>

000000001000000000000001010**0**0000</p>

The 5th bit from the right is 0, meaning dithering is not present. If it is equal to 1, then dithering is present.

Note: If you do not have Intel Arc or Intel UHD (11th generation and above), but you want to perform a similar experiment, ask a question on the forum. The community can help find the register address and its format for your Intel iGPU. However, this step is not necessary for building the kernel.
