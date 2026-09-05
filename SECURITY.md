# Security Policy

## Supported versions

当前 `main` 分支和最近一次 GitHub Release 受支持；旧版本不主动修复。

## Reporting a vulnerability

请通过 GitHub Private vulnerability reporting 私密报告，不要公开 Issue 中粘贴本地路径、录制内容或其他敏感信息。

报告请包含：

- 影响版本
- 复现步骤
- 影响范围

## Scope

本工具为本地 Windows 工具，运行时不访问网络。如发现以下问题，欢迎报告：

- 外部命令/文件读取导致本地路径意外泄漏
- 构建或发布流程引入供应链风险
- 录制内容被意外写到非预期位置
