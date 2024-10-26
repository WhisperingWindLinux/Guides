# Ubuntu 24.04.1 LTS

## Install deps

```bash
sudo apt-get build-dep mesa
```
```bash
sudo apt install libllvmspirv lib-18-dev cmake libclang-dev cbindgen libgraphene-1.0-dev libgdk-pixbuf2.0-dev libpango1.0-dev gsettings-desktop-schemas-dev libxkbcommon-dev libatk1.0-dev libdbus-1-dev libcolord-dev liblcms2-dev libeis-dev libgtk-4-dev libxtst-dev  libxkbfile-dev libxkbcommon-x11-dev libxcb-res0-dev libgnome-desktop-4-dev libcanberra-dev libgudev-1.0-dev libinput-dev libstartup-notification0-dev libpipewire-0.3-dev libgirepository1.0-dev libspice-client-gtk-3.0-dev python3-dbusmock xvfb-run libunwind-dev
```

## Build Mesa 

```bash
git clone --depth 1 --branch 24.01_nodither https://github.com/WhisperingWindLinux/Mesa.git
```

```bash
sudo cp '/usr/lib/llvm-17/lib/clang/17/include/opencl-c-base.h' /usr/local/include/
sudo cp '/usr/lib/llvm-17/lib/clang/17/include/opencl-c.h' /usr/local/include/
```

```bash
meson setup builddir/
meson compile -C builddir/
sudo meson install -C builddir/
```

## Build Mutter

```bash
git clone https://gitlab.gnome.org/GNOME/mutter.git
cd mutter
git checkout 46.2
```

```bash
meson setup builddir/
meson compile -C builddir/
sudo meson install -C builddir/
```

Replace the following system files:

```bash
/usr/libexec/mutter-x11-frames 
/usr/libexec/mutter-restart-helper
```
