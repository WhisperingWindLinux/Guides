# IOMFB Runtime Properties — Apple Silicon DCP

## Property table for DCP firmware version **13.5** (macOS Ventura / Asahi Linux)

Zero-based indexing. Use the value from the **ID** column for `applyProperty` calls.

| ID | Property Name | What it does (plain English) | Potential BVD benefit |
|----|--------------|------------------------------|----------------------|
| 0 | `blendOutCSCMethod` | Color space conversion method after blending layers | May affect smoothness of color transitions |
| 1 | `CMDegammaMethod` | Gamma processing method before blending | Affects contrast and shadow detail visibility |
| 2 | `requestPixelBacklightModulation` | Controls pixel-level backlight modulation | May eliminate backlight flickering |
| 3 | `pixelBacklightModulationForceState` | Forces backlight modulation on/off | Direct control over PWM-like backlight behavior |
| 4 | `DPBDriverOverrideLPFControls` | Overrides backlight driver low-pass filter | Reduces PWM-like flicker effects |
| 5 | `DPBDriverLPFControlValue` | Backlight filter smoothing value | Fine-tunes backlight smoothness |
| 6 | `DPBDriverLPFControl2Value` | Secondary backlight filter value | Additional smoothing parameter |
| 7 | `DPBDriverOverrideMaxSlopes` | Limits how fast backlight can change | Eliminates abrupt brightness jumps |
| 8 | `DPBDriverLPFMaxSlopeValue` | Maximum backlight change rate | Smoother brightness transitions |
| 9 | `DPBDriverMaxSlopeValue` | Maximum brightness slope | Controls transition smoothness |
| 10 | `DPBDriverOverrideBacklight` | Overrides backlight control entirely | Manual backlight control for stability |
| 11 | `DPBDriverBacklightValue` | Direct backlight level value | Precise backlight control |
| 12 | `enableGammaCorrection` | Toggles hardware gamma correction | Disabling may reduce processing artifacts |
| 13 | `brightnessCorrection` | Brightness level correction | May affect perceived screen stability |
| 14 | `brightnessCorrectionB` | Alternative brightness correction | Secondary brightness tuning |
| 15 | `brightnessLevel` | Current brightness level | Changes with keyboard brightness keys |
| 16 | `brightnessLevelMA` | Brightness level (MA variant) | Affects perceived brightness stability |
| 17 | `brightnessLevelIDAC` | Brightness level (IDAC variant) | Fine brightness control |
| 18 | `contrastEnhancerStrength` | Artificial contrast boosting | Disabling may reduce harsh image processing |
| 19 | `brightnessCompensationEnable` | Automatic brightness compensation | May cause subtle brightness fluctuations |
| 20 | `temperatureCompensationEnable` | Color adjustment based on display temperature | May cause subtle color shifts over time |
| **21** | **`enableDither`** | **Temporal dithering — flickering pixels to fake smoother gradients** | **PRIMARY TARGET — disabling eliminates high-frequency flicker that triggers BVD** |
| 22 | `enableDarkEnhancer` | Artificially boosts dark area visibility | Disabling may reduce noise in shadows |
| 23 | `enableADBEColorManager` | Apple's proprietary color processing | Disabling may simplify color pipeline |
| 24 | `enableWhitePointCorrection` | Adjusts white point to compensate for panel aging | May affect overall color comfort |
| 25 | `enable2DUniformityCorrection` | Corrects brightness unevenness across the screen | May reduce visible screen door effect |
| 26 | `enable2DTemperatureCorrection` | Corrects color unevenness due to heat | May reduce color shifts during use |
| 27 | `enableDefaultTemperatureCorrection` | Standard temperature-based color correction | May cause subtle color fluctuations |
| 28 | `uniformity2D` | Screen uniformity data | Controls brightness distribution |
| 29 | `enableAmbientLightSensorStatistics` | Collects ambient light data for auto-brightness | Auto-brightness may cause distracting changes |
| 30 | `enableSubPixelLayoutCompensation` | Adjusts for subpixel arrangement (RGB/BGR) | Affects text sharpness — important for eye strain |
| 31 | `enablePartialUpdate` | Only updates changed parts of screen | May reduce visual noise from full refreshes |
| 32 | `enableLatLeakComp` | Compensates for LCD pixel charge leakage | May affect image stability |
| 33 | `enableHighGrayOD` | Overdrive for bright gray transitions | May reduce ghosting in bright areas |
| 34 | `ambientBrightness` | Measured ambient light level | Reported by light sensor |
| 35 | `enableGamutMapper` | Color space mapping (sRGB → P3 etc.) | Disabling may simplify color pipeline |
| 36 | `enableStats` | Display statistics collection | Debug only |
| 37 | `maxAvgBpp` | Maximum average bits per pixel (compression) | Affects DSC compression quality |
| 38 | `maxPeakBpp` | Maximum peak bits per pixel | Affects image quality under compression |
| 39 | `clockRatio` | Display clock multiplier | Affects refresh timing |
| 40 | `debugUInt32` | Debug value | Debug only |
| 41 | `vrrDivisor` | Variable refresh rate timing divisor | Affects VRR smoothness |
| 42 | `vrrVersion` | VRR protocol version | Compatibility setting |
| 43 | `darkBoot` | Dark screen during boot | Boot-time display behavior |
| 44 | `wideGamutPassthrough` | Passes wide-color data unchanged | Bypasses color processing |
| 45 | `enableFiltersNoRewriteMode` | Filter processing optimization | May affect image quality |
| 46 | `enablePLCMode` | Panel self-refresh mode | Power saving — may cause flicker |
| 47 | `enableABG` | Anti-burn-in guard | Prevents static image retention |
| 48 | `enableABGDynamicMap` | Dynamic burn-in protection map | Active OLED protection |
| 49 | `enableDBM` | Dynamic brightness management | May cause unwanted brightness changes |
| 50 | `enableBIC` | Bilateral image correction | Edge-preserving smoothing |
| 51 | `enableBICUpdates` | BIC update frequency | How often image correction updates |
| 52 | `enableSBIM` | Spatial brightness image modulation | Local brightness adjustment |
| 53 | `enableGPDeringing` | Removes halos/ringing artifacts on GPU | Cleaner edges — less visual noise |
| 54 | `enableGPAlphaDiv` | GPU alpha division for transparency | Affects transparency rendering |
| 55 | `twilightStrength` | TrueTone-like warm color shift strength | Controls blue light reduction |
| 56 | `TLBrightOverride` | Brightness override (TrueTone-related) | Manual TrueTone brightness |
| 57 | `allocateDefaultFramebuffer` | Reserves memory for display output | Boot-time setting |
| 58 | `HardPowerEvent` | Hardware power state change event | Display wake/sleep handling |
| 59 | `ESDThresholdMS` | Electrostatic discharge detection threshold | Hardware protection |
| 60 | `enableKernelTests` | Kernel-level display tests | Debug only |
| 61 | `disableDisplayOptimize` | Disables display optimization passes | **May disable hidden processing that causes eye strain** |
| 62 | `ConfigureQMSVRR` | Quick Media Switching VRR config | Affects media playback smoothness |
| 63 | `enableEven60FPSFrames` | Forces consistent 60 FPS frame pacing | Eliminates micro-stutter at 60Hz |
| 64 | `panicOnHungSwap` | Kernel panic on stuck frame swap | Debug only |
| 65 | `fakeTconESDEvent` | Simulates ESD event for testing | Debug only |
| 66 | `registerTraceEnable` | Hardware register tracing | Debug only |
| 67 | `frameInfoTraceEnable` | Frame information tracing | Debug only |
| 68 | `QoSDebug` | Quality-of-service debugging | Debug only |
| 69 | `enablePowerGateDCS` | Powers down DCS when idle | Power saving — may cause wake-up flicker |
| 70 | `enableVideoCaching` | Caches video frames | Performance optimization |
| 71 | `dummySystemWantsCaching` | Test flag for caching | Debug only |
| 72 | `disableSystemCachingInput` | Disables input caching | Performance setting |
| 73 | `enableMockALSSCapture` | Fake ambient light sensor data | Debug only |
| 74 | `APTFixedRR` | Fixed refresh rate for APT mode | Locks refresh rate |
| 75 | `AODFixedRR` | Fixed refresh rate for Always-On Display | AOD stability |
| 76 | `AODWaitForWalkdown` | AOD transition delay | AOD smoothness |
| 77 | `enablePCCLogs` | Power Control Cluster logging | Debug only |
| 78 | `enableAPTLogs` | APT logging | Debug only |
| 79 | `enableAPT_CDFD` | APT CDFD feature | Advanced display feature |
| 80 | `enableAPT_PRC` | APT PRC feature | Advanced display feature |
| 81 | `enableAPTConfigExpired` | APT config expiration flag | Debug flag |
| 82 | `enableAPT_CA` | APT CA feature | Advanced display feature |
| 83 | `BLNitsCap` | Maximum backlight brightness in nits | Limits peak brightness |
| 84 | `RTPLCBLNitsCap` | RTPLC brightness cap | Brightness limiting |
| 85 | `RTPLCBLNitsScaler` | RTPLC brightness scaler | Brightness curve adjustment |
| 86 | `RTPLCNitsThresh` | RTPLC brightness threshold | Brightness trigger point |
| 87 | `enableAPTEvents` | APT event notifications | Debug only |
| 88 | `APTEventsMask` | APT event filter mask | Debug only |
| 89 | `enableNormalMode` | Normal display mode toggle | Returns display to standard mode |
| 90 | `enableAPTDefaultGray` | APT default gray level | Gray point calibration |
| 91 | `APTDefaultGrayValue` | APT gray value | Numerical gray level |
| 92 | `StatsTapPoint` | Where to capture statistics data | Debug only |
| 93 | `enableFrameInfoForRepeats` | Frame info for repeated frames | Debug only |
| 94 | `resetAPT_CA` | Resets APT CA state | Debug/troubleshooting |
| 95 | `publishChargeValues` | Publishes pixel charge data | Debug only |
| 96 | `resetChargeValues` | Resets charge tracking | Debug/troubleshooting |
| 97 | `panicOnChargeOOB` | Panic on out-of-bounds charge | Hardware protection |
| 98 | `panicOnChargeParity` | Panic on charge parity error | Hardware protection |
| 99 | `panicOnStuckPolarity` | Panic on stuck pixel polarity | Hardware protection |
| 100 | `limitRefreshRate` | Caps maximum refresh rate | **Limiting to 60Hz may reduce flicker sensitivity** |
| 101 | `midporchRegion` | Display timing porch region | Affects signal timing |
| 102 | `exportCRCAtVBI` | Exports checksum during blanking | Debug only |
| 103 | `IdleCachingMethod` | Caching strategy when display is idle | Power saving setting |
| 104 | `enablePCCCabal` | Power Control Cluster "coalition" mode | Advanced power management |
| 105 | `supportICCProfile` | ICC color profile support | Enables system color management |
| 106 | `supportHDR` | High Dynamic Range support | Enables HDR display modes |
| 107 | `enablePCCTrinity` | PCC Trinity architecture (M1/M2) | Power management for M1/M2 |
| 108 | `enablePCC` | Power Control Cluster main switch | **MASTER POWER SWITCH — may reduce EMI interference** |
| 109 | `enablePCC2D` | 2D Power Control Cluster | 2D power distribution |
| 110 | `bypassPCC2DLed` | Bypasses LED power control | Direct LED power path |
| 111 | `PCC2DLedAccelOut` | LED acceleration output | LED response tuning |
| 112 | `PCC2DLedLog` | LED power logging | Debug only |
| 113 | `disablePCC2DBrc` | Disables PCC2D brightness control | Manual brightness path |
| 114 | `disableTempComp` | Disables temperature compensation | **May prevent color shifts from device heating** |
| 115 | `modeBlm` | Backlight modulation mode | Controls PWM/DC dimming method |
| 116 | `PCCNormBrightOut` | Normalized brightness output | Brightness normalization |
| 117 | `BLMVLEDManual` | Manual LED backlight control | Direct backlight control |
| 118 | `BLMAHOutputFreq` | Backlight output frequency | **Changing PWM frequency may reduce flicker** |
| 119 | `BLMAHMode` | Backlight modulation type | DC vs PWM dimming selection |
| 120 | `BLMPLimitCfg` | Backlight power limit configuration | Prevents backlight overdrive |
| 121 | `enableBLMSloper` | Backlight transition smoothing | Smoother brightness changes |
| 122 | `enableLAC` | Local area contrast | Affects local dimming |
| 123 | `BLMAHUPCount` | Backlight ramp-up count | Brightness transition steps |
| 124 | `M3DiagsTimeout` | M3 diagnostic timeout | Debug only |
| 125 | `DisableBConBoot` | Disables brightness control at boot | Boot-time setting |
| 126 | `enableAPT_PDC` | APT PDC feature | Advanced display feature |
| 127 | `enableAPT_PDC_PM` | APT PDC power management | Power saving feature |
| 128 | `enableAPT_PDC_Repeat` | APT PDC repeat mode | Display refresh behavior |
| 129 | `PDCGlobalTemp` | PDC global temperature | Temperature tracking |
| 130 | `PDCSettleCount` | PDC stabilization count | Display settling time |
| 131 | `PDCSaveLongFrames` | PDC long frame handling | Frame timing |
| 132 | `PDCSaveRepeatUnstablePCC` | Handles unstable PCC repeats | Stability improvement |
| 133 | `PDCEntryTime` | PDC entry delay | Power state transition timing |
| 134 | `PDCExitTime` | PDC exit delay | Power state transition timing |
| 135 | `PDCAlwaysOnNits` | PDC always-on brightness | Minimum brightness in nits |
| 136 | `PDCContentSwitchCount` | Content switch counter | Frame type tracking |
| 137 | `pccLumaGammaFactor` | Luminance gamma factor for PCC | Gamma curve for power management |
| 138 | `PDCCutoffLux` | PDC ambient light cutoff | Auto-brightness threshold |
| 139 | `PDCExitCount` | PDC exit counter | Power state tracking |
| 140 | `overdriveCompCutoff` | Overdrive compensation threshold | Limits pixel overdrive |
| 141 | `enableAOT` | Always-On Tone mapping | HDR tone mapping |
| 142 | `vshHistVal` | Histogram value | Image statistics |
| 143 | `contrastEnhancerCorrectionFactor` | Contrast enhancer strength factor | Fine-tunes contrast processing |
| 144 | `proxScanPlan` | Proximity sensor scan plan | Sensor configuration |
| 145 | `proxScanPosition` | Proximity sensor position | Sensor location |
| 146 | `SWSTemp` | SWS temperature reading | Temperature monitoring |
| 147 | `forceAOTARMode` | Forces AOT AR mode | HDR mode override |
| 148 | `enableSPUC` | SPUC feature toggle | Display processing unit |
| 149 | `enableBLMAHOutputLog` | Backlight output logging | Debug only |
| 150 | `enableBLMAHStatsLog` | Backlight statistics logging | Debug only |
| 151 | `enableBLMStandby` | Backlight standby mode | Power saving for backlight |
| 152 | `enableVUC` | VUC feature toggle | Display processing |
| 153 | `limit_max_physical_brightness` | Hardware brightness limit | **Reducing max brightness may ease eye strain** |
| 154 | `enableRTPLC` | RTPLC feature toggle | Display processing |
| 155 | `enableRTPLCRT` | RTPLC RT feature | Real-time processing |
| 156 | `enableRTPLCFD` | RTPLC FD feature | Frame-dependent processing |
| 157 | `enableRTPLCNitsCap` | RTPLC brightness cap | Brightness limiting |
| 158 | `enableRTPLCPTC` | RTPLC PTC feature | Panel timing control |
| 159 | `enableSWS` | SWS feature toggle | Display processing |
| 160 | `enablePixelCapture` | Pixel capture for diagnostics | Debug only |
| 161 | `PixelCaptureConfig` | Pixel capture configuration | Debug only |
| 162 | `ADCLLoadAll` | ADCL full load | Calibration setting |
| 163 | `forceEnableACSS` | Forces ACSS enable | Advanced color feature |

