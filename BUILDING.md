# 构建 Naku News

Release 的 `source.tar.gz` 包含当前修改后的 Folo 客户端、原生字幕/翻译辅助程序、更新辅助程序和构建脚本。解压后的目录结构为 `folo/`、`native/`、`scripts/`。

在 Apple Silicon Mac 上安装 Xcode Command Line Tools、Node.js 22.21+ 和 pnpm，然后：

```sh
cd Naku-News-1.0.0-source
python3 scripts/fetch-news-sparkle.py
cd folo
pnpm install --frozen-lockfile
cd ..
NAKU_FFMPEG_BINARY=/absolute/path/to/arm64/ffmpeg NAKU_NEWS_BUILD=101 \
  bash scripts/build-nas-macos.sh --url https://your-nas-news.example.com \
  --output /absolute/path/to/new-output-directory
```

Sparkle 固定为 2.9.6，并在下载后验证官方归档 SHA-256。FFmpeg 使用可运行的 arm64 构建；本机字幕通过系统 Speech/Translation 框架处理。

自建分发请替换 `forge.config.cts` 中的更新地址和公钥，使用自己的 Ed25519 私钥签署。私钥存入 macOS 钥匙串，不写入代码、归档或后端。`scripts/prepare-news-release.py` 生成差分、还原验证及已签名 appcast。先上传并校验完整包、差分包与校验文件，最后再更新线上 appcast。

原测试版没有更新器，无法远程给旧程序凭空添加更新能力；需先安装带更新器的版本。发布后的客户端按数字 `CFBundleVersion` 比较更新，每个正式构建递增，市场版本使用 `package.json` 的版本。
