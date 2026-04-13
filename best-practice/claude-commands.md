# Commands 最佳实践

![Last Updated](https://img.shields.io/badge/Last_Updated-Apr%2008%2C%202026%209%3A35%20PM%20PKT-white?style=flat&labelColor=555) ![Version](https://img.shields.io/badge/Claude_Code-v2.1.96-blue?style=flat&labelColor=555)<br>
[![Implemented](https://img.shields.io/badge/Implemented-2ea44f?style=flat)](../implementation/claude-commands-implementation.md)

Claude Code Commands — frontmatter 字段和官方内置 slash 命令。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## Frontmatter 字段（13 个）

| 字段 | 类型 | 是否必需 | 描述 |
|-------|------|----------|-------------|
| `name` | string | 否 | 显示名称和 `/slash-command` 标识符。省略时默认为目录名 |
| `description` | string | 推荐 | 命令的功能描述。显示在自动补全中，Claude 用它进行自动发现 |
| `argument-hint` | string | 否 | 自动补全时显示的提示（如 `[issue-number]`、`[filename]`） |
| `disable-model-invocation` | boolean | 否 | 设为 `true` 阻止 Claude 自动调用此命令 |
| `user-invocable` | boolean | 否 | 设为 `false` 从 `/` 菜单中隐藏 — 命令变为仅供后台加载的知识 |
| `paths` | string/list | 否 | 限制此 Skill 激活条件的 Glob 模式。接受逗号分隔的字符串或 YAML 列表。设置后，Claude 仅在与匹配文件工作时才自动加载该 Skill |
| `allowed-tools` | string | 否 | 当此命令激活时，允许无需权限提示即可使用的工具 |
| `model` | string | 否 | 此命令运行时使用的模型（如 `haiku`、`sonnet`、`opus`） |
| `effort` | string | 否 | 调用时覆盖模型的 effort 级别（`low`、`medium`、`high`、`max`） |
| `context` | string | 否 | 设为 `fork` 在隔离的 subagent 上下文中运行此命令 |
| `agent` | string | 否 | 当 `context: fork` 时设置的 subagent 类型（默认：`general-purpose`） |
| `shell` | string | 否 | `` !`command` `` 块的 Shell — 接受 `bash`（默认）或 `powershell`。需要 `CLAUDE_CODE_USE_POWERSHELL_TOOL=1` |
| `hooks` | object | 否 | 限定于此命令作用域的生命周期 hooks |

---

## ![官方](../!/tags/official.svg) **（65 个）**

| # | 命令 | 标签 | 描述 |
|---|---------|-----|-------------|
| 1 | `/login` | ![认证](https://img.shields.io/badge/Auth-2980B9?style=flat) | 登录你的 Anthropic 账户 |
| 2 | `/logout` | ![认证](https://img.shields.io/badge/Auth-2980B9?style=flat) | 从你的 Anthropic 账户登出 |
| 3 | `/setup-bedrock` | ![认证](https://img.shields.io/badge/Auth-2980B9?style=flat) | 通过交互式向导配置 Amazon Bedrock 身份验证、区域和模型固定。仅在设置 `CLAUDE_CODE_USE_BEDROCK=1` 时可见。首次使用 Bedrock 的用户也可以从登录屏幕访问此向导 |
| 4 | `/upgrade` | ![认证](https://img.shields.io/badge/Auth-2980B9?style=flat) | 打开升级页面切换到更高级别的订阅计划 |
| 5 | `/color [color\|default]` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 设置当前会话的提示栏颜色。可用颜色：`red`、`blue`、`green`、`yellow`、`purple`、`orange`、`pink`、`cyan`。使用 `default` 重置 |
| 6 | `/config` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 打开设置界面，调整主题、模型、输出样式和其他偏好设置。别名：`/settings` |
| 7 | `/keybindings` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 打开或创建你的快捷键配置文件 |
| 8 | `/permissions` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 管理工具权限的允许、询问和拒绝规则。打开交互式对话框，可以按作用域查看规则、添加或删除规则、管理工作目录以及查看最近 Auto Mode 的拒绝记录。别名：`/allowed-tools` |
| 9 | `/privacy-settings` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 查看和更新你的隐私设置。仅限 Pro 和 Max 订阅用户使用 |
| 10 | `/sandbox` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 切换沙箱模式。仅在支持的平台上可用 |
| 11 | `/statusline` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 配置 Claude Code 的状态栏。描述你想要的效果，或不带参数运行以从 shell 提示符自动配置 |
| 12 | `/stickers` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 订购 Claude Code 贴纸 |
| 13 | `/terminal-setup` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 配置终端快捷键，如 Shift+Enter 等。仅在需要它的终端中可见，如 VS Code、Alacritty 或 Warp |
| 14 | `/theme` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 更改颜色主题。包括浅色和深色变体、色盲友好（daltonized）主题，以及使用终端调色板的 ANSI 主题 |
| 15 | `/voice` | ![配置](https://img.shields.io/badge/Config-F39C12?style=flat) | 切换按住说话语音听写功能。需要 Claude.ai 账户 |
| 16 | `/context` | ![上下文](https://img.shields.io/badge/Context-8E44AD?style=flat) | 以彩色网格可视化当前上下文使用情况。显示上下文密集型工具的优化建议、memory 膨胀和容量警告 |
| 17 | `/cost` | ![上下文](https://img.shields.io/badge/Context-8E44AD?style=flat) | 显示 token 使用统计。查看费用跟踪指南了解订阅特定详情 |
| 18 | `/extra-usage` | ![上下文](https://img.shields.io/badge/Context-8E44AD?style=flat) | 配置额外用量，在遇到速率限制时继续工作 |
| 19 | `/insights` | ![上下文](https://img.shields.io/badge/Context-8E44AD?style=flat) | 生成分析你 Claude Code 会话的报告，包括项目领域、交互模式和摩擦点 |
| 20 | `/stats` | ![上下文](https://img.shields.io/badge/Context-8E44AD?style=flat) | 可视化每日使用量、会话历史、连续使用天数和模型偏好 |
| 21 | `/status` | ![上下文](https://img.shields.io/badge/Context-8E44AD?style=flat) | 打开设置界面（状态标签），显示版本、模型、账户和连接信息。在 Claude 响应时也可使用，无需等待当前响应完成 |
| 22 | `/usage` | ![上下文](https://img.shields.io/badge/Context-8E44AD?style=flat) | 显示计划使用限制和速率限制状态 |
| 23 | `/doctor` | ![调试](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 诊断和验证你的 Claude Code 安装和设置 |
| 24 | `/feedback [report]` | ![调试](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 提交关于 Claude Code 的反馈。别名：`/bug` |
| 25 | `/help` | ![调试](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 显示帮助和可用命令 |
| 26 | `/powerup` | ![调试](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 通过带有动画演示的快速互动课程发现 Claude Code 功能 |
| 27 | `/release-notes` | ![调试](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 在交互式版本选择器中查看更新日志。选择特定版本查看发布说明，或选择显示所有版本 |
| 28 | `/tasks` | ![调试](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 列出和管理后台任务。别名：`/bashes` |
| 29 | `/copy [N]` | ![导出](https://img.shields.io/badge/Export-7F8C8D?style=flat) | 将最后一条助手响应复制到剪贴板。传递数字 `N` 复制倒数第 N 条响应：`/copy 2` 复制倒数第二条。当代码块存在时，显示交互式选择器来选择单个代码块或完整响应。在选择器中按 `w` 将选择内容写入文件而非剪贴板，在 SSH 下特别有用 |
| 30 | `/export [filename]` | ![导出](https://img.shields.io/badge/Export-7F8C8D?style=flat) | 将当前对话导出为纯文本。带文件名则直接写入该文件。不带则打开对话框，选择复制到剪贴板或保存到文件 |
| 31 | `/agents` | ![扩展](https://img.shields.io/badge/Extensions-16A085?style=flat) | 管理 Agent 配置 |
| 32 | `/chrome` | ![扩展](https://img.shields.io/badge/Extensions-16A085?style=flat) | 配置 Claude in Chrome 设置 |
| 33 | `/hooks` | ![扩展](https://img.shields.io/badge/Extensions-16A085?style=flat) | 查看工具事件的 hook 配置 |
| 34 | `/ide` | ![扩展](https://img.shields.io/badge/Extensions-16A085?style=flat) | 管理 IDE 集成并显示状态 |
| 35 | `/mcp` | ![扩展](https://img.shields.io/badge/Extensions-16A085?style=flat) | 管理 MCP 服务器连接和 OAuth 身份验证 |
| 36 | `/plugin` | ![扩展](https://img.shields.io/badge/Extensions-16A085?style=flat) | 管理 Claude Code 插件 |
| 37 | `/reload-plugins` | ![扩展](https://img.shields.io/badge/Extensions-16A085?style=flat) | 重新加载所有活动插件以应用待定更改，无需重启。报告每个重新加载组件的计数并标记任何加载错误 |
| 38 | `/skills` | ![扩展](https://img.shields.io/badge/Extensions-16A085?style=flat) | 列出可用的 Skills |
| 39 | `/memory` | ![记忆](https://img.shields.io/badge/Memory-3498DB?style=flat) | 编辑 `CLAUDE.md` 记忆文件、启用或禁用自动记忆、查看自动记忆条目 |
| 40 | `/effort [low\|medium\|high\|max\|auto]` | ![模型](https://img.shields.io/badge/Model-E67E22?style=flat) | 设置模型 effort 级别。`low`、`medium` 和 `high` 跨会话保持。`max` 仅限当前会话，需要 Opus 4.6。`auto` 重置为模型默认值。不带参数显示当前级别。立即生效，无需等待当前响应完成 |
| 41 | `/fast [on\|off]` | ![模型](https://img.shields.io/badge/Model-E67E22?style=flat) | 开启或关闭快速模式 |
| 42 | `/model [model]` | ![模型](https://img.shields.io/badge/Model-E67E22?style=flat) | 选择或切换 AI 模型。支持的模型可用左右箭头调整 effort 级别。更改立即生效，无需等待当前响应完成 |
| 43 | `/passes` | ![模型](https://img.shields.io/badge/Model-E67E22?style=flat) | 与朋友分享一周免费 Claude Code。仅在账户符合条件时可见 |
| 44 | `/plan [description]` | ![模型](https://img.shields.io/badge/Model-E67E22?style=flat) | 直接从提示栏进入 plan 模式。传递可选描述以进入 plan 模式并立即开始该任务，例如 `/plan fix the auth bug` |
| 45 | `/ultraplan <prompt>` | ![模型](https://img.shields.io/badge/Model-E67E22?style=flat) | 在 ultraplan 会话中起草计划，在浏览器中审查，然后远程执行或发送回终端 |
| 46 | `/add-dir <path>` | ![项目](https://img.shields.io/badge/Project-27AE60?style=flat) | 向当前会话添加新的工作目录 |
| 47 | `/diff` | ![项目](https://img.shields.io/badge/Project-27AE60?style=flat) | 打开交互式 diff 查看器，显示未提交的更改和每轮的 diff。用左右箭头在当前 git diff 和各个 Claude 轮次之间切换，用上下箭头浏览文件 |
| 48 | `/init` | ![项目](https://img.shields.io/badge/Project-27AE60?style=flat) | 用 `CLAUDE.md` 指南初始化项目。设置 `CLAUDE_CODE_NEW_INIT=1` 启用交互式流程，还会引导你了解 Skills、Hooks 和个人记忆文件 |
| 49 | `/review` | ![项目](https://img.shields.io/badge/Project-27AE60?style=flat) | 已弃用。请改为安装 `code-review` 插件：`claude plugin install code-review@claude-plugins-official` |
| 50 | `/security-review` | ![项目](https://img.shields.io/badge/Project-27AE60?style=flat) | 分析当前分支上的待提交更改是否存在安全漏洞。审查 git diff 并识别注入、身份验证问题和数据泄露等风险 |
| 51 | `/desktop` | ![远程](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 在 Claude Code 桌面应用中继续当前会话。仅限 macOS 和 Windows。别名：`/app` |
| 52 | `/install-github-app` | ![远程](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 为仓库设置 Claude GitHub Actions 应用。引导你选择仓库和配置集成 |
| 53 | `/install-slack-app` | ![远程](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 安装 Claude Slack 应用。打开浏览器完成 OAuth 流程 |
| 54 | `/mobile` | ![远程](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 显示 QR 码以下载 Claude 移动应用。别名：`/ios`、`/android` |
| 55 | `/remote-control` | ![远程](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 使此会话可从 claude.ai 远程控制。别名：`/rc` |
| 56 | `/remote-env` | ![远程](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 配置用 `--remote` 启动的 Web 会话的默认远程环境 |
| 57 | `/schedule [description]` | ![远程](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 创建、更新、列出或运行云定时任务。Claude 会以对话方式引导你完成设置 |
| 58 | `/branch [name]` | ![会话](https://img.shields.io/badge/Session-4A90D9?style=flat) | 在此点创建当前对话的分支。别名：`/fork` |
| 59 | `/btw <question>` | ![会话](https://img.shields.io/badge/Session-4A90D9?style=flat) | 问一个快速侧面问题，不会添加到对话中 |
| 60 | `/clear` | ![会话](https://img.shields.io/badge/Session-4A90D9?style=flat) | 清除对话历史并释放上下文。别名：`/reset`、`/new` |
| 61 | `/compact [instructions]` | ![会话](https://img.shields.io/badge/Session-4A90D9?style=flat) | 压缩对话，可选聚焦指令 |
| 62 | `/exit` | ![会话](https://img.shields.io/badge/Session-4A90D9?style=flat) | 退出 CLI。别名：`/quit` |
| 63 | `/rename [name]` | ![会话](https://img.shields.io/badge/Session-4A90D9?style=flat) | 重命名当前会话并在提示栏显示名称。不带名称则从对话历史自动生成 |
| 64 | `/resume [session]` | ![会话](https://img.shields.io/badge/Session-4A90D9?style=flat) | 通过 ID 或名称恢复对话，或打开会话选择器。别名：`/continue` |
| 65 | `/rewind` | ![会话](https://img.shields.io/badge/Session-4A90D9?style=flat) | 回退对话和/或代码到之前的点，或从选定的消息开始总结。参见 checkpointing。别名：`/checkpoint` |

`/debug` 等内置 Skill 也会出现在 slash 命令菜单中，但它们不是内置命令。

---

## 来源

- [Claude Code Slash 命令](https://code.claude.com/docs/en/slash-commands)
- [Claude Code 交互模式](https://code.claude.com/docs/en/interactive-mode)
- [Claude Code 更新日志](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
