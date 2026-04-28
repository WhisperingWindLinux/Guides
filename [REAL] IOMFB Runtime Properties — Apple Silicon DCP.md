# IOMFB Runtime Properties — External vs Internal Display Comparison

## DCP firmware version 13.5 (macOS Ventura / Asahi Linux)

### Legend
- ✅ = Works on this display type (status 0)
- ❌ = Property not found for this display type (status 4)
- ⚠️ = Property exists but failed (status 2)
- — = Not tested

| Selector | Property Name | External | Internal | Notes |
|----------|--------------|----------|----------|-------|
| 0 | `BlendOutputCSCMethod` | ✅ | ✅ | Universal |
| 1 | `CMDegammaMethod` | ✅ | ✅ | Universal |
| 2 | `requestPixelBacklightModulation` | ❌ | ✅ | Internal only |
| 3 | `forcePixelBacklightModulation` | ❌ | ✅ | Internal only |
| 4 | `overrideLPFControls` | ❌ | ❌ | Not found on either |
| 5 | `LPFControlValue` | ❌ | ❌ | Not found on either |
| 6 | `LPFControl2Value` | ❌ | ❌ | Not found on either |
| 7 | `overrideDPBMaxSlopes` | ❌ | ❌ | Not found on either |
| 8 | `DPBLPFMaxSlopeValue` | ❌ | ❌ | Not found on either |
| 9 | `DPBMaxSlopeValue` | ❌ | ❌ | Not found on either |
| 10 | `overrideBacklight` | ❌ | ❌ | Not found on either |
| 11 | `backlightValue` | ❌ | ❌ | Not found on either |
| 12 | `enableGammaCorrection` | ❌ | ❌ | Not found on either |
| 13 | *(unknown)* | ✅ | ✅ | Universal |
| 14 | *(unknown)* | ✅ | ✅ | Universal |
| 15 | *(unknown)* | ✅ | ✅ | Universal |
| 16 | *(unknown)* | ✅ | ✅ | Universal |
| 17 | *(unknown)* | ✅ | ✅ | Universal |
| 18 | `IOMFBContrastEnhancerStrength` | ❌ | ✅ | Internal only |
| 19 | `IOMFBBrightnessCompensationEnable` | ⚠️ | ✅ | Status 2 on external |
| 20 | `IOMFBTemperatureCompensationEnable` | ⚠️ | ✅ | Status 2 on external |
| **21** | **`enableDither`** | ✅ | ✅ | **PRIMARY BVD TARGET** |
| 22 | `enableDarkEnhancer` | ❌ | ✅ | Internal only |
| 23 | `enableADBEColorManager` | ❌ | ❌ | Not found on either |
| 24 | `enableWhitePointCorrection` | ❌ | ❌ | Not found on either |
| 25 | `enable2DTemperatureCorrection` | ⚠️ | ✅ | Deprecated; status 2 on external |
| 26 | `enable2DTemperatureCorrection` (dup) | ⚠️ | ✅ | Duplicate entry |
| 27 | `enableDefaultTemperatureCorrection` | ⚠️ | ✅ | Status 2 on external |
| 28 | `uniformity2D` | ⚠️ | ✅ | Status 2 on external |
| 29 | `enableAmbientLightSensorStatistics` | ❌ | ✅ | Internal only |
| 30 | `enableSubPixelLayoutCompensation` | ❌ | ❌ | Not found on either |
| 31 | `enablePartialUpdate` | ❌ | ❌ | Not found on either |
| 32 | `enableLatLeakComp` | ❌ | ❌ | Not found on either |
| 33 | `enableHighGrayOD` | ❌ | ❌ | Not found on either |
| 34 | *(unknown)* | ✅ | ✅ | Universal |
| 35 | `enableGamutMapper` | ❌ | ❌ | Not found on either |
| 36 | `enableStats` | ❌ | ❌ | Not found on either |
| 37 | *(unknown)* | ✅ | ✅ | Universal |
| 38 | *(unknown)* | ✅ | ✅ | Universal |
| 39 | *(unknown)* | ✅ | ✅ | Universal |
| 40 | *(unknown)* | ✅ | ✅ | Universal |
| 41 | `VRRDivisor` | ❌ | ❌ | Not found on either |
| 42 | `VRRVersion` | ❌ | ❌ | Not found on either |
| 43 | *(unknown)* | ✅ | ✅ | Universal |
| 44 | `IOMFBWideGamutPassthrough` | ❌ | ❌ | Not found on either |
| 45 | `enableFiltersNoRewriteMode` | ❌ | ❌ | Not found on either |
| 46 | `enablePLCMode` | ❌ | ❌ | Not found on either |
| 47 | `enableABGMode` | ❌ | ❌ | Not found on either |
| 48 | `enableABGDynamicMap` | ❌ | ❌ | Not found on either |
| 49 | `enableDBMMode` | ❌ | ❌ | Not found on either |
| 50 | `enableBICMode` | ❌ | ❌ | Not found on either |
| 51 | `enableBICUpdates` | ❌ | ❌ | Not found on either |
| 52 | `enableSBIM` | ❌ | ❌ | Not found on either |
| 53 | `enableGPDeringing` | ❌ | ❌ | Not found on either |
| 54 | `enableGPAlphaDiv` | ❌ | ❌ | Not found on either |
| 55 | `twilightStrength` | ❌ | ❌ | Not found on either |
| 56 | `TLBrightOverride` | ❌ | ❌ | Not found on either |
| 57 | `allocateDefaultFramebuffer` | ❌ | ❌ | Not found on either |
| 58 | `debugHardPowerEvent` | ❌ | ❌ | Not found on either |
| 59 | `ESDThresholdMS` | ❌ | ❌ | Not found on either |
| 60 | `EnableKernelTests` | ❌ | ❌ | Not found on either |
| 61 | *(unknown)* | ✅ | ✅ | Universal |
| 62 | *(unknown)* | ✅ | ✅ | Universal |
| 63 | `EnableEven60FPSFrames` | ❌ | ❌ | Not found on either |
| 64 | `PanicOnHungSwap` | ❌ | ❌ | Not found on either |
| 65 | `FakeTconESDEvent` | ❌ | ❌ | Not found on either |
| 66 | *(unknown)* | ✅ | ✅ | Universal |
| 67 | *(unknown)* | ✅ | ✅ | Universal |
| 68 | *(unknown)* | ✅ | ✅ | Universal |
| 69 | `enablePowerGateDCS` | ❌ | ❌ | Not found on either |
| 70 | `enableVideoCaching` | ❌ | ❌ | Not found on either |
| 71 | `dummySystemWantsCaching` | ❌ | ❌ | Not found on either |
| 72 | `disableSystemCachingInput` | ❌ | ❌ | Not found on either |
| 73 | `enableMockALSSCapture` | ❌ | ❌ | Not found on either |
| 74 | *(unknown)* | ✅ | ✅ | Universal |
| 75 | *(unknown)* | ✅ | ✅ | Universal |
| 76 | *(unknown)* | ✅ | ✅ | Universal |
| 77 | *(unknown)* | ✅ | ✅ | Universal |
| 78 | *(unknown)* | ✅ | ✅ | Universal |
| 79 | *(unknown)* | ✅ | ✅ | Universal |
| 80 | *(unknown)* | ✅ | ✅ | Universal |
| 81 | *(unknown)* | ✅ | ✅ | Universal |
| 82 | *(unknown)* | ✅ | ✅ | Universal |
| 83 | `BLNitsCap` | ❌ | ✅ | Internal only |
| 84 | `RTPLCBLNitsCap` | ❌ | ❌ | Not found on either |
| 85 | `RTPLCBLNitsScaler` | ❌ | ❌ | Not found on either |
| 86 | `RTPLCNitsThresh` | ❌ | ❌ | Not found on either |
| 87 | *(unknown)* | ✅ | ✅ | Universal |
| 88 | *(unknown)* | ✅ | ✅ | Universal |
| 89 | *(unknown)* | ✅ | ✅ | Universal |
| 90 | *(unknown)* | ✅ | ✅ | Universal |
| 91 | *(unknown)* | ✅ | ✅ | Universal |
| 92 | *(unknown)* | ✅ | ✅ | Universal |
| 93 | *(unknown)* | ✅ | ✅ | Universal |
| 94 | *(unknown)* | ✅ | ✅ | Universal |
| 95 | *(unknown)* | ✅ | ✅ | Universal |
| 96 | *(unknown)* | ✅ | ✅ | Universal |
| 97 | *(unknown)* | ✅ | ✅ | Universal |
| 98 | *(unknown)* | ✅ | ✅ | Universal |
| 99 | *(unknown)* | ✅ | ✅ | Universal |
| 100 | *(unknown)* | ✅ | ✅ | Universal |
| 101 | `SkipRegion` | ❌ | ❌ | Not found on either |
| 102 | `ExportCRCAtVBI` | ❌ | ❌ | Not found on either |
| 103 | *(unknown)* | ✅ | ✅ | Universal |
| 104 | `PCCCabalEnable` | ❌ | ✅ | Internal only |
| 105 | *(unknown)* | ✅ | ✅ | Universal |
| 106 | `IOMFBSupportsHDR10Plus` | ❌ | ❌ | Not found on either |
| 107 | `PCCTrinityEnable` | ❌ | ✅ | Internal only |
| 108 | `PCCEnable` | ❌ | ✅ | Internal only |
| 109 | `PCC2DEnable` | ❌ | ✅ | Internal only |
| 110 | `BypassPCC2DLed` | ❌ | ❌ | Not found on either |
| 111 | `PCC2DLedAccelOut` | ❌ | ❌ | Not found on either |
| 112 | `PCC2DLedAccelLog` | ❌ | ❌ | Not found on either |
| 113 | `DisablePCC2DBrc` | ❌ | ❌ | Not found on either |
| 114 | `DisableTempComp` | ❌ | ❌ | Not found on either |
| 115 | `ModeBlm` | ❌ | ❌ | Not found on either |
| 116 | `IOMFBTestBacklightDimValue` | ❌ | ✅ | Internal only |
| 117 | `BLMVLEDManual` | ❌ | ✅ | Internal only |
| 118 | `BLMAHOutputFreq` | ❌ | ✅ | Internal only |
| 119 | `BLMAHMode` | ❌ | ✅ | Internal only |
| 120 | `BLMPLimitCfg` | ❌ | ✅ | Internal only |
| 121 | `enableBLMSloper` | ❌ | ✅ | Internal only |
| 122 | `enableLAC` | ❌ | ✅ | Internal only |
| 123 | `BLMAHUPCount` | ❌ | ✅ | Internal only |
| 124 | `M3DiagsTimeout` | ❌ | ❌ | Not found on either |
| 125 | `DisableBConBoot` | ❌ | ✅ | Internal only |
| 126 | *(unknown)* | ✅ | ✅ | Universal |
| 127 | *(unknown)* | ✅ | ✅ | Universal |
| 128 | `APTPDCEnableRepeat` | ❌ | ❌ | Not found on either |
| 129 | `PDCGlobalTemp` | ❌ | ✅ | Internal only |
| 130 | *(unknown)* | ✅ | ✅ | Universal |
| 131 | *(unknown)* | ✅ | ✅ | Universal |
| 132 | *(unknown)* | ✅ | ✅ | Universal |
| 133 | `PDCEntryTime` | ❌ | ❌ | Not found on either |
| 134 | `PDCExitTime` | ❌ | ❌ | Not found on either |
| 135 | `PDCAlwaysOnNits` | ❌ | ❌ | Not found on either |
| 136 | `PDCContentSwitchCount` | ❌ | ❌ | Not found on either |
| 137 | `pccLumaGammaFactor` | ❌ | ❌ | Not found on either |
| 138 | `PDCCutoffLux` | ❌ | ❌ | Not found on either |
| 139 | `PDCExitCount` | ❌ | ❌ | Not found on either |
| 140 | `overdriveCompCutoff` | ❌ | ✅ | Internal only |
| 141 | *(unknown)* | ✅ | ✅ | Universal |
| 142 | `VSHHistVal` | ❌ | ❌ | Not found on either |
| 143 | `CECorrectionFactor` | ❌ | ✅ | Internal only |
| 144 | `ProxScanPlan` | ⚠️ | ⚠️ | Status 2 on both |
| 145 | *(unknown)* | ✅ | ✅ | Universal |
| 146 | `SWSTemp` | ❌ | ❌ | Not found on either |
| 147 | `ForceAOTARMode` | ❌ | ❌ | Not found on either |
| 148 | `SPUCEnable` | ❌ | ❌ | Not found on either |
| 149 | `BLMAHOutputLogEnable` | ❌ | ✅ | Internal only |
| 150 | `BLMAHStatsLogEnable` | ❌ | ✅ | Internal only |
| 151 | `BLMStandbyEnable` | ❌ | ✅ | Internal only |
| 152 | `VUCEnable` | ❌ | ❌ | Not found on either |
| 153 | `limit_max_physical_brightness` | ❌ | ❌ | Not found on either |
| 154 | `RTPLCEnable` | ❌ | ❌ | Not found on either |
| 155 | `RTPLCEnableRT` | ❌ | ❌ | Not found on either |
| 156 | `RTPLCEnableFD` | ❌ | ❌ | Not found on either |
| 157 | `RTPLCEnableNitsCap` | ❌ | ❌ | Not found on either |
| 158 | `RTPLCEnablePredThreshCross` | ❌ | ❌ | Not found on either |
| 159 | `enableSWS` | ❌ | ❌ | Not found on either |
| 160 | *(unknown)* | ✅ | ✅ | Universal |
| 161 | *(unknown)* | ✅ | ✅ | Universal |
| 162 | *(unknown)* | ✅ | ✅ | Universal |
| 163 | `forceEnableACSS` | ❌ | ❌ | Not found on either |
| 164 | `gamutConversionPostBlend` | ❌ | ❌ | Not found on either |
| 165 | `gamutConversionPipe0` | ❌ | ❌ | Not found on either |
| 166 | `gamutConversionPipe1` | ❌ | ❌ | Not found on either |
| 167 | `SystemIdlenessEnabled` | ❌ | ❌ | Not found on either |
| 168 | `SystemIdlenessThreshold` | ❌ | ❌ | Not found on either |
| 169 | `VRRIdleEnabled` | ❌ | ❌ | Not found on either |
| 170 | `VRRIdleThreshold` | ❌ | ❌ | Not found on either |
| 171 | `VRRBurnInEnabled` | ✅ | ❌ | External only |
| 172 | `VRRBurnInThreshold` | ❌ | ❌ | Not found on either |
| 173 | `VRRBurnInCooldownEnabled` | ❌ | ❌ | Not found on either |
| 174 | `VRRBurnInCooldownThreshold` | ❌ | ❌ | Not found on either |
| 175 | `PowerGateADPIdleEnabled` | ❌ | ❌ | Not found on either |
| 176 | `PowerGateADPIdleThreshold` | ❌ | ❌ | Not found on either |
| 177 | `RuntimeProperty::COUNT` | ❌ | ❌ | Sentinel |

## Summary

### Universal properties (work on both displays): 65 properties
Selectors: 0, 1, 13-17, 21, 34, 37-40, 43, 61-62, 66-68, 74-82, 87-100, 103, 105, 126-127, 130-132, 141, 145, 160-162, 171*

### Internal-only properties: 32 properties
Selectors: 2, 3, 18, 22, 25-29, 83, 104, 107-109, 116-123, 125, 129, 140, 143, 149-151

### External-only properties: 1 property
Selector: 171

### Not found on either display: 67 properties
All others

### Properties with status 2 (exists but failed): 5 properties
Selectors: 19, 20, 25-28, 144
