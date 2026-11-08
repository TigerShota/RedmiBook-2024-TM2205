# RedmiBook 2024 (TM2205) — OpenCore EFI

小米 RedmiBook 2024（TM2205）黑苹果 OpenCore 引导配置备份。

## 配置概要

| 项目 | 内容 |
| --- | --- |
| 机型标识 | MacBookPro16,2 |
| 引导 | OpenCore + OpenCanopy 图形选择界面 |
| 驱动 | HfsPlus.efi、OpenRuntime.efi、OpenCanopy.efi、ResetNvramEntry.efi |
| ACPI | AWAC、EC-USBX-LAPTOP、GPI0、HPET、PLUG-ALT、PMC、PNLF、RHUB、RMNE、SBUS-MCHC、XOSI、ALS0、DMAR |
| 显卡 | WhateverXe.kext（WhateverGreen 分支）+ AppleIntelTGLCompat.kext |

主要 kext：Lilu、VirtualSMC（SMCProcessor / SMCSuperIO / SMCBatteryManager / SMCLightSensor）、WhateverXe、AppleALC、AirportItlwm、IntelBluetoothFirmware（含 BlueToolFixup、IntelBTPatcher）、USBToolBox / UTBDefault、VoodooI2CHID、VoodooPS2Controller、ECEnabler、NVMeFix、RealtekRTL8111、CpuTopologyRebuild、RestrictEvents、AMFIPass、XHCI-unsupported、BrightnessKeys。

## 已知问题

- 触控板：未完全可用（VoodooI2CHID 已加载，手势/多指支持不完整）
- 睡眠：休眠唤醒异常，暂不建议依赖睡眠
- HDMI：外接 HDMI 输出未正常工作

## 使用注意

- 本仓库仅含 OpenCore 相关文件，不含 Windows 的 `EFI/Microsoft` 引导。
- `config.plist` 中的 `SystemSerialNumber` / `MLB` / `SystemUUID` 为本机生成值，直接复用前请自行重新生成，避免与他人共用同一套 SMBIOS 标识。
- 使用前请确认 OpenCore 与 kext 版本匹配；替换 EFI 前务必备份原分区内容。
