# NOTICE — 版权与署名

## 代码来源

本仓库的代码主体来自以下上游项目（按时间顺序）：

1. **NoahSaso/Pusher** — <https://github.com/NoahSaso/Pusher>
   原始「Pusher」iOS 越狱插件：将设备通知转发到各种推送服务。本仓库的全部核心流水线、偏好面板与其余大部分源码衍生于该项目。

2. **jzksnsjswkw/Pusher-rootless** — <https://github.com/jzksnsjswkw/Pusher-rootless>
   Pusher 的 rootless/roothide 移植版（iOS 15–16），新增中文界面、Bark/飞书/企业微信等服务与短信（sms.db 卡槽查询）支持。本仓库直接衍生于该项目。

3. **pppscn/SmsForwarder** — <https://github.com/pppscn/SmsForwarder>
   安卓端「短信转发器」应用，为本项目的移植目标与功能参照；其代码未被复制进本仓库。

## 修改内容

本仓库（hlakbrr/TextRelay）相对 jzksnsjswkw/Pusher-rootless 的修改：

- 全部包名、类名、偏好域名、XPC 服务名等标识符由 `com.jzksnsjswkw.pusher` / `Pusher` 重命名为 `com.hlakbrr.textrelay` / `TextRelay`，以避免与上游包冲突；
- 设置面板保留「原作者 @NoahSaso」与上游链接入口；
- 新增本 README / NOTICE，重写 Sileo 源发布流程（发布到本仓库 gh-pages）。

## 许可证状态

截至本仓库创建时，上述上游项目**均未附带开源许可证**（仓库中无 LICENSE 文件）。因此：

- 本仓库代码同样**不授予任何形式的商用许可**，仅供个人学习、研究与自己设备上使用；
- 如果你是对上游代码拥有权利的作者，且认为本仓库的衍生发布不妥，请通过 Issue 联系，我们会及时处理（下架/私有为私有分支）；
- 原作者链接保留于设置面板与本文件中，请勿移除。

## 商标

Bark、钉钉、企业微信、飞书、Server酱、Pushover、Pushbullet、IFTTT、WxPusher、Gotify 等名称与图标为各自所有者的商标，本项目中的引用仅用于表明转发通道的兼容性，不代表任何合作或背书。
