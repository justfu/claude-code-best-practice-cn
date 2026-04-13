# 12 种自定义 Claude Code 的方式 — Boris Cherny 的技巧

Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 2 月 12 日分享的自定义技巧摘要。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 背景

Boris Cherny 强调可定制性是工程师最喜爱 Claude Code 的方面之一 — hooks、插件、LSP、MCP、Skills、effort、自定义 agent、状态栏、输出样式等等。他分享了 12 种开发者和团队自定义设置的实际方式。

---

## 1/ 配置你的终端

为最佳的 Claude Code 体验设置你的终端：

- **主题**：运行 `/config` 设置浅色/深色模式
- **通知**：为 iTerm2 启用通知，或使用自定义通知 hook
- **换行**：如果在 IDE 终端、Apple Terminal、Warp 或 Alacritty 中使用 Claude Code，运行 `/terminal-setup` 启用 shift+enter 换行（这样你不需要输入 `\`）
- **Vim 模式**：运行 `/vim`

---

## 2/ 调整 Effort 级别

运行 `/model` 选择你偏好的 effort 级别：

- **Low** — 更少 token，更快响应
- **Medium** — 平衡行为
- **High** — 更多 token，更多智能

Boris 的偏好：一切使用 High。

---

## 3/ 安装插件、MCP 和 Skills

插件让你安装 LSP（支持所有主流语言）、MCP、Skills、Agent 和自定义 hooks。

从官方 Anthropic 插件市场安装，或为你的公司创建自己的市场。将 `settings.json` 提交到代码库以为你的团队自动添加市场。

运行 `/plugin` 开始。

---

## 4/ 创建自定义 Agent

在 `.claude/agents` 中放入 `.md` 文件来创建自定义 Agent。每个 Agent 可以有自定义名称、颜色、工具集、预允许和预拒绝的工具、权限模式和模型。

你还可以使用 `settings.json` 中的 `"agent"` 字段或 `--agent` 标志设置主对话的默认 agent。

运行 `/agents` 开始。

---

## 5/ 预批准常用权限

Claude Code 使用一个结合了提示注入检测、静态分析、沙箱化和人工监督的权限系统。

开箱即用，一组安全命令已被预批准。要预批准更多，运行 `/permissions` 并添加到允许和阻止列表。将这些提交到团队的 `settings.json` 中。

支持完整的通配符语法 — 如 `Bash(bun run *)` 或 `Edit(/docs/**)`。

---

## 6/ 启用沙箱

选择加入 Claude Code 的开源沙箱运行时，在减少权限提示的同时提高安全性。

运行 `/sandbox` 启用。沙箱在你的机器上运行，支持文件和网络隔离。

---

## 7/ 添加状态栏

自定义状态栏显示在输入框正下方，显示模型、目录、剩余上下文、成本以及你工作时要看的任何内容。

每个团队成员可以有不同的状态栏。使用 `/statusline` 让 Claude 根据你的 `.bashrc`/`.zshrc` 生成一个。

---

## 8/ 自定义快捷键

Claude Code 中的每个快捷键都可以自定义。运行 `/keybindings` 重新映射任何键。设置会热重载，你可以立即看到效果。

---

## 9/ 设置 Hooks

Hooks 让你确定性地挂钩到 Claude 的生命周期中：

- 自动将权限请求路由到 Slack 或 Opus
- 在 Claude 到达轮次结束时推动它继续（你甚至可以启动一个 agent 或使用提示来决定 Claude 是否应该继续）
- 预处理或后处理工具调用，例如添加你自己的日志

让 Claude 添加一个 hook 来开始。

---

## 10/ 自定义你的 Spinner 动词

自定义你的 spinner 动词，添加或用你自己的动词替换默认列表。将 `settings.json` 提交到版本控制以与团队共享动词。

---

## 11/ 使用输出样式

运行 `/config` 并设置输出样式，让 Claude 使用不同的语调或格式响应。

- **Explanatory** — 推荐在不熟悉的代码库中使用，让 Claude 在工作时解释框架和代码模式
- **Learning** — 让 Claude 指导你完成代码更改
- **Custom** — 创建自定义输出样式来调整 Claude 的语调

---

## 12/ 自定义一切！

Claude Code 开箱即用就很好用，但当你做了自定义时，将你的 `settings.json` 提交到 git，这样你的团队也能受益。配置支持多个层级：

- 为你的代码库
- 为子文件夹
- 仅为个人
- 通过企业范围的策略

有 37 个设置和 84 个环境变量（在 `settings.json` 中使用 `"env"` 字段来避免包装脚本），你想要的任何行为大概率都是可配置的。

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 2 月 12 日](https://x.com/bcherny)
