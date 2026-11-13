# 用 Quest 3 玩《Beat Saber》，在三星 Tizen 电视上同步观看

[العربية](README.ar.md) · [中文](README.zh.md) · [English](README.md) · [Français](README.fr.md) · [Русский](README.ru.md) · [Español](README.es.md)

**一人游玩，两个画面。** Windows 游戏电脑运行《Beat Saber》，Virtual Desktop 将 VR 画面传到玩家的 Quest 3。同时，Sunshine 捕获电脑桌面，通过家庭局域网传给三星 BU8000 上的 Moonlight。观众在电视上看到的是电脑显示器上的内容。

**所需设备。** 一台装有 PC 版《Beat Saber》的 Windows 游戏电脑、一台已配置好 Virtual Desktop 并能运行 PCVR 游戏的 Quest 3，以及同一家庭局域网内的三星 BU8000。实测电视运行 Tizen 6.5，游戏电脑通过网线连接路由器。安装电视应用时用到了另一台 Windows 电脑。

## 首次设置

1. **在游戏电脑上**安装 [Windows 版 Sunshine](https://github.com/SunshineStream/Sunshine/releases/latest)。用这台电脑打开 [Sunshine 本地管理页面](https://localhost:47990)，设置用户名和密码。在应用列表中保留 **Desktop**。
2. **在电视上**打开 **Apps**，输入 **12345** 进入开发者菜单。开启 **Developer Mode**，在 **Host PC IP** 中填入用于安装 Moonlight 的电脑的局域网 IP 地址。如果更改了设置，请重启电视。实测时，这里填写的是那台负责安装的电脑的地址。[Moonlight Tizen 安装指南](https://github.com/brightcraft/moonlight-tizen/wiki/Installation-Guide)
3. **在用于安装的电脑上**，从 [Moonlight Tizen 发布页](https://github.com/brightcraft/moonlight-tizen/releases) 下载标准版 **Moonlight.wgt**，使用 **Apps2Samsung** 将其安装到电视上。实测时，安装工具复用了已有的、对这台电视有效的 Samsung Partner 证书。首次申请证书时，请按安装工具的提示操作。[Apps2Samsung](https://github.com/Apps2Samsung/Apps2Samsung)
4. **在电视上**打开 Moonlight，选择游戏电脑。如果列表里没有它，手动添加游戏电脑有线网卡的局域网 IP 地址。电视会显示一个 PIN 码。在游戏电脑上进入 Sunshine 管理页面的 **PIN** 页，选择来自电视的配对请求，输入该 PIN 码。

如果使用 Windows 版 Apps2Samsung CLI，请在存放工具和安装包的文件夹中运行以下命令。将 `TV_IP` 和 `INSTALL_PC_IP` 分别替换为电视和安装电脑的局域网 IP 地址。

```powershell
.\apps2samsung-cli.exe install .\Moonlight.wgt --tv TV_IP --local-ip INSTALL_PC_IP
```

## 每次游玩时

在 Quest 3 中通过 Virtual Desktop 启动 PC 版《Beat Saber》。先看一下电脑显示器，确认上面是希望观众看到的游戏画面。然后在电视上依次选择 **Moonlight → 游戏电脑 → Desktop**。如果电视上只看到 Windows 桌面，请先检查 Sunshine 正在捕获的显示器上显示了什么。

**实测情况。** 玩家确认已运行《Beat Saber》。Sunshine 日志确认 BU8000 配对成功并开始串流，RTX 3070 使用 H.264 硬件编码，客户端请求的帧率为 60 fps，音频以立体声采集。测试未记录具体使用了哪个游戏画面窗口，也未测量端到端延迟。
