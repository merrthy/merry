# 深海翻译 ShenHai Translate

一个只做一件事的 Chrome 扩展：**打开英文网页 → 点一下图标 → 整页变成中文**。

## 来源

本项目是开源项目 **[TWP - Translate Web Pages](https://github.com/FilipePS/Traduzir-paginas-web)**
（`FilipePS/Traduzir-paginas-web`，MPL-2.0）的二次开发版本，基于其 `chrome-mv3` 分支。
上游版权与许可遵循 **MPL-2.0**（见 `LICENSE`），本目录下的修改同样以 MPL-2.0 发布。

## 相对上游做了什么

| 文件 | 改动 | 效果 |
| --- | --- | --- |
| `src/lib/config.js` | 默认目标语言 `["en","es","de"]` → `["zh-CN","en","es"]` | 翻译目标默认**简体中文** |
| `src/lib/config.js` | `translateClickingOnce` → `"yes"` | **点图标直接切换整页翻译**，不弹面板 |
| `src/lib/config.js` | 首次安装时持久化中文优先配置 | 即使浏览器语言是英文，默认也是译成中文；之后用户仍可自行修改 |
| `src/lib/config.js` | `useOldPopup` → `"no"`、`showReleaseNotes` → `"no"` | 界面统一一套，首装不弹更新说明 |
| `src/background/background.js` | 移除新旧弹窗分支 | 代码更干净 |
| `src/popup/popup.{html,js}`、`src/options/options.{html,js}` | 删除"切换旧版界面"入口 | 界面更简洁 |
| `src/popup/old-popup.*` | 删除 | — |
| `src/_locales/` | 43 种语言 → 仅 `en` + `zh_CN` | 体积更小 |
| `src/firefox-manifest.json` | 删除 | Chrome 端不需要 |
| `src/manifest.json` | 名称 → `深海翻译`，版本 `10.2.5.1` | — |

## 目录说明

- `src/` —— **这就是可直接加载的扩展目录**（Manifest V3，无需构建）
- `dist/`、`extra/` —— 上游构建产物与辅助脚本，不使用

## 安装

1. Chrome 打开 `chrome://extensions/`，开启右上角「开发者模式」
2. 点「加载已解压的扩展程序」，选择本仓库的 `src` 目录
3. 建议把扩展固定到工具栏

## 使用

- 点工具栏图标 → 整页英文变中文；再点一次 → 恢复原文
- 右键图标 → 「显示弹窗」打开完整面板 / 「更多选项」进入设置
- 快捷键 `Alt+T` 切换整页翻译
- 翻译引擎默认 Google，免 API Key；可在设置里换 Bing / Yandex

## 许可

MPL-2.0，基于 [FilipePS/Traduzir-paginas-web](https://github.com/FilipePS/Traduzir-paginas-web) 修改。
