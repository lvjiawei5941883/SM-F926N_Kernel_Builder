# SM-F926N Kernel Builder

> ⚠️ **警告**：本项目编译产物未经过实机测试，可能无法正常开机或导致设备异常。请谨慎使用，刷机前务必备份重要数据，自行承担风险。

三星 Galaxy Z Fold 3 (SM-F926N) 内核编译仓库，基于 [lanlinga/KernelSU_Action](https://github.com/lanlinga/KernelSU_Action) 框架。

## 特性

- 支持 **KSU v0.9.5** 与 **ReSukiSU** 双版本，`config.env` 中 `KSU_VARIANT` 一键切换
- ReSukiSU 非 GKI 手动 hook 模式，适配 SM-F926N 5.4 内核
- Clang 14 + GCC 编译，ccache 加速
- 自动生成 AnyKernel3 刷机包

## 使用

1. Fork 本仓库
2. 上传三星内核源码至 [SM-F926N_Kernel_Source](https://github.com/lvjiawei5941883/SM-F926N_Kernel_Source)（或使用自托管 Release ZIP）
3. 编辑 `config.env`：
   - `KSU_VARIANT=ksu` → 编译 KSU v0.9.5
   - `KSU_VARIANT=resukisu` → 编译 ReSukiSU
4. 在 Actions 页面手动触发 Build Kernel

## 刷入

AnyKernel3 zip 通过 TWRP / OrangeFox 或 Kernel Flasher App 刷入。

## 参考

- [KernelSU](https://github.com/tiann/KernelSU)
- [ReSukiSU](https://github.com/ReSukiSU/ReSukiSU)
- [lanlinga/KernelSU_Action](https://github.com/lanlinga/KernelSU_Action)

## ⚠️ 重要说明

**此仓库为实验性项目，尚未在真实设备上测试通过。**
- 内核编译成功，但刷入后可能无法开机（震动发热，kernel panic）
- 问题可能出在 dtb overlay 不完整、defconfig 不匹配或三星 RKP 保护
- 目前仍在调试中，请勿用于生产设备
- 如果你有 SM-F926N 设备并愿意测试，欢迎提供反馈

**已知问题**：
1. 编译成功但不开机（震动发热）
2. DTC_EXT 路径问题（三星定制 dtc 缺失）
3. defconfig 差异（kor_singlex vs eur_openx）

**后续计划**：
- 对比 Glide Kernel 的 defconfig
- 修复 dtb overlay
- 测试 APatch/FolkPatch 替代方案
