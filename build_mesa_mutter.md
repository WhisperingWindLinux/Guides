Ubuntu 24.04.1 LTS

## Install deps

sudo apt-get build-dep mesa
sudo apt install libllvmspirv lib-18-dev cmake libclang-dev cbindgen libgraphene-1.0-dev libgdk-pixbuf2.0-dev libpango1.0-dev gsettings-desktop-schemas-dev libxkbcommon-dev libatk1.0-dev libdbus-1-dev libcolord-dev liblcms2-dev libeis-dev libgtk-4-dev libxtst-dev  libxkbfile-dev libxkbcommon-x11-dev libxcb-res0-dev libgnome-desktop-4-dev libcanberra-dev libgudev-1.0-dev libinput-dev libstartup-notification0-dev libpipewire-0.3-dev libgirepository1.0-dev libspice-client-gtk-3.0-dev python3-dbusmock xvfb-run libunwind-dev

## Build Mesa 

git clone --depth 1 --branch 24.01_nodither https://github.com/WhisperingWindLinux/Mesa.git

sudo cp '/usr/lib/llvm-17/lib/clang/17/include/opencl-c-base.h' /usr/local/include/
sudo cp '/usr/lib/llvm-17/lib/clang/17/include/opencl-c.h' /usr/local/include/     

meson setup builddir/
meson compile -C builddir/
sudo meson install -C builddir/

## Build Mutter

git clone https://gitlab.gnome.org/GNOME/mutter.git
cd mutter
git checkout 46.2

meson setup builddir/
meson compile -C builddir/
sudo meson install -C builddir/

Replace the following system files:
/usr/libexec/mutter-x11-frames 
/usr/libexec/mutter-restart-helper
