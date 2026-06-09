# SM-F926N Kernel Builder

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
