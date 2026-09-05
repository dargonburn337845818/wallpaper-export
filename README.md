# Wallpaper Export

Wallpaper Engine 高清导出工具（NVENC，无需 OBS）。

从 Wallpaper Engine 的播放窗口直接截取并编码为 MP4，支持：

- `h264_nvenc` 硬件编码（需安装带 NVENC 的 ffmpeg）
- 命令行 / 图形界面两种用法
- 自动查找 Wallpaper Engine 安装路径
- 录制前强制置顶 WE 渲染窗口

## 用法

```bash
# 命令行
WallpaperExport.exe --wallpaper "...\project.json" --width 1920 --height 1080 --seconds 15

# 图形界面
WallpaperExport.exe --gui
```

命令行参数：

| 参数 | 说明 |
|---|---|
| `--wallpaper` | Wallpaper Engine 壁纸 `project.json` 路径 |
| `--width` / `--height` | 输出分辨率（默认全屏） |
| `--seconds` | 录制秒数（默认 15） |
| `--framerate` | 帧率（默认 60） |
| `--output` | 输出 MP4 路径 |
| `--upscale` | 可选放大，如 `2560x1440` |
| `--gui` | 打开图形界面 |

## 环境要求

- Windows
- Wallpaper Engine
- ffmpeg（含 `h264_nvenc`，请加入 PATH）

## 构建 EXE

```bash
pip install pyinstaller
python -m PyInstaller --noconfirm --onefile --windowed --name WallpaperExport \
  --collect-all tkinter export_we_wallpaper.py
```

仓库已配置 GitHub Actions：推 `v*` tag 会自动构建并发布 `WallpaperExport.exe`。

## License

MIT
