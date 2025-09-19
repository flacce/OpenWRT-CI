# 🚀 OpenWRT-CI 自动化编译系统

[![GitHub Stars](https://img.shields.io/github/stars/flacce/OpenWRT-CI?style=flat-square&logo=github)](https://github.com/flacce/OpenWRT-CI/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/flacce/OpenWRT-CI?style=flat-square&logo=github)](https://github.com/flacce/OpenWRT-CI/network)
[![GitHub Issues](https://img.shields.io/github/issues/flacce/OpenWRT-CI?style=flat-square&logo=github)](https://github.com/flacce/OpenWRT-CI/issues)
[![GitHub License](https://img.shields.io/github/license/flacce/OpenWRT-CI?style=flat-square)](https://github.com/flacce/OpenWRT-CI/blob/main/LICENSE)

> 🎯 基于 GitHub Actions 的 OpenWRT 固件自动化编译系统，支持多平台设备，集成精选插件，一键编译发布。

## 📋 目录

- [✨ 特性](#-特性)
- [🏗️ 支持平台](#️-支持平台)
- [📦 内置插件](#-内置插件)
- [🚀 快速开始](#-快速开始)
- [⚙️ 配置说明](#️-配置说明)
- [📁 项目结构](#-项目结构)
- [🔧 自定义编译](#-自定义编译)
- [📖 使用说明](#-使用说明)
- [🤝 贡献指南](#-贡献指南)
- [📄 许可证](#-许可证)

## ✨ 特性

### 🎯 核心优势
- **🤖 全自动化** - 基于 GitHub Actions，无需本地环境
- **🔄 智能缓存** - 优化编译缓存策略，大幅缩短编译时间
- **📱 多平台支持** - 支持 ROCKCHIP、MEDIATEK 等主流平台
- **🎨 精美界面** - 优化的 Web 管理界面和发布页面
- **⚡ 性能优化** - 硬件加速支持，网络性能调优

### 🛠️ 技术特性
- **📦 精选插件** - 仅保留核心实用插件，避免冗余
- **🔧 模块化设计** - 可重用的工作流核心，易于维护
- **🎛️ 灵活配置** - 支持多种编译参数和设备配置
- **📊 详细日志** - 完整的编译过程记录和错误诊断
- **🔒 安全可靠** - 移除调试组件，生产环境优化

## 🏗️ 支持平台

### 📱 ROCKCHIP 平台
支持基于 ROCKCHIP 芯片的设备，包括：

| 品牌 | 设备型号 | 芯片 | 特性 |
|------|----------|------|------|
| **FriendlyARM** | NanoPC-T4/T6 | RK3399/RK3588 | 高性能开发板 |
| **FriendlyARM** | NanoPi-R2C/R2S | RK3328 | 入门级路由器 |
| **FriendlyARM** | NanoPi-R4S/R4SE | RK3399 | 企业级路由器 |
| **FriendlyARM** | NanoPi-R5C/R5S | RK3568 | 新一代路由器 |
| **FriendlyARM** | NanoPi-R6C/R6S | RK3588S | 旗舰级路由器 |
| **快犀牛** | FastRhino-R66S/R68S | RK3568 | 商用路由器 |
| **香橙派** | Orange Pi 5/5 Plus | RK3588S | 高性能单板机 |
| **香橙派** | Orange Pi R1 Plus | RK3328 | 迷你路由器 |

### 🔧 MEDIATEK 平台
支持联发科芯片设备（配置文件已准备）

### 🎯 其他平台
- **360-T7** - 360 路由器专用配置
- **JDC-IPQ60XX** - 高通 IPQ60XX 系列

## 📦 内置插件

### 🌐 网络工具
| 插件名称 | 功能描述 | 推荐指数 |
|----------|----------|----------|
| **🔒 PassWall** | 科学上网代理工具 | ⭐⭐⭐⭐⭐ |
| **🌍 MosDNS** | 智能 DNS 分流解析 | ⭐⭐⭐⭐⭐ |
| **🔗 EasyTier** | P2P 组网工具 | ⭐⭐⭐⭐ |
| **📊 NetSpeedTest** | 网速测试工具 | ⭐⭐⭐ |

### 🎨 系统特性
- **🎯 精简配置** - 移除冗余组件，专注核心功能
- **⚡ 硬件加速** - 全系支持硬件 NAT 加速
- **🔧 系统优化** - CPU 频率调节、内存优化
- **📱 现代界面** - 响应式 Web 管理界面

## 🚀 快速开始

### 1️⃣ Fork 项目
点击右上角 **Fork** 按钮，将项目复制到你的 GitHub 账户

### 2️⃣ 启用 Actions
1. 进入你的 Fork 项目
2. 点击 **Actions** 标签页
3. 点击 **I understand my workflows, enable them**

### 3️⃣ 开始编译
1. 进入 **Actions** 页面
2. 选择对应的工作流（如 `ROCKCHIP 平台编译`）
3. 点击 **Run workflow** 开始编译

### 4️⃣ 下载固件
编译完成后，在 **Releases** 页面下载对应设备的固件

## ⚙️ 配置说明

### 📁 配置文件结构
```
Config/
├── GENERAL.txt      # 通用配置（所有平台共用）
├── ROCKCHIP.txt     # ROCKCHIP 平台专用配置
├── MEDIATEK.txt     # MEDIATEK 平台专用配置
├── 360-T7.txt       # 360-T7 设备专用配置
└── JDC-IPQ60XX.txt  # IPQ60XX 平台专用配置
```

### 🔧 核心配置项

#### 编译优化
```bash
CONFIG_CCACHE=y                    # 启用编译缓存
CONFIG_DEVEL=y                     # 开发者模式
CONFIG_TARGET_MULTI_PROFILE=y      # 多设备支持
```

#### 网络功能
```bash
CONFIG_PACKAGE_kmod-nft-fullcone=y # 全锥NAT
CONFIG_PACKAGE_kmod-nft-offload=y  # 硬件加速
CONFIG_PACKAGE_kmod-wireguard=y    # WireGuard VPN
```

#### USB 支持
```bash
CONFIG_PACKAGE_kmod-usb3=y         # USB 3.0 支持
CONFIG_PACKAGE_kmod-usb-storage=y  # USB 存储
CONFIG_PACKAGE_kmod-usb-net=y      # USB 网卡
```

## 📁 项目结构

```
OpenWRT-CI/
├── .github/workflows/          # GitHub Actions 工作流
│   ├── WRT-CORE.yml           # 核心编译工作流
│   ├── 360-T7.yml             # 360-T7 设备编译
│   ├── JDC-IPQ60XX.yml        # IPQ60XX 平台编译
│   └── WRT-TEST.yml           # 测试工作流
├── Config/                     # 配置文件目录
│   ├── GENERAL.txt            # 通用配置
│   ├── ROCKCHIP.txt           # ROCKCHIP 配置
│   └── ...                    # 其他平台配置
├── Scripts/                    # 编译脚本
│   ├── Packages.sh            # 软件包管理脚本
│   ├── Handles.sh             # 特殊处理脚本
│   └── Settings.sh            # 系统设置脚本
└── README.md                   # 项目说明文档
```

## 🔧 自定义编译

### 添加新设备支持
1. 在 `Config/` 目录创建设备配置文件
2. 在 `.github/workflows/` 创建对应工作流
3. 参考现有配置进行适配

### 修改插件配置
1. 编辑 `Scripts/Packages.sh` 添加/删除插件
2. 修改 `Config/GENERAL.txt` 调整系统配置
3. 提交更改触发重新编译

### 自定义网络配置
编辑工作流文件中的网络参数：
```yaml
WRT_IP: 192.168.1.1      # 管理地址
WRT_PW: password         # 登录密码
WRT_SSID: OpenWrt        # WiFi 名称
WRT_WORD: 12345678       # WiFi 密码
```

## 📖 使用说明

### 🔥 刷机步骤
1. **备份原厂固件** - 刷机前务必备份
2. **选择正确固件** - 根据设备型号选择对应文件
3. **进入刷机模式** - 按设备说明进入刷机模式
4. **刷入固件** - 使用官方刷机工具或 Web 界面
5. **等待启动** - 首次启动需要较长时间
6. **恢复出厂** - 建议刷机后恢复一次出厂设置

### 🌐 首次配置
1. 浏览器访问 `http://192.168.1.1`
2. 使用默认密码登录（见 Release 说明）
3. 进入 **系统 → 管理权** 修改密码
4. 配置网络连接和 WiFi 设置
5. 根据需要启用相关插件

### 🔧 常见问题
- **无法访问管理界面** - 检查网络连接和 IP 地址
- **WiFi 无法连接** - 确认 WiFi 密码和加密方式
- **网络不通** - 检查 WAN 口连接和网络配置
- **插件无法使用** - 查看系统日志排查问题

## 🤝 贡献指南

### 🎯 贡献方式
- **🐛 报告问题** - 提交 Issue 描述遇到的问题
- **💡 功能建议** - 提出新功能或改进建议
- **🔧 代码贡献** - 提交 Pull Request 改进项目
- **📖 文档完善** - 改进文档和使用说明

### 📝 提交规范
- 使用中文提交信息
- 添加 emoji 前缀标识类型
- 清晰描述更改内容

示例：
```
🐛 修复编译错误：解决依赖包冲突问题
✨ 新增功能：添加新设备支持
📝 更新文档：完善使用说明
⚡ 性能优化：改进编译缓存策略
```

### 🔄 开发流程
1. Fork 项目到个人账户
2. 创建功能分支进行开发
3. 提交 Pull Request
4. 等待代码审查和合并

## 📊 项目统计

- **🎯 支持设备** 20+ 款主流路由器设备
- **⚡ 编译时间** 平均 45-60 分钟（含缓存优化）
- **📦 固件大小** 约 15-25MB（根据平台不同）
- **🔄 更新频率** 跟随上游源码更新

## 🙏 致谢

感谢以下项目和开发者的贡献：
- [OpenWrt](https://openwrt.org/) - 开源路由器固件项目
- [ImmortalWrt](https://github.com/immortalwrt/immortalwrt) - OpenWrt 分支项目
- [P3TERX](https://github.com/P3TERX/Actions-OpenWrt) - GitHub Actions 编译方案
- 各插件开发者和维护者

## 📄 许可证

本项目采用 [MIT License](LICENSE) 开源协议。

---

<div align="center">

**🌟 如果这个项目对你有帮助，请给个 Star 支持一下！**

[![Star History Chart](https://api.star-history.com/svg?repos=flacce/OpenWRT-CI&type=Date)](https://star-history.com/#flacce/OpenWRT-CI&Date)

</div>