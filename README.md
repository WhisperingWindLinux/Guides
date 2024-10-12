# This guide contains a description of applying the fix that disables dithering in 6-bit mode for Intel iGPU/GPU in Linux

## Foreword (this is really important, please don't skip this section)

This solution is particularly useful if you have a 6-bit+FRC monitor and you want to experiment with the 6-bit mode. For 8-bit color depth and above, this fix is not needed because Intel iGPU/GPU dithering is not present.

Please note that your monitor should be connected via DisplayPort to your Intel iGPU/GPU. There are some exceptions, such as Intel Arc, where the HDMI port internally route through DisplayPort. Similarly, some motherboards may have a similar design for the iGPU, but this is relatively rare.

Most laptop displays are internally connected via DisplayPort.

I've developed and tested this on kernel 6.10 with Ubuntu 24.04.1 LTS, and while it should work on other versions, I'm not entirely certain about the minimum Ubuntu version that supports this kernel. 

I haven't tested the build guide on other Debian-based operating systems, but in theory, it should work. If you're using a non-Debian based OS, you should look up a guide specific to building the kernel for your distro.

X11 provides an easy way to switch color depth using xrandr. Other environments may not support color depth selection, such as Wayland. Please use X11.

The fix has been tested on the Intel Alder Lake UHD 48EU (Xe) i5-12450H and the Intel Arc A770, but in theory, it should work for all Intel iGPUs/GPUs.

## How to build the kernel

This is not the most comprehensive guide for building a kernel. For example, it omits issues related to digital signatures. It means that the kernel is not signed and will not boot with Secure Boot enabled. Secure Boot is this is the BIOS/UEFI option. **I don't know if disabling Secure Boot (this is the BIOS/UEFI option) will cause any problems if you already have some operating systems previously installed with this option enabled.**

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

Note: xrandr uses X11, so it will not work fully in other environments.

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

Try switching between Limited Range / Full Range

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

Try adjusting gamma

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

Link to the Intel manual where you can find information on registers (including PIPE_MISC, which we worked with above: https://cdrdv2-public.intel.com/703047/intel-gfx-prm-osrc-tgl-vol-02-c-command-reference-registers-part-2.pdf, page 688).

Note: If you do not have Intel Arc or Intel UHD (11th generation and above), but you want to perform a similar experiment, ask a question on the forum. The community can help find the register address and its format for your Intel iGPU. However, this step is not necessary for building the kernel.
