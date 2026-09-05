# Wallpaper Export

> Windows 工具：从 Wallpaper Engine 播放窗口直接录制并导出 MP4，使用 NVENC 硬件编码，无需 OBS。

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## 简介

Wallpaper Export 是一个 Windows 本地工具，直接从 Wallpaper Engine 的渲染窗口截取画面并编码为 MP4，避免 OBS 录制窗口带来的额外配置。工具自动查找 Wallpaper Engine 安装路径，并在录制前将渲染窗口置顶。

## 功能

- 使用 `h264_nvenc` 硬件编码（需要带 NVENC 的 ffmpeg）。
- 命令行与图形界面两种用法。
- 自动查找 Wallpaper Engine 安装路径。
- 录制前强制置顶 WE 渲染窗口。

## 环境要求

- Windows
- Wallpaper Engine
- ffmpeg（含 `h264_nvenc`，并加入 PATH）

## 使用

### 命令行

```bash
WallpaperExport.exe --wallpaper "...\project.json" --width 1920 --height 1080 --seconds 15
```

### 图形界面

```bash
WallpaperExport.exe --gui
```

### 参数

| 参数 | 说明 |
|---|---|
| `--wallpaper` | Wallpaper Engine 壁纸 `project.json` 路径 |
| `--width` / `--height` | 输出分辨率，默认全屏 |
| `--seconds` | 录制秒数，默认 15 |
| `--framerate` | 帧率，默认 60 |
| `--output` | 输出 MP4 路径 |
| `--upscale` | 可选放大，如 `2560x1440` |
| `--gui` | 打开图形界面 |

## 构建

```bash
pip install pyinstaller
python -m PyInstaller --noconfirm --onefile --windowed --name WallpaperExport \
  --collect-all tkinter export_we_wallpaper.py
```

推送 `v*` tag 后，GitHub Actions 会自动构建并发布 `WallpaperExport.exe`。

## 开发

源码入口为 `export_we_wallpaper.py`。项目是 Windows-only 的本地工具，无运行时网络依赖；请不要引入跨项目依赖。

## 贡献

欢迎提交 Issue 与 Pull Request。提交前请确认改动保持工具自包含，并避免加入网络/遥测逻辑。

## 安全

本工具不访问网络、不上传数据。若发现漏洞或隐私问题，请通过 GitHub Private vulnerability reporting 报告，不要在公开 Issue 中贴本地路径或敏感信息。

## 许可证

[MIT](LICENSE)
