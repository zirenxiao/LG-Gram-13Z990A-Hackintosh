# LG Gram 13Z990A OpenCore

## Latest Update

由于机器已出手，故不再更新。现有EFI可以正常运行。

This repository will be no longer updated, existing EFI files work up to macOS 12.2.1.

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

## macOS 支持情况

- 已测试
  - macOS 11.2
  - macOS 11.2.3
  - macOS 11.6.3
  - macOS 11.6.4
  - macOS 12.2.1

## 工作情况
- [x] 声卡（扬声器，3.5mm耳机）
- [x] 显卡（HEVC+H.264 4K双硬解；HDMI输出最高2K@60）
- [x] Wi-Fi/蓝牙（Airdrop；Handoff）
- [x] 电源（电量显示；原生电源管理；CPU变频；）
- [ ] 睡眠（睡死，暂时不能开启睡眠）
- [ ] 键盘（仅F4 F8 F10 F11 F12可正常使用）
- [x] 触控板
- [x] USB定制
- [x] iServices
- [ ] 雷电 3
- [x] 读卡器，有小概率导致无法启动系统，原因未知


## 使用

- 修改 BIOS 设定 (开机时按下F2进入 BIOS 后，Ctrl + Alt + F7 开启 BIOS 隐藏选项）
  1. BIOS-Main-Boot Features: **CMS Support [No]**, **Fast Boot [Disabled]** 
  2. BIOS-Advanced-Intel Advanced Menu-Power&Performance-CPU Power Management Control: **CFG Lock [Disabled]** 

- 使用OpenCore Configurator打开（对应0.7.4版本）
  1. 选择机型MacBookPro15,2，生成合适的三码
  2. EFI文件夹复制到macOS安装器，即可开始安装

- 安装完后必须的设置
  1. 电源选项： **Put hard disk to sleep when possible [Disabled]**，否则睡死
  2. 触控板设置：Force Click关闭
  3. 执行以下命令彻底关闭睡眠
  ```
  # 复制粘贴以下运行结果，备份
  pmset -g
  # 完全禁用sleep
  sudo pmset -a sleep 0
  sudo pmset -a hibernatemode 0
  sudo pmset -a disablesleep 1
  # 如睡眠问题已修复，可以执行如下命令解除禁用
  sudo pmset -a sleep 1
  sudo pmset -a hibernatemode [之前备份的值]
  sudo pmset -a disablesleep 0
  ```


## 更新记录

### 2022.03.12 v1.6

* 更新驱动版本至最新
* 自动切换Intel Wi-Fi驱动，同时兼容11.x和12.x

### 2022.02.14 v1.5

* 升级驱动到最新版本
* 支持macOS 12.x （需自行替换Wi-Fi驱动为12.x专用）

### 2021.10.20 v1.4

* 关闭开机声音，会导致无法进入系统
* 修复触控板失效的问题
* USB定制

### 2021.10.17 v1.3

* 更新OpenCore到最新版本0.7.4
* 修复主题bug（via Theme Validator)

### 2021.10.16 v1.2

* 更新大部分kext到最新

### 2021.10.16 v1.0

* 更新itlwm到2.0.0，老版本Wi-Fi容易掉且不稳定
* 更新IntelBluetoothFirmware到2.0.1
* AppleALC更新会导致声音丢失

## 未来更新

* 睡眠
* 雷电3驱动

## Reference

本OpenCore EFI修改自[myd986](https://github.com/myd986/LG-gram-14z990-Hackintosh)
