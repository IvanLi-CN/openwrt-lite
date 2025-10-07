# OpenWrt Lite 23.05

Fork from [pmkol/openwrt-lite](https://github.com/pmkol/openwrt-lite)

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
