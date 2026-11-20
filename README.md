# TextRelay — iOS 短信/通知转发器

越狱 iOS 上的短信与通知转发工具（Theos 插件，deb 分发）。它把 **[pppscn/SmsForwarder（短信转发器，安卓）](https://github.com/pppscn/SmsForwarder)** 的核心思路带到 iPhone 上：监控设备上的短信与 App 通知，按规则转发到你指定的推送服务。

代码基于 [NoahSaso/Pusher](https://github.com/NoahSaso/Pusher)（其 rootless 移植版为 [jzksnsjswkw/Pusher-rootless](https://github.com/jzksnsjswkw/Pusher-rootless)），在其基础上完成标识符重构、渠道保留与文档重写，详见 [NOTICE.md](NOTICE.md)。

## 功能

- **短信转发**：短信到达即推送（含验证码场景）；支持按收信 SIM 卡槽区分双卡
- **通知转发**：任意 App 的通知都可转发，等效安卓版「APP 通知转发」
- **通知拦截**：按规则让特定通知不在设备上显示（通知滤盒）
- **过滤规则**：关键词 / 正则匹配、按 App 黑白名单、循环推送防护
- **转发渠道**（内置 18 种）：Bark、钉钉、企业微信（应用消息 / 群机器人）、飞书、Server酱 / Server酱³、邮件（SMTP）、Gotify、IFTTT、Pushbullet、Pushover、WxPusher、Pusher Receiver、通用 Webhook、自定义 HTTP 服务、JavaScript 脚本服务、iOS 快捷指令
- **中文界面**：设置面板与日志均为中文友好

## 系统要求

| 项目 | 要求 |
|---|---|
| 设备 | iPhone / iPad（arm64） |
| 系统 | iOS 15.0 – 16.x |
| 越狱 | **Dopamine** / palera1n rootless / roothide（rootful 经典越狱不支持本包） |
| 依赖 | AltList（[opa334 源](https://opa334.github.io/)）、libSandyXpc（本仓库源内置镜像，自动安装） |

## 安装

### 方式一：Sileo 软件源（推荐）

1. Sileo → 软件源 → 右上角「+」，添加：
   ```
   https://hlakbrr.github.io/TextRelay/
   ```
2. 搜索 **TextRelay** 安装（Dopamine 设备装 `TextRelay-rootless`，roothide 设备装 `TextRelay-roothide`）。
3. 首次安装前请确保已添加 [opa334 官方源](https://opa334.github.io/)，依赖 AltList 会自动拉取。

### 方式二：手动安装 deb

从 [Releases](https://github.com/hlakbrr/TextRelay/releases) 下载对应架构的 deb：

- `com.hlakbrr.textrelay_*_iphoneos-arm64.deb` → rootless（Dopamine / palera1n 无根）
- `com.hlakbrr.textrelay-*_iphoneos-arm64e.deb` → roothide

下载到「文件」App 本地目录后，用 Sileo 打开安装。

## 使用

1. 越狱后打开 **设置 → TextRelay**；
2. 「服务」里添加一个转发渠道（如 Bark：填入你设备 Key 即可）并测试；
3. 开启总开关；如需短信转发，打开「收信」相关开关，双卡用户可为每个卡槽命名；
4. 需要只转发验证码等特定短信时，添加过滤规则（关键词/正则），黑名单可防止 Bark 等本机 App 造成循环推送。

### 注意事项

- 短信转发依赖「信息」App 的系统通知，请保持其通知权限开启；
- **重启后需重新越狱**（Dopamine 为半不完美越狱）；未越狱期间收到的短信不会被转发；
- 本工具与上游 Pusher 一样仅供学习研究，请勿用于违反当地法律法规的用途；短信内容敏感，转发目标服务的安全性自行评估。

## 构建

CI（GitHub Actions，macOS runner）在发布 Release 时自动构建两种架构的 deb 并上传；也可本地构建：

```bash
# 需要 Theos，以及 AltList / SandyXpc 两个依赖装进 $THEOS（见 .github/workflows/build.yml）
THEOS_PACKAGE_SCHEME=rootless make clean package   # Dopamine / palera1n 无根
THEOS_PACKAGE_SCHEME=roothide make clean package   # roothide
```

产物在 `packages/` 目录。

## 致谢与版权

- [NoahSaso/Pusher](https://github.com/NoahSaso/Pusher) — 原始 Pusher 插件（本仓库代码的主要来源）
- [jzksnsjswkw/Pusher-rootless](https://github.com/jzksnsjswkw/Pusher-rootless) — rootless 移植、中文界面与新增服务
- [pppscn/SmsForwarder](https://github.com/pppscn/SmsForwarder) — 安卓端「短信转发器」，本项目移植目标
- [opa334/AltList](https://github.com/opa334/AltList)、[Lessica/SandyXpc](https://github.com/Lessica/SandyXpc)、[roothide](https://github.com/roothide) — 运行时依赖

上游均未附带开源许可证，代码仅供个人学习研究使用，请勿商用；各商标（Bark、钉钉、企业微信、飞书、WxPusher 等）归其所有者所有。详见 [NOTICE.md](NOTICE.md)。
