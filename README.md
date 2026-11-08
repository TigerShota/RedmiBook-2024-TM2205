# RedmiBook 2024 焕新版 (TM2205) — OpenCore EFI

小米 RedmiBook 2024 焕新版（TM2205）黑苹果 OpenCore 引导配置备份。

## 硬件配置

| 项目 | 规格 |
| --- | --- |
| 机型 | RedmiBook 2024 焕新版（TM2205），14 英寸 |
| CPU | 12th Gen Intel Core i5-12450H，Alder Lake-H，Intel 7 工艺 |
| CPU 核心 | 8 核 12 线程（4 × P-core Golden Cove + 4 × E-core Gracemont），L3 12MB |
| 核显 | Intel UHD Graphics（Alder Lake，device ID `0x46A3`），Xe-LP 架构，48 EU，最高 1.2GHz |
| 内存 | 16GB LPDDR5-5200（SK Hynix 板载，不可升级） |
| 硬盘 | FORESEE XP2000F512G 512GB NVMe SSD（PCIe 4.0 ×4，固件 V1223G0T） |
| 屏幕 | TL140ADXP20-0，14 英寸 2880×1800（2.8K）120Hz 内屏 |
| 无线 | Intel Wi-Fi 6 AX201（CNVi）+ 蓝牙 5.1 |
| 声卡 | Realtek HD Audio（AppleALC 驱动） |
| 有线网卡 | Realtek RTL8111 |

## 引导配置

| 项目 | 内容 |
| --- | --- |
| 机型标识 | MacBookPro16,2 |
| 引导 | OpenCore + OpenCanopy 图形选择界面 |
| 驱动 | HfsPlus.efi、OpenRuntime.efi、OpenCanopy.efi、ResetNvramEntry.efi |
| ACPI | AWAC、EC-USBX-LAPTOP、GPI0、HPET、PLUG-ALT、PMC、PNLF、RHUB、RMNE、SBUS-MCHC、XOSI、ALS0、DMAR |

主要 kext：Lilu、VirtualSMC（SMCProcessor / SMCSuperIO / SMCBatteryManager / SMCLightSensor）、WhateverXe（WhateverGreen 分支）、AppleIntelTGLCompat、AppleALC、AirportItlwm、IntelBluetoothFirmware（含 BlueToolFixup、IntelBTPatcher）、USBToolBox / UTBDefault、VoodooI2CHID、VoodooPS2Controller、ECEnabler、NVMeFix、RealtekRTL8111、CpuTopologyRebuild、RestrictEvents、AMFIPass、XHCI-unsupported、BrightnessKeys。

## 已知问题

- 触控板：完全不可用（VoodooI2CHID 虽已加载，但触控板无任何响应）
- 睡眠：休眠/唤醒异常，暂不建议依赖睡眠
- HDMI：外接 HDMI 无输出

## 使用注意

- 本仓库仅含 OpenCore 相关文件，不含 Windows 的 `EFI/Microsoft` 引导。
- `config.plist` 中的 `SystemSerialNumber` / `MLB` / `SystemUUID` 为本机生成值，直接复用前请自行重新生成，避免与他人共用同一套 SMBIOS 标识。
- 使用前请确认 OpenCore 与 kext 版本匹配；替换 EFI 前务必备份原分区内容。
