# Sunshine Open VHF

[English](README.md) · 简体中文

> [!IMPORTANT]
> **[`open-vhf`](https://github.com/kirito12136/Sunshine/tree/open-vhf) 是这个 fork 中独立维护的 Windows 手柄功能分支。**
> 这个仓库的默认分支是 [`master`](https://github.com/kirito12136/Sunshine/tree/master)，Sunshine 官方主分支是
> [`SunshineStream/Sunshine:master`](https://github.com/SunshineStream/Sunshine/tree/master)。

Sunshine 是可以自行部署、供 Moonlight 连接的游戏串流主机。本分支加入
[libvirtualgamepad](https://github.com/Nonary/libvirtualgamepad) 后端。安装兼容的 Windows Open VHF 驱动后，
使用该后端无需购买 Virtual HID Broker 许可证。

[下载本分支的 Windows x64 版本](https://github.com/kirito12136/Sunshine/releases/latest) ·
[查看与上游 `master` 的代码差异](https://github.com/SunshineStream/Sunshine/compare/master...kirito12136:open-vhf)

## 与上游主分支的区别

| 项目 | 上游 Sunshine（Windows） | `open-vhf`（Windows） |
| --- | --- | --- |
| 可选手柄后端 | 需许可证的 Virtual HID Broker，以及支持 Xbox 360 和 DualShock 4 的 ViGEmBus 回退。 | 保留原有选项，增加 **Open VHF (libvirtualgamepad)**。 |
| **All Available Drivers** | 优先使用已授权且可用的 Virtual HID Broker，符合条件时可回退到 ViGEmBus。 | 先尝试 Open VHF，失败后沿用原有的 Virtual HID Broker 和 ViGEmBus 选择逻辑。 |
| **Open VHF (libvirtualgamepad)** | — | 仅使用 Open VHF。驱动或所选型号不可用时，该手柄无法创建。 |

- 支持模拟 Xbox One、Xbox Series、DualShock 4、DualSense 和 Nintendo Switch Pro，具体型号以已安装驱动为准。体感、触摸板和震动等功能也取决于所选型号和 Moonlight 客户端。
- 网页配置增加 Open VHF 选项和故障排查提示。Windows 构建默认集成 [libvirtualgamepad 客户端 SDK](third-party/libvirtualgamepad/README.md)。
- fork 的 `master` 运行[上游同步工作流](https://github.com/kirito12136/Sunshine/actions/workflows/sync-open-vhf.yml)。Windows x64 构建和测试通过后，工作流才会把合并结果推送到 `open-vhf`。

## Windows 安装与设置

1. 在 [Releases](https://github.com/kirito12136/Sunshine/releases) 下载 MSI 安装包，或解压 ZIP 便携包。
2. 在 Windows 串流主机上单独安装兼容且已签名的 libvirtualgamepad 驱动。参见 [驱动打包与签名说明](https://github.com/Nonary/libvirtualgamepad#driver-package-and-signing)。
3. 在 Sunshine 网页中进入 **配置 → 输入**（**Configuration → Input**），将 **Gamepad Backend** 设为 **Open VHF (libvirtualgamepad)**。如果希望其他后端继续作为回退，选择 **All Available Drivers**。

本分支提供 Windows x64 安装包。Linux、macOS 等平台的安装包见 [Sunshine 上游 Releases](https://github.com/SunshineStream/Sunshine/releases/latest)。
从源码构建可参阅[本分支的构建说明](docs/building.md)，其他配置可参阅 [Sunshine 官方文档](https://docs.lizardbyte.dev/projects/sunshine/latest/)。
