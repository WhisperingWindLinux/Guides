# IOMFB Runtime Properties — Combined Reference

## DCP firmware version 13.5 (macOS Ventura / Asahi Linux)

**Sources:**
- **Table A** (priority): experimental data — External/Internal statuses (`✅/❌/⚠️`)
- **Table B**: names and descriptions from DCP firmware binary (indices may shift)

**Status legend:**
- ✅ = Working (status 0)
- ❌ = Not found (status 4)
- ⚠️ = Exists, but returned error (status 2)
- `~` in "Name (B)" column = presumed mapping by order
- ❓ = Mapping uncertain
---

| ID (A) | Name (A) | External | Internal | Name (B) | Description (B) | BVD Priority | Notes |
|--------|---------|----------|----------|---------|-------------|-------------|------------|
| 0 | `BlendOutputCSCMethod` | ✅ | ✅ | `blendOutCSCMethod` | Color conversion method after layer blending | — | |
| 1 | `CMDegammaMethod` | ✅ | ✅ | `CMDegammaMethod` | Gamma processing method before blending | — | |
| 2 | `requestPixelBacklightModulation` | ❌ | ✅ | `requestPixelBacklightModulation` | Hint to allow pixel-level temporal/spatial luminance modulation
   (likely tied to dithering or power optimization) | — | Internal only |
