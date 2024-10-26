## Enable the zink render

Add the following lines to ~/.profile:

```bash
xrandr --output DP-1 --set "max bpc" 6           # 8, if your monitor is true 8-bit
xrandr --output DP-1 --set "Broadcast RGB" Full

export LIBGL_ALWAYS_SOFTWARE=0                   # optional, but useful for comparing modes.
export LIBGL_DRI3_DISABLE=1
export LIBGL_DRI2_DISABLE=1
```

```bash
$ inxi -G
Graphics:
  Device-1: Intel DG2 [Arc A770] driver: i915 v: kernel
  Display: x11 server: X.Org v: 21.1.11 with: Xwayland v: 23.2.6 driver: X:
    loaded: modesetting unloaded: fbdev,vesa dri: zink gpu: i915
    resolution: 1920x1080~60Hz
  API: EGL v: 1.5 drivers: iris,swrast,zink
    platforms: gbm,x11,surfaceless,device
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: mesa v: N/A renderer: zink
    Vulkan 1.3(Intel Arc A770 Graphics (DG2) (INTEL_OPEN_SOURCE_MESA))
```
