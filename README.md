# SM-F926N Kernel Builder

> **警告**：本项目编译产物未经过实机测试，可能无法正常开机或导致设备异常。请谨慎使用，刷机前务必备份重要数据，自行承担风险。

三星 Galaxy Z Fold 3 (SM-F926N) 韩国版内核自动编译项目，基于 [KernelSU_Action](https://github.com/lanlinga/KernelSU_Action) 框架，使用 GitHub Actions 云端编译。

## 快速开始

1. Fork 本仓库
2. 编辑 `config.env`（关键配置见下方）
3. 进入 Actions 页面 → Build Kernel → Run workflow

## config.env 关键配置

| 变量 | 说明 | 默认值 |
|---|---|---|
| `ENABLE_KERNELSU` | 是否编译 KernelSU 内核（`true`/`false`） | `false` |
| `KSU_VARIANT` | KernelSU 变体：`ksu`（标准版）或 `resukisu`（ReSukiSU 非 GKI 手动 hook） | `resukisu` |
| `KERNEL_CONFIG` | defconfig 路径 | `vendor/q2q_kor_singlex_defconfig` |
| `ENABLE_CCACHE` | 是否启用 ccache 加速编译 | `true` |
| `DISABLE-LTO` | 禁用 LTO（减少编译错误） | `true` |

- `ENABLE_KERNELSU=false` 时编译**纯净内核**，不含任何 KernelSU 代码
- `ENABLE_KERNELSU=true` + `KSU_VARIANT=resukisu` 时编译 **ReSukiSU 内核**（适配 SM-F926N 5.4 内核的手动 hook 模式）
- `ENABLE_KERNELSU=true` + `KSU_VARIANT=ksu` 时编译标准 KSU 内核（v0.9.5 非 GKI 版）

全部配置项及默认值见 `config.env` 注释。

## 编译产物

每次成功编译产出两个 artifact：

- `Image.gz-*` — 压缩内核镜像
- `AnyKernel3-*` — 可直接刷入的刷机包（zip）

## 刷入

AnyKernel3 zip 通过 TWRP / OrangeFox 或 Kernel Flasher App 刷入。

## 技术栈

- Clang 14 (r450784e, AOSP master-kernel-build-2022)
- GCC 4.9 (ARM64 + ARM32)
- DTC 1.4.4 (AOSP) + Samsung DT overlay
- ccache 2GB 缓存
- AnyKernel3 自动打包

## 已知问题

1. 编译通过但未实测，刷入后可能无法开机（kernel panic）
2. defconfig 为韩国版（`kor_singlex`），刷入其他区域设备可能部分硬件不工作
3. dtb 拼接使用通配符合并所有 lahaina dtb，可能引入不匹配的面板配置

## 参考

- [KernelSU](https://github.com/tiann/KernelSU)
- [ReSukiSU](https://github.com/ReSukiSU/ReSukiSU)
- [KernelSU_Action](https://github.com/lanlinga/KernelSU_Action)
- [三星开源发布中心](https://opensource.samsung.com)