| 3 | `forcePixelBacklightModulation` | ❌ | ✅ | `pixelBacklightModulationForceState` | Forces that modulation mode on/off, overriding DCP policy | — | Internal only |
| 4 | `overrideLPFControls` | ❌ | ❌ | `DPBDriverOverrideLPFControls` | Overrides backlight driver low-pass filter | — | Not found on either |
| 5 | `LPFControlValue` | ❌ | ❌ | `DPBDriverLPFControlValue` | Backlight filter smoothing value | — | Not found on either |
| 6 | `LPFControl2Value` | ❌ | ❌ | `DPBDriverLPFControl2Value` | Secondary backlight filter value | — | Not found on either |
| 7 | `overrideDPBMaxSlopes` | ❌ | ❌ | `DPBDriverOverrideMaxSlopes` | Limits backlight change rate | — | Not found on either |
| 8 | `DPBLPFMaxSlopeValue` | ❌ | ❌ | `DPBDriverLPFMaxSlopeValue` | Maximum backlight change rate (LPF) | — | Not found on either |
| 9 | `DPBMaxSlopeValue` | ❌ | ❌ | `DPBDriverMaxSlopeValue` | Maximum brightness slope | — | Not found on either |
| 10 | `overrideBacklight` | ❌ | ❌ | `DPBDriverOverrideBacklight` | Complete override of backlight control | — | Not found on either |
| 11 | `backlightValue` | ❌ | ❌ | `DPBDriverBacklightValue` | Direct backlight level value | — | Not found on either |
| 12 | `enableGammaCorrection` | ❌ | ❌ | `enableGammaCorrection` | Toggles hardware gamma correction | 🟠 High | Not found on either |
| 13 | *(unknown)* | ✅ | ✅ | ~`brightnessCorrection` | Brightness level correction | — | Presumed ordering |
| 14 | *(unknown)* | ✅ | ✅ | ~`brightnessCorrectionB` | Alternative brightness correction | — | Presumed ordering |
| 15 | *(unknown)* | ✅ | ✅ | ~`brightnessLevel` | Current brightness level | — | Changes with brightness buttons |
| 16 | *(unknown)* | ✅ | ✅ | ~`brightnessLevelMA` | Brightness level (MA variant) | — | Presumed ordering |
| 17 | *(unknown)* | ✅ | ✅ | ~`brightnessLevelIDAC` | Fine brightness control (IDAC) | — | Presumed ordering |
| 18 | `IOMFBContrastEnhancerStrength` | ❌ | ✅ | `contrastEnhancerStrength` | Artificial contrast enhancement | — | Internal only |
| 19 | `IOMFBBrightnessCompensationEnable` | ⚠️ | ✅ | `brightnessCompensationEnable` | Automatic brightness compensation | — | Status 2 on external |
| 20 | `IOMFBTemperatureCompensationEnable` | ⚠️ | ✅ | `temperatureCompensationEnable` | Display temperature-based color correction | — | Status 2 on external |
| **21** | **`enableDither`** | ✅ | ✅ | **`enableDither`** | **Temporal dithering — flickering pixels to simulate smooth gradients** | 🔴 **Critical** | **PRIMARY BVD TARGET** |
| 22 | `enableDarkEnhancer` | ❌ | ✅ | `enableDarkEnhancer` | Artificial dark area enhancement | 🟡 Medium | Internal only |
| 23 | `enableADBEColorManager` | ❌ | ❌ | `enableADBEColorManager` | Apple proprietary color processing | — | Not found on either |
| 24 | `enableWhitePointCorrection` | ❌ | ❌ | `enableWhitePointCorrection` | Panel aging white point compensation | — | Not found on either |
| 25 | `enable2DTemperatureCorrection` | ⚠️ | ✅ | `enable2DUniformityCorrection` | Screen brightness uniformity correction | — | ❓ Possible name mismatch; Status 2 on external |
| 26 | `enable2DTemperatureCorrection` (dup) | ⚠️ | ✅ | `enable2DTemperatureCorrection` | Heat-induced color non-uniformity correction | — | Duplicate in Table A; Status 2 on external |
| 27 | `enableDefaultTemperatureCorrection` | ⚠️ | ✅ | `enableDefaultTemperatureCorrection` | Standard temperature-based color correction | — | Status 2 on external |
| 28 | `uniformity2D` | ⚠️ | ✅ | `uniformity2D` | Screen uniformity data | — | Status 2 on external |
| 29 | `enableAmbientLightSensorStatistics` | ❌ | ✅ | `enableAmbientLightSensorStatistics` | Ambient light sensor data collection | — | Internal only |
| 30 | `enableSubPixelLayoutCompensation` | ❌ | ❌ | `enableSubPixelLayoutCompensation` | Subpixel layout correction (RGB/BGR) | — | Not found on either |
| 31 | `enablePartialUpdate` | ❌ | ❌ | `enablePartialUpdate` | Updates only changed screen areas | — | Not found on either |
| 32 | `enableLatLeakComp` | ❌ | ❌ | `enableLatLeakComp` | LCD pixel charge leakage compensation | — | Not found on either |
| 33 | `enableHighGrayOD` | ❌ | ❌ | `enableHighGrayOD` | Overdrive for bright gray transitions | — | Not found on either |
| 34 | *(unknown)* | ✅ | ✅ | ~`ambientBrightness` | Measured ambient light level | — | Presumed ordering |
| 35 | `enableGamutMapper` | ❌ | ❌ | `enableGamutMapper` | Color space mapping (sRGB → P3, etc.) | 🟡 Medium | Not found on either |
| 36 | `enableStats` | ❌ | ❌ | `enableStats` | Display statistics collection | — | Debug only |
| 37 | *(unknown)* | ✅ | ✅ | ~`maxAvgBpp` | Maximum average bits per pixel (compression) | — | Presumed ordering |
| 38 | *(unknown)* | ✅ | ✅ | ~`maxPeakBpp` | Maximum peak bits per pixel | — | Presumed ordering |
| 39 | *(unknown)* | ✅ | ✅ | ~`clockRatio` | Display clock multiplier | — | Presumed ordering |
| 40 | *(unknown)* | ✅ | ✅ | ~`debugUInt32` | Debug value | — | Debug only |
| 41 | `VRRDivisor` | ❌ | ❌ | `vrrDivisor` | Variable refresh rate timing divisor | — | Not found on either |
| 42 | `VRRVersion` | ❌ | ❌ | `vrrVersion` | VRR protocol version | — | Not found on either |
| 43 | *(unknown)* | ✅ | ✅ | ~`darkBoot` | Dark screen during boot | — | Presumed ordering |
| 44 | `IOMFBWideGamutPassthrough` | ❌ | ❌ | `wideGamutPassthrough` | Passes wide-color data unchanged | — | Not found on either |
| 45 | `enableFiltersNoRewriteMode` | ❌ | ❌ | `enableFiltersNoRewriteMode` | Filter processing optimization | — | Not found on either |
| 46 | `enablePLCMode` | ❌ | ❌ | `enablePLCMode` | Panel self-refresh mode | — | Not found on either |
| 47 | `enableABGMode` | ❌ | ❌ | `enableABG` | Burn-in protection | — | Not found on either |
| 48 | `enableABGDynamicMap` | ❌ | ❌ | `enableABGDynamicMap` | Dynamic burn-in protection map (OLED) | — | Not found on either |
| 49 | `enableDBMMode` | ❌ | ❌ | `enableDBM` | Dynamic brightness management | — | Not found on either |
| 50 | `enableBICMode` | ❌ | ❌ | `enableBIC` | Bilateral image correction | — | Not found on either |
| 51 | `enableBICUpdates` | ❌ | ❌ | `enableBICUpdates` | BIC update frequency | — | Not found on either |
| 52 | `enableSBIM` | ❌ | ❌ | `enableSBIM` | Spatial local brightness modulation | — | Not found on either |
| 53 | `enableGPDeringing` | ❌ | ❌ | `enableGPDeringing` | Removes GPU halo/ringing artifacts | — | Not found on either |
| 54 | `enableGPAlphaDiv` | ❌ | ❌ | `enableGPAlphaDiv` | GPU alpha channel division for transparency | — | Not found on either |
| 55 | `twilightStrength` | ❌ | ❌ | `twilightStrength` | Warm color shift strength (TrueTone) | — | Not found on either |
| 56 | `TLBrightOverride` | ❌ | ❌ | `TLBrightOverride` | TrueTone brightness override | — | Not found on either |
| 57 | `allocateDefaultFramebuffer` | ❌ | ❌ | `allocateDefaultFramebuffer` | Reserves memory for display output | — | Boot-time |
| 58 | `debugHardPowerEvent` | ❌ | ❌ | `HardPowerEvent` | Hardware power change event | — | Not found on either |
| 59 | `ESDThresholdMS` | ❌ | ❌ | `ESDThresholdMS` | Electrostatic discharge detection threshold | — | Not found on either |
| 60 | `EnableKernelTests` | ❌ | ❌ | `enableKernelTests` | Kernel-level display tests | — | Debug only |
| 61 | *(unknown)* | ✅ | ✅ | ~`disableDisplayOptimize` | Disables display optimization passes | 🟡 Medium | Presumed ordering |
| 62 | *(unknown)* | ✅ | ✅ | ~`ConfigureQMSVRR` | Quick Media Switching VRR configuration | — | Presumed ordering |
| 63 | `EnableEven60FPSFrames` | ❌ | ❌ | `enableEven60FPSFrames` | Forces uniform 60 FPS pacing | — | Not found on either |
| 64 | `PanicOnHungSwap` | ❌ | ❌ | `panicOnHungSwap` | Kernel panic on stuck frame swap | — | Debug only |
| 65 | `FakeTconESDEvent` | ❌ | ❌ | `fakeTconESDEvent` | Simulates ESD event for testing | — | Debug only |
| 66 | *(unknown)* | ✅ | ✅ | ~`registerTraceEnable` | Hardware register tracing | — | Debug only |
| 67 | *(unknown)* | ✅ | ✅ | ~`frameInfoTraceEnable` | Frame information tracing | — | Debug only |
| 68 | *(unknown)* | ✅ | ✅ | ~`QoSDebug` | Quality of service debugging | — | Debug only |
| 69 | `enablePowerGateDCS` | ❌ | ❌ | `enablePowerGateDCS` | Disables DCS in idle mode | — | Not found on either |
| 70 | `enableVideoCaching` | ❌ | ❌ | `enableVideoCaching` | Video frame caching | — | Not found on either |
| 71 | `dummySystemWantsCaching` | ❌ | ❌ | `dummySystemWantsCaching` | Test caching flag | — | Debug only |
| 72 | `disableSystemCachingInput` | ❌ | ❌ | `disableSystemCachingInput` | Disables input data caching | — | Not found on either |
| 73 | `enableMockALSSCapture` | ❌ | ❌ | `enableMockALSSCapture` | Fake ambient light sensor data | — | Debug only |
| 74 | *(unknown)* | ✅ | ✅ | ~`APTFixedRR` | Fixed refresh rate for APT | — | Presumed ordering |
| 75 | *(unknown)* | ✅ | ✅ | ~`AODFixedRR` | Fixed frequency for Always-On Display | — | Presumed ordering |
| 76 | *(unknown)* | ✅ | ✅ | ~`AODWaitForWalkdown` | AOD transition delay | — | Presumed ordering |
| 77 | *(unknown)* | ✅ | ✅ | ~`enablePCCLogs` | Power Control Cluster logging | — | Debug only |
| 78 | *(unknown)* | ✅ | ✅ | ~`enableAPTLogs` | APT logging | — | Debug only |
| 79 | *(unknown)* | ✅ | ✅ | ~`enableAPT_CDFD` | APT CDFD function | — | Presumed ordering |
| 80 | *(unknown)* | ✅ | ✅ | ~`enableAPT_PRC` | APT PRC function | — | Presumed ordering |
| 81 | *(unknown)* | ✅ | ✅ | ~`enableAPTConfigExpired` | APT configuration expiration flag | — | Debug flag |
| 82 | *(unknown)* | ✅ | ✅ | ~`enableAPT_CA` | APT CA function | — | Presumed ordering |
| 83 | `BLNitsCap` | ❌ | ✅ | `BLNitsCap` | Maximum backlight brightness in nits | — | Internal only |
| 84 | `RTPLCBLNitsCap` | ❌ | ❌ | `RTPLCBLNitsCap` | RTPLC brightness limit | — | Not found on either |
| 85 | `RTPLCBLNitsScaler` | ❌ | ❌ | `RTPLCBLNitsScaler` | RTPLC brightness scaling | — | Not found on either |
| 86 | `RTPLCNitsThresh` | ❌ | ❌ | `RTPLCNitsThresh` | RTPLC brightness threshold | — | Not found on either |
| 87 | *(unknown)* | ✅ | ✅ | ~`enableAPTEvents` | APT event notifications | — | Debug only |
| 88 | *(unknown)* | ✅ | ✅ | ~`APTEventsMask` | APT event filter mask | — | Debug only |
| 89 | *(unknown)* | ✅ | ✅ | ~`enableNormalMode` | Switch to standard display mode | — | Presumed ordering |
| 90 | *(unknown)* | ✅ | ✅ | ~`enableAPTDefaultGray` | Default gray level for APT | — | Presumed ordering |
| 91 | *(unknown)* | ✅ | ✅ | ~`APTDefaultGrayValue` | APT gray level numeric value | — | Presumed ordering |
| 92 | *(unknown)* | ✅ | ✅ | ~`StatsTapPoint` | Statistics capture point | — | Debug only |
| 93 | *(unknown)* | ✅ | ✅ | ~`enableFrameInfoForRepeats` | Frame info for repeated frames | — | Debug only |
| 94 | *(unknown)* | ✅ | ✅ | ~`resetAPT_CA` | Reset APT CA state | — | Debug/troubleshooting |
| 95 | *(unknown)* | ✅ | ✅ | ~`publishChargeValues` | Publishes pixel charge data | — | Debug only |
| 96 | *(unknown)* | ✅ | ✅ | ~`resetChargeValues` | Reset charge tracking | — | Debug/troubleshooting |
| 97 | *(unknown)* | ✅ | ✅ | ~`panicOnChargeOOB` | Panic on charge out-of-bounds | — | Hardware protection |
| 98 | *(unknown)* | ✅ | ✅ | ~`panicOnChargeParity` | Panic on charge parity error | — | Hardware protection |
| 99 | *(unknown)* | ✅ | ✅ | ~`panicOnStuckPolarity` | Panic on stuck pixel polarity | — | Hardware protection |
| 100 | *(unknown)* | ✅ | ✅ | ~`limitRefreshRate` | Limits maximum refresh rate | 🟢 Lower | Presumed ordering |
| 101 | `SkipRegion` | ❌ | ❌ | `midporchRegion` | ❓ Display timing region | — | ❓ Names do not match |
| 102 | `ExportCRCAtVBI` | ❌ | ❌ | `exportCRCAtVBI` | Export checksum during blanking pulse | — | Debug only |
| 103 | *(unknown)* | ✅ | ✅ | ~`IdleCachingMethod` | Display idle caching strategy | — | Presumed ordering |
| 104 | `PCCCabalEnable` | ❌ | ✅ | `enablePCCCabal` | Power Control Cluster "coalition" mode | — | Internal only |
| 105 | *(unknown)* | ✅ | ✅ | ~`supportICCProfile` | ICC color profile support | — | Presumed ordering |
| 106 | `IOMFBSupportsHDR10Plus` | ❌ | ❌ | `supportHDR` | ❓ HDR support | — | ❓ Names do not match exactly |
| 107 | `PCCTrinityEnable` | ❌ | ✅ | `enablePCCTrinity` | PCC Trinity architecture (M1/M2) | — | Internal only |
| 108 | `PCCEnable` | ❌ | ✅ | `enablePCC` | Power Control Cluster main switch | 🟠 High | Internal only |
| 109 | `PCC2DEnable` | ❌ | ✅ | `enablePCC2D` | 2D Power Control Cluster | — | Internal only |
| 110 | `BypassPCC2DLed` | ❌ | ❌ | `bypassPCC2DLed` | Bypasses LED power management | — | Not found on either |
| 111 | `PCC2DLedAccelOut` | ❌ | ❌ | `PCC2DLedAccelOut` | LED acceleration output | — | Not found on either |
| 112 | `PCC2DLedAccelLog` | ❌ | ❌ | `PCC2DLedLog` | LED power logging | — | Debug only |
| 113 | `DisablePCC2DBrc` | ❌ | ❌ | `disablePCC2DBrc` | Disables PCC2D brightness control | — | Not found on either |
| 114 | `DisableTempComp` | ❌ | ❌ | `disableTempComp` | Disables temperature compensation | 🟢 Lower | Not found on either |
| 115 | `ModeBlm` | ❌ | ❌ | `modeBlm` | Backlight modulation mode (PWM/DC) | — | Not found on either |
| 116 | `IOMFBTestBacklightDimValue` | ❌ | ✅ | `PCCNormBrightOut` | ❓ Normalized brightness output | — | ❓ Names do not match; Internal only |
| 117 | `BLMVLEDManual` | ❌ | ✅ | `BLMVLEDManual` | Manual LED backlight control | — | Internal only |
| 118 | `BLMAHOutputFreq` | ❌ | ✅ | `BLMAHOutputFreq` | Backlight output frequency | 🟠 High | Internal only; PWM frequency change |
| 119 | `BLMAHMode` | ❌ | ✅ | `BLMAHMode` | Backlight modulation type (DC vs PWM) | — | Internal only |
| 120 | `BLMPLimitCfg` | ❌ | ✅ | `BLMPLimitCfg` | Backlight power limit configuration | — | Internal only |
| 121 | `enableBLMSloper` | ❌ | ✅ | `enableBLMSloper` | Backlight transition smoothing | — | Internal only |
| 122 | `enableLAC` | ❌ | ✅ | `enableLAC` | Local area contrast | — | Internal only |
| 123 | `BLMAHUPCount` | ❌ | ✅ | `BLMAHUPCount` | Brightness ramp-up step count | — | Internal only |
| 124 | `M3DiagsTimeout` | ❌ | ❌ | `M3DiagsTimeout` | M3 diagnostics timeout | — | Debug only |
| 125 | `DisableBConBoot` | ❌ | ✅ | `DisableBConBoot` | Disables brightness control at boot | — | Internal only |
| 126 | *(unknown)* | ✅ | ✅ | ~`enableAPT_PDC` | APT PDC function | — | Presumed ordering |
| 127 | *(unknown)* | ✅ | ✅ | ~`enableAPT_PDC_PM` | APT PDC power management | — | Presumed ordering |
| 128 | `APTPDCEnableRepeat` | ❌ | ❌ | `enableAPT_PDC_Repeat` | APT PDC repeat mode | — | Not found on either |
| 129 | `PDCGlobalTemp` | ❌ | ✅ | `PDCGlobalTemp` | PDC global temperature | — | Internal only |
| 130 | *(unknown)* | ✅ | ✅ | ~`PDCSettleCount` | PDC stabilization time | — | Presumed ordering |
| 131 | *(unknown)* | ✅ | ✅ | ~`PDCSaveLongFrames` | PDC long frame processing | — | Presumed ordering |
| 132 | *(unknown)* | ✅ | ✅ | ~`PDCSaveRepeatUnstablePCC` | Unstable PCC repeat handling | — | Presumed ordering |
| 133 | `PDCEntryTime` | ❌ | ❌ | `PDCEntryTime` | PDC entry delay | — | Not found on either |
| 134 | `PDCExitTime` | ❌ | ❌ | `PDCExitTime` | PDC exit delay | — | Not found on either |
| 135 | `PDCAlwaysOnNits` | ❌ | ❌ | `PDCAlwaysOnNits` | Always-On brightness in nits | — | Not found on either |
| 136 | `PDCContentSwitchCount` | ❌ | ❌ | `PDCContentSwitchCount` | Content switch counter | — | Not found on either |
| 137 | `pccLumaGammaFactor` | ❌ | ❌ | `pccLumaGammaFactor` | Brightness gamma factor for PCC | — | Not found on either |
| 138 | `PDCCutoffLux` | ❌ | ❌ | `PDCCutoffLux` | Ambient light threshold for PDC | — | Not found on either |
| 139 | `PDCExitCount` | ❌ | ❌ | `PDCExitCount` | PDC exit counter | — | Not found on either |
| 140 | `overdriveCompCutoff` | ❌ | ✅ | `overdriveCompCutoff` | Overdrive compensation threshold | — | Internal only |
| 141 | *(unknown)* | ✅ | ✅ | ~`enableAOT` | Always-On Tone mapping (HDR) | — | Presumed ordering |
| 142 | `VSHHistVal` | ❌ | ❌ | `vshHistVal` | Histogram value | — | Not found on either |
| 143 | `CECorrectionFactor` | ❌ | ✅ | `contrastEnhancerCorrectionFactor` | Contrast enhancement strength factor | — | Internal only |
| 144 | `ProxScanPlan` | ⚠️ | ⚠️ | `proxScanPlan` | Proximity sensor scan plan | — | Status 2 on both |
| 145 | *(unknown)* | ✅ | ✅ | ~`proxScanPosition` | Proximity sensor position | — | Presumed ordering |
| 146 | `SWSTemp` | ❌ | ❌ | `SWSTemp` | SWS temperature | — | Not found on either |
| 147 | `ForceAOTARMode` | ❌ | ❌ | `forceAOTARMode` | Force AOT AR mode | — | Not found on either |
| 148 | `SPUCEnable` | ❌ | ❌ | `enableSPUC` | SPUC function switch | — | Not found on either |
| 149 | `BLMAHOutputLogEnable` | ❌ | ✅ | `enableBLMAHOutputLog` | Backlight output logging | — | Internal only; Debug only |
| 150 | `BLMAHStatsLogEnable` | ❌ | ✅ | `enableBLMAHStatsLog` | Backlight statistics logging | — | Internal only; Debug only |
| 151 | `BLMStandbyEnable` | ❌ | ✅ | `enableBLMStandby` | Backlight standby mode | — | Internal only |
| 152 | `VUCEnable` | ❌ | ❌ | `enableVUC` | VUC switch | — | Not found on either |
| 153 | `limit_max_physical_brightness` | ❌ | ❌ | `limit_max_physical_brightness` | Hardware brightness limit | 🟢 Lower | Not found on either |
| 154 | `RTPLCEnable` | ❌ | ❌ | `enableRTPLC` | RTPLC switch | — | Not found on either |
| 155 | `RTPLCEnableRT` | ❌ | ❌ | `enableRTPLCRT` | RTPLC RT function | — | Not found on either |
| 156 | `RTPLCEnableFD` | ❌ | ❌ | `enableRTPLCFD` | Frame-dependent processing | — | Not found on either |
| 157 | `RTPLCEnableNitsCap` | ❌ | ❌ | `enableRTPLCNitsCap` | RTPLC brightness limit | — | Not found on either |
| 158 | `RTPLCEnablePredThreshCross` | ❌ | ❌ | `enableRTPLCPTC` | Panel timing control | — | Not found on either |
| 159 | `enableSWS` | ❌ | ❌ | `enableSWS` | SWS switch | — | Not found on either |
| 160 | *(unknown)* | ✅ | ✅ | ~`enablePixelCapture` | Pixel capture for diagnostics | — | Debug only |
| 161 | *(unknown)* | ✅ | ✅ | ~`PixelCaptureConfig` | Pixel capture configuration | — | Debug only |
| 162 | *(unknown)* | ✅ | ✅ | ~`ADCLLoadAll` | Full ADCL load | — | Calibration |
| 163 | `forceEnableACSS` | ❌ | ❌ | `forceEnableACSS` | Force enable ACSS | — | Not found on either |
| 164 | `gamutConversionPostBlend` | ❌ | ❌ | — | — | — | Not in Table B |
| 165 | `gamutConversionPipe0` | ❌ | ❌ | — | — | — | Not in Table B |
| 166 | `gamutConversionPipe1` | ❌ | ❌ | — | — | — | Not in Table B |
| 167 | `SystemIdlenessEnabled` | ❌ | ❌ | — | — | — | Not in Table B |
| 168 | `SystemIdlenessThreshold` | ❌ | ❌ | — | — | — | Not in Table B |
| 169 | `VRRIdleEnabled` | ❌ | ❌ | — | — | — | Not in Table B |
| 170 | `VRRIdleThreshold` | ❌ | ❌ | — | — | — | Not in Table B |
| 171 | `VRRBurnInEnabled` | ✅ | ❌ | — | — | — | External only; Not in Table B |
| 172 | `VRRBurnInThreshold` | ❌ | ❌ | — | — | — | Not in Table B |
| 173 | `VRRBurnInCooldownEnabled` | ❌ | ❌ | — | — | — | Not in Table B |
| 174 | `VRRBurnInCooldownThreshold` | ❌ | ❌ | — | — | — | Not in Table B |
| 175 | `PowerGateADPIdleEnabled` | ❌ | ❌ | — | — | — | Not in Table B |
| 176 | `PowerGateADPIdleThreshold` | ❌ | ❌ | — | — | — | Not in Table B |
| 177 | `RuntimeProperty::COUNT` | ❌ | ❌ | — | — | — | Sentinel; end of enumeration |

