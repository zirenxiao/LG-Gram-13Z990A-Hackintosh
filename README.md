# LG Gram 13Z990A OpenCore

## 配置

|      | 详情   |
| ---- | -----------------------------------------|
| 型号 | LG Gram 13 Z990A|
| CPU  | Core i5-8265U|
| 显卡 | Intel UHD Graphics 620（Whiskey Lake）|
| 内存 | 8G板载|
| 硬盘 | Intel 1TB|
| 声卡 | Conexant CX8200|
| 网卡 | Intel AC-9560|
| 蓝牙 | Intel AC-9560|

## 工作情况
- [x] 声卡（扬声器，3.5mm耳机）
- [x] 显卡（HEVC+H.264 4K双硬解；HDMI输出最高2K@60）
- [x] Wi-Fi/蓝牙（Airdrop；Handoff）
- [x] 电源（电量显示；原生电源管理；CPU变频；睡眠一晚掉电4%）
- [ ] 键盘（仅F4 F8 F10 F11 F12可正常使用）
- [x] 触控板
- [x] USB定制
- [x] iServices
- [ ] 雷电 3
- [x] 读卡器，睡眠唤醒后可能丢失

## 使用

- 修改 BIOS 设定 (开机时按下F2进入 BIOS 后，Ctrl + Alt + F7 开启 BIOS 隐藏选项）
  1. BIOS-Main-Boot Features: **CMS Support [No]**, **Fast Boot [Disabled]** 
  2. BIOS-Advanced-Intel Advanced Menu-Power&Performance-CPU Power Management Control: **CFG Lock [Disabled]** 

- 使用附带的OpenCore Configurator打开（或者自行下载，对应0.6.6版本）
  1. 生成合适的三码
  2. Show Picker打开，或者开机按Alt键，否则开机选择界面不出现，自动跳转Windows
  3. EFI文件夹复制到macOS安装器，即可开始安装

- 安装完后必须的设置
  1. 电源选项： **Put hard disk to sleep when possible [Disabled]**，否则睡死

- 注意：Z980不兼容！


## 更新记录

### 2021.10.17 v2

* 更新大部分kext到最新

### 2021.10.16

* 更新itlwm到2.0.0，老版本Wi-Fi容易掉且不稳定
* 更新IntelBluetoothFirmware到2.0.1
* AppleALC更新会导致声音丢失

## Reference

本OpenCore EFI修改自[myd986](https://github.com/myd986/LG-gram-14z990-Hackintosh)