## Key Properties for BVD

These properties have the highest potential impact on visual comfort:

| Priority | ID | Property | Recommended Value | Expected Effect |
|----------|----|----------|-------------------|-----------------|
| 🔴 Critical | **21** | `enableDither` | **0** | Eliminates temporal dithering flicker |
| 🟠 High | **12** | `enableGammaCorrection` | **0** | Reduces processing artifacts |
| 🟠 High | **108** | `enablePCC` | **0** | May reduce EMI from power circuitry |
| 🟡 Medium | **22** | `enableDarkEnhancer` | **0** | Reduces shadow noise |
| 🟡 Medium | **35** | `enableGamutMapper` | **0** | Simplifies color pipeline |
| 🟡 Medium | **61** | `disableDisplayOptimize` | **1** | Disables hidden processing |
| 🟢 Lower | **100** | `limitRefreshRate` | **60** | Locks to standard 60Hz |
| 🟢 Lower | **114** | `disableTempComp` | **1** | Prevents heat-related color shifts |
| 🟢 Lower | **153** | `limit_max_physical_brightness` | lower value | Reduces peak brightness |

## Notes

1. **Zero-based indexing** — confirmed on firmware 13.5
2. **Boolean values:** `0` = disable/off, `1` = enable/on
3. **Property order varies by DCP firmware version** — verify against your firmware before use
4. **Test one property at a time** — combinations may have unexpected effects
5. **LPM (Low Power Mode)** may achieve similar effects through power management

## References

- [Stillcolor](https://github.com/aiaf/Stillcolor) — macOS utility for disabling dithering via IORegistry
- [Asahi Linux DCP driver](https://github.com/AsahiLinux/linux) — DCP implementation for Linux on Apple Silicon