---

## Conflicts and Uncertainties

The following entries require manual verification — names in tables do not match:

| ID | Name in Table A (experiment) | Name in Table B (binary) | Comment |
|----|-------------------------------|---------------------------|-------------|
| 25 | `enable2DTemperatureCorrection` | `enable2DUniformityCorrection` | B appears before `enable2DTemperatureCorrection` (ID 26) — possible shift |
| 101 | `SkipRegion` | `midporchRegion` | Unlikely to be the same, or shift |
| 106 | `IOMFBSupportsHDR10Plus` | `supportHDR` | Different names, likely the same property |
| 116 | `IOMFBTestBacklightDimValue` | `PCCNormBrightOut` | Completely different names — possible shift in B |

## BVD Properties (Summary)

| Priority | ID | Name | External | Internal | Recommended Value | Expected Effect |
|-----------|----|-----|----------|----------|-----------------------|-----------------|
| 🔴 Critical | **21** | `enableDither` | ✅ | ✅ | **0** | Eliminates temporal dithering flicker |
| 🟠 High | **12** | `enableGammaCorrection` | ❌ | ❌ | 0 | Reduces processing artifacts (not found) |
| 🟠 High | **108** | `enablePCC` | ❌ | ✅ | 0 | Reduces EMI from power circuitry (Internal only) |
| 🟠 High | **118** | `BLMAHOutputFreq` | ❌ | ✅ | — | PWM frequency change (Internal only) |
| 🟡 Medium | **22** | `enableDarkEnhancer` | ❌ | ✅ | 0 | Reduces noise in dark areas (Internal only) |
| 🟡 Medium | **35** | `enableGamutMapper` | ❌ | ❌ | 0 | Simplifies color pipeline (not found) |
| 🟡 Medium | **61** | *(unknown)* ~`disableDisplayOptimize` | ✅ | ✅ | 1 | Disables hidden processing |
| 🟢 Lower | **100** | *(unknown)* ~`limitRefreshRate` | ✅ | ✅ | 60 | Locks to 60Hz |
| 🟢 Lower | **114** | `DisableTempComp` | ❌ | ❌ | 1 | Disables thermal correction (not found) |
| 🟢 Lower | **153** | `limit_max_physical_brightness` | ❌ | ❌ | low | Reduces peak brightness (not found) |

---

*Table A indices (experimental) — source of truth. Names and descriptions from Table B are matched by name match or presumed by order (`~`). Properties from Table A with IDs 164–177 are absent from Table B — likely added after the binary version or specific to this firmware.*
