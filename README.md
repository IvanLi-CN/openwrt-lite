# OpenWrt Lite 23.05

Fork from [pmkol/openwrt-lite](https://github.com/pmkol/openwrt-lite)

## 功能总览

- 核心系统
  - 基于 OpenWrt 23.05 的轻量模板，支持云构建（GitHub Actions）与本地编译
  - 自定义配置集中于 `openwrt/23-config-common-custom`，方便按需开关插件

- 网络与加速（支持/可选）
  - Full Cone NAT、TCP BBRv3、Multipath TCP（MPTCP）、Shortcut-FE、LLVM-BPF 等网络优化能力

- 常用网络组件（预置为主，个别可按需开关）
  - 代理相关：Mihomo 面板（`luci-app-nikki`）、OpenClash（`luci-app-openclash`）
  - DNS 与分流：MosDNS（`luci-app-mosdns`）
  - 隧道与内网穿透：FRP 客户端（`luci-app-frpc`）
  - 远程与虚拟专网：Tailscale（`luci-app-tailscale`）、ZeroTier（`luci-app-zerotier`）、WireGuard（`luci-proto-wireguard`）
  - 家庭网络：UPnP（`luci-app-upnp`）

- 可观测与管理
  - Netdata（`luci-app-netdata`）
  - 流量统计 NLBWMon（`luci-app-nlbwmon`）
  - 网络测速（`luci-app-netspeedtest`）
  - 系统远程终端 TTYD（`luci-app-ttyd`）
  - 看门狗/自恢复 Watchcat（`luci-app-watchcat`）
  - 远程唤醒 WOL Plus（`luci-app-wolplus`）

- 系统与存储
  - CPU 频率管理（`luci-app-cpufreq`）、系统内存工具（`luci-app-ramfree`）
  - 磁盘与分区管理 DiskMan（`luci-app-diskman`）
  - QoS/限速 EQoS+（`luci-app-eqosplus`）、端口转发与网络工具 Socat（`luci-app-socat`）
  - 部分文件/共享相关插件（如 Samba/KSmbd）默认关闭，可在自定义配置中开启

> 说明：以上功能以当前 `openwrt/23-config-common-custom` 的默认项为准；你可以按需修改开启/关闭，工作流构建会自动应用该配置。

## 定制

- 修改 `openwrt/23-config-common-custom` 配置，注释或删除掉不需要的插件，该配置会自动覆盖lite与server配置中的luci插件

- 按照 .config 格式添加需要的插件，例如 `CONFIG_PACKAGE_luci-app-mihomo=y`

- 如果添加了 Feed 中不存在的插件，请在 `openwrt/scripts/06-custom.sh` 加入插件引用代码

## 构建

- 在左侧边栏中，单击要运行的工作流的名称“**Build OpenWrt 23.05 Custom**”

- 在工作流运行的列表右上方，单击“**Run workflow**”按钮，选择要构建的版本与设备固件并运行工作流

```
Select the build version: lite | server
Select device to build: x86_64 | nanopi-r4s | nanopi-r5s(r5c)
Build options: 默认无需填写，用于写入高级构建参数，参数之间用空格分开
例如 LAN=192.168.31.1 NO_DOCKER=y ENABLE_LOCAL_KMOD=y
```
