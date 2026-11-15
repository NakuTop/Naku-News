# Naku News

面向 macOS 的个人新闻、视频与播客阅读器，基于开源 [Folo](https://github.com/RSSNext/Folo) 定制。

- NAS 账户登录，各账户独立订阅与阅读状态。
- RSS 发现、分类选源、全文阅读及中英对照。
- B 站、抖音应用内播放；播客与本机双语字幕。
- NAS 共享 AI；本机字幕处理无需模型 API Token。
- Sparkle 签名更新，支持差分包与完整包回退。

## 下载与更新

正式版本在 [Releases](https://github.com/NakuTop/Naku-News/releases) 下载。当前提供 Apple Silicon 版本。
安装后通过「Naku News → 检查更新」更新，后台默认每 4 小时检查一次；安装重启由用户确认。

需要配套的私人 NAS 后端。发布包不包含 NAS 密码、API Key 或平台 Cookie。
当前包采用本机 ad-hoc 代码签名和独立 Ed25519 更新签名，未进行 Apple 公证。

## 源码与许可

Naku News 的 Folo 衍生客户端遵循 GPL-3.0。每个正式 Release 附对应的完整客户端源码、原生辅助程序及构建脚本。
原项目及依赖的版权声明保留；Sparkle 的许可证随更新辅助程序一并分发。

本仓库承载下载和已签名更新目录，不承载私人 NAS 数据。
