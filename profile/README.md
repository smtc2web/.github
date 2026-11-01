<div align="center">

<img src="https://avatars.githubusercontent.com/u/330889906?v=4" alt="smtc2web" width="120" height="120">

# smtc2web

**让直播间知道你现在在听什么。**

我们做一款开源的桌面媒体桥接工具：把操作系统当前正在播放的媒体信息取出来，
通过本机 HTTP 服务交给 OBS 浏览器源渲染成浮层。主程序用 Rust 编写，
界面是 Tauri 2 + Vue 3，Windows 走 SMTC、Linux 走 MPRIS2，主题可换可热更新。

[![Release](https://img.shields.io/github/v/release/smtc2web/smtc2web?color=blue&label=release)](https://github.com/smtc2web/smtc2web/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/smtc2web/smtc2web/total?label=downloads)](https://github.com/smtc2web/smtc2web/releases)
[![Stars](https://img.shields.io/github/stars/smtc2web/smtc2web?style=social)](https://github.com/smtc2web/smtc2web/stargazers)
[![Contributors](https://img.shields.io/github/contributors/smtc2web/smtc2web?label=contributors)](https://github.com/smtc2web/smtc2web/graphs/contributors)
[![Website](https://img.shields.io/badge/Web-smtc2web.org-4B32C3)](https://smtc2web.org)
[![License](https://img.shields.io/badge/License-MIT-green?label=main%20app)](https://github.com/smtc2web/smtc2web/blob/master/LICENSE)

</div>

---

## 我们要解决的问题

主播放歌时，直播画面里的手动改字、外挂插件、平台限定都很麻烦。
smtc2web 直接读取系统级的媒体会话，在本机起一个很小的 HTTP 服务，
OBS 里加一个浏览器源指过去就有了。不依赖直播平台，不上传数据，默认只听 `127.0.0.1`。

## 仓库一览

| 仓库 | 作用 |
| --- | --- |
| [smtc2web](https://github.com/smtc2web/smtc2web) | 主程序：Rust + Tauri 2 + Vue 3，Windows SMTC / Linux MPRIS2 → 本机 HTTP → OBS |
| [smtc2web-website](https://github.com/smtc2web/smtc2web-website) | 官网与内置 Wiki，文档、下载与捐赠入口都在这里 |
| [smtc2web-dev](https://github.com/smtc2web/smtc2web-dev) | 面向 smtc2web 开发环境的命令行工具 |
| [smtc2web-themes](https://github.com/smtc2web/smtc2web-themes) | 主题商店，可免费下载或发布主题 |
| [theme-upload](https://github.com/smtc2web/theme-upload) | 主题发布流水线，让主题的更新分发更省事 |
| [r2-dir-list](https://github.com/smtc2web/r2-dir-list) | Cloudflare R2 下载镜像的目录列表页（fork 自 cmj2002/r2-dir-list） |
| [smtc2web-theme-spotify](https://github.com/smtc2web/smtc2web-theme-spotify) | Spotify 风格主题，在组织内作为公开模板维护；主程序子模块目前指向 `AkarinLiu/smtc2web-theme-spotify` |
| [smtc2web-theme-default](https://github.com/smtc2web/smtc2web-theme-default) | 主题开发模板，从这里起步写自己的主题 |

## 快速上手

1. 到 [Releases](https://github.com/smtc2web/smtc2web/releases/latest) 下载对应平台的安装包
   （Windows x64 / arm64，Linux amd64 / arm64 的 deb 与 rpm），
   也可以用镜像站 <https://download.smtc2web.org>。
2. 启动 smtc2web，托盘出现图标后它会自动读取正在播放的内容。
3. OBS 新建 **浏览器** 来源，URL 填 `http://localhost:3030`。改过监听端口的话同步改这里。
4. 想换个样子，去主题页启用内置主题，或者从主题商店下载、从 Git 仓库安装。

构建与打包说明见 Wiki：<https://smtc2web.org/wiki/compile>。

## 开发与工具链

- 主仓库的 Node 与 pnpm 版本由 [mise](https://mise.jdx.dev/) 通过 `.mise.toml` 锁定，
  Rust 仍使用 rustup 的 stable 工具链；进入目录后 `mise install && pnpm install` 即可开工。
- CI 在 Windows 与 Linux、x86_64 与 aarch64 四种组合上跑 `cargo check` 与
  `cargo clippy -- -D warnings`，另有 `vue-tsc` 类型检查。
- 安装包经 minisign 签名，客户端通过更新端点校验后才安装。

## 社区与贡献

- 参与方式见 [CONTRIBUTING.md](https://github.com/smtc2web/smtc2web/blob/master/CONTRIBUTING.md)，
  行为准则见 [CODE_OF_CONDUCT.md](https://github.com/smtc2web/smtc2web/blob/master/CODE_OF_CONDUCT.md)。
- 提功能或问题：Issues 里已备好缺陷与功能请求两套模板。
- 实时交流：[Zed 社区频道](https://zed.dev/channel/smtc2web-31825)，或写信到 <hello@smtc2web.org>。
- 长期贡献、修复过恶意漏洞或提供关键代码的参与者，会按贡献者指南的说明获得 Maintainer 权限。
- 本项目靠爱发电，欢迎<a href="https://smtc2web.org/#%E6%8D%90%E8%B5%A0">捐赠支持</a>。

## 安全

请**不要**用公开 Issue 报告漏洞，走私密安全公告：
<https://github.com/smtc2web/smtc2web/security/advisories/new>。
安全政策与响应时限见 [SECURITY.md](https://github.com/smtc2web/smtc2web/blob/master/SECURITY.md)，
只有最新的补丁版本会获得安全更新。

## English

<details>
<summary>smtc2web organization overview</summary>

smtc2web builds an open-source desktop media bridge. It reads the operating system's
current media session (SMTC on Windows, MPRIS2 on Linux) and exposes it over a small
local HTTP server so an OBS Browser source can render a now-playing overlay — no
platform lock-in, no telemetry, bound to `127.0.0.1` by default.

- **Start here**: grab the latest installer from [Releases](https://github.com/smtc2web/smtc2web/releases/latest)
  or the [R2 mirror](https://download.smtc2web.org), then point an OBS Browser source at `http://localhost:3030`.
- **Repositories**: the [main app](https://github.com/smtc2web/smtc2web),
  the [website and wiki](https://github.com/smtc2web/smtc2web-website),
  a [dev CLI](https://github.com/smtc2web/smtc2web-dev),
  a [theme store](https://github.com/smtc2web/smtc2web-themes) with a
  [publishing pipeline](https://github.com/smtc2web/theme-upload),
  an [R2 directory listing](https://github.com/smtc2web/r2-dir-list),
  plus the [embedded Spotify theme](https://github.com/smtc2web/smtc2web-theme-spotify)
  and a [theme template](https://github.com/smtc2web/smtc2web-theme-default).
- **Tooling**: Node and pnpm are pinned by [mise](https://mise.jdx.dev/) in the app repo,
  Rust comes from rustup; CI covers Windows and Linux on x86_64 and aarch64.
- **Security**: report vulnerabilities privately through
  [security advisories](https://github.com/smtc2web/smtc2web/security/advisories/new);
  only the latest patch release is supported.
- **Licenses**: not uniform — the app, the dev CLI, the theme pipeline and the R2 listing are MIT,
  both theme repos are CC0-1.0, and the website plus theme store have no license declared yet.
- **Docs**: <https://smtc2web.org/wiki/compile>

</details>

## 许可

各仓库的许可以其仓库内的 LICENSE 文件为准，并不统一：

| 范围 | 许可 |
| --- | --- |
| 主程序 smtc2web、smtc2web-dev、theme-upload、r2-dir-list | MIT |
| 两个主题仓库（spotify / default） | CC0 1.0 Universal，贡献到公有领域 |
| smtc2web-website、smtc2web-themes | 暂未声明，复用前请先开 Issue 确认 |

欢迎 fork、改造，把主题带进你的直播间。
