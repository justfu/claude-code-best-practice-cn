# Claude Code 中 15 个隐藏且被低估的功能 — 来自 Boris Cherny

Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 3 月 30 日分享的技巧总结。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 背景

Boris 分享了他最喜欢的 Claude Code 中隐藏且被低估的功能，重点介绍了他使用最多的那些。

<a href="https://x.com/bcherny/status/2038454336355999749"><img src="assets/boris-30-mar-26/0.png" alt="Boris Cherny 介绍推文" width="50%" /></a>

---

## 1/ Claude Code 有移动端应用

你知道 Claude Code 有移动端应用吗？Boris 经常在 iOS 应用上编写代码——这是一种无需打开笔记本电脑就能进行更改的便捷方式。

- 下载适用于 iOS/Android 的 Claude 应用
- 导航到左侧的 **Code** 标签页
- 你可以直接在手机上审查更改、批准 PR 并编写代码

<a href="https://x.com/bcherny/status/2038454337811386436"><img src="assets/boris-30-mar-26/1.png" alt="Claude Code 移动端应用" width="50%" /></a>

---

## 2/ 在移动端/Web/桌面端和终端之间切换会话

运行 `claude --teleport` 或 `/teleport` 以在你的机器上继续一个云端会话。或者运行 `/remote-control` 从你的手机/Web 控制一个本地运行的会话。

- **Teleport**：将云端会话拉取到你的本地终端
- **Remote Control**：让你从任何设备控制本地会话
- Boris 在他的 `/config` 中设置了 **"Enable Remote Control for all sessions"**

<a href="https://x.com/bcherny/status/2038454339933548804"><img src="assets/boris-30-mar-26/2.png" alt="Teleport 和 Remote Control" width="50%" /></a>

---

## 3/ /loop 和 /schedule — 两个最强大的功能

使用这些功能来安排 Claude 按设定的时间间隔自动运行，一次最长可达一周。Boris 本地运行着许多 loop：

- `/loop 5m /babysit` — 自动处理代码审查、自动 rebase 并将 PR 护送到生产环境
- `/loop 30m /slack-feedback` — 每 30 分钟自动提交 PR 以获取 Slack 反馈
- `/loop /post-merge-sweeper` — 提交 PR 以处理他遗漏的代码审查意见
- `/loop 1h /pr-pruner` — 关闭陈旧的、不再需要的 PR
- ......还有很多更多！

尝试将工作流转化为 skill + loop 的组合。它非常强大。

<a href="https://x.com/bcherny/status/2038454341884154269"><img src="assets/boris-30-mar-26/3.png" alt="/loop 和 /schedule" width="50%" /></a>

---

## 4/ 使用 Hook 确定性运行逻辑

使用 hook 作为 agent 生命周期的一部分来运行逻辑。例如：

- **动态加载**每次启动 Claude 时的上下文（`SessionStart`）
- **记录模型运行的每一个 bash 命令**（`PreToolUse`）
- **将权限提示路由到 WhatsApp**供你批准/拒绝（`PermissionRequest`）
- **提示 Claude**在它停止时继续工作（`Stop`）

<a href="https://x.com/bcherny/status/2038454343519932844"><img src="assets/boris-30-mar-26/4.png" alt="使用 Hook" width="50%" /></a>

---

## 5/ Cowork Dispatch

Boris 每天使用 Dispatch 来处理 Slack 和邮件、管理文件，以及在不面对电脑时在笔记本电脑上完成工作。当他不写代码的时候，他就在 dispatch。

- Dispatch 是 Claude Desktop 应用的**安全远程控制**
- 它可以使用你的 MCP、浏览器和计算机，需要你的许可
- 把它看作一种从任何地方将非编码任务委托给 Claude 的方式

<a href="https://x.com/bcherny/status/2038454345419936040"><img src="assets/boris-30-mar-26/5.png" alt="Cowork Dispatch" width="50%" /></a>

---

## 6/ 使用 Chrome 扩展进行前端工作

使用 Claude Code 最重要的技巧：**给 Claude 一种验证其输出的方式。** 一旦你这样做了，Claude 会不断迭代直到结果出色。

- 想象一下，你让某人构建一个网站但不允许他们使用浏览器——结果很可能不太好看
- 给 Claude 一个浏览器，它会编写代码并不断迭代直到看起来很好
- Boris 每次编写 Web 代码时都使用 Chrome 扩展——它通常比其他类似的 MCP 更可靠

<a href="https://x.com/bcherny/status/2038454347156398333"><img src="assets/boris-30-mar-26/6.png" alt="用于前端的 Chrome 扩展" width="50%" /></a>

---

## 7/ 使用 Claude Desktop 应用自动启动和测试 Web 服务器

沿着同样的思路，Desktop 应用内置了让 Claude **自动运行你的 Web 服务器甚至在内置浏览器中测试**的能力。

- 你可以在 CLI 或 VSCode 中使用 Chrome 扩展设置类似的功能
- 或者直接使用 Desktop 应用获得集成体验

<a href="https://x.com/bcherny/status/2038454348804714642"><img src="assets/boris-30-mar-26/7.png" alt="Desktop 应用 Web 服务器测试" width="50%" /></a>

---

## 8/ Fork 你的会话

人们经常问如何 fork 一个现有的会话。两种方式：

1. 在你的会话中运行 `/branch`
2. 从 CLI 运行 `claude --resume <session-id> --fork-session`

`/branch` 创建一个分支对话——你现在就在这个分支中。要恢复原始会话，使用 `claude -r <original-session-id>`。

<a href="https://x.com/bcherny/status/2038454350214041740"><img src="assets/boris-30-mar-26/8.png" alt="Fork 你的会话" width="50%" /></a>

---

## 9/ 使用 /btw 进行侧面查询

Boris 总是使用这个功能来在 agent 工作时回答快速问题。`/btw` 让你在不打断 agent 当前任务的情况下提出一个侧面问题。

示例：
```
/btw how do I spell dachshund?
> dachshund — German for "badger dog" (dachs + badger, hund + dog).
↑/↓ to scroll · Space, Enter, or Escape to dismiss
```

<a href="https://x.com/bcherny/status/2038454351849787485"><img src="assets/boris-30-mar-26/9.png" alt="/btw 侧面查询" width="50%" /></a>

---

## 10/ 使用 Git Worktree

Claude Code 内置了对 git worktree 的深度支持。Worktree 对于在同一仓库中进行大量并行工作至关重要。Boris 始终有**几十个 Claude 在同时运行**，这就是他做到的方式。

- 使用 `claude -w` 在 worktree 中启动新会话
- 或者在 Claude Desktop 应用中勾选 **"worktree" 复选框**
- 对于非 git VCS 用户，使用 `WorktreeCreate` hook 添加你自己的 worktree 创建逻辑

<a href="https://x.com/bcherny/status/2038454353787519164"><img src="assets/boris-30-mar-26/10.png" alt="Git worktree" width="50%" /></a>

---

## 11/ 使用 /batch 扩展大规模变更集

`/batch` 会对你进行采访，然后让 Claude 将工作分散到尽可能多的 **worktree agent**（数十个、数百个甚至数千个）来完成。

- 适用于大型代码迁移和其他可并行化的工作
- 每个 worktree agent 在代码库的独立副本上独立工作

<a href="https://x.com/bcherny/status/2038454355469484142"><img src="assets/boris-30-mar-26/11.png" alt="/batch 大规模变更集" width="50%" /></a>

---

## 12/ 使用 --bare 将 SDK 启动速度提升最高 10 倍

默认情况下，当你运行 `claude -p`（或 TypeScript 或 Python SDK）时，Claude 会搜索本地的 CLAUDE.md、settings 和 MCP。但对于非交互式使用，大多数时候你希望通过 `--system-prompt`、`--mcp-config`、`--settings` 等显式指定要加载的内容。

- 这是 SDK 最初构建时的一个设计疏忽
- 在未来版本中，他们会将默认值切换为 `--bare`
- 目前，使用该标志来获得最高 **10 倍的启动加速**

```bash
claude -p "summarize this codebase" \
    --output-format=stream-json \
    --verbose \
    --bare
```

<a href="https://x.com/bcherny/status/2038454357088457168"><img src="assets/boris-30-mar-26/12.png" alt="--bare 标志加速 SDK 启动" width="50%" /></a>

---

## 13/ 使用 --add-dir 让 Claude 访问更多文件夹

在跨多个仓库工作时，Boris 通常在一个仓库中启动 Claude，并使用 `--add-dir`（或 `/add-dir`）让 Claude 看到另一个仓库。

- 这不仅告诉 Claude 该仓库的存在，还**授予它权限**在该仓库中工作
- 或者，将 `"additionalDirectories"` 添加到团队的 `settings.json` 中，以便在启动 Claude Code 时始终加载额外的文件夹

<a href="https://x.com/bcherny/status/2038454359047156203"><img src="assets/boris-30-mar-26/13.png" alt="--add-dir 多仓库" width="50%" /></a>

---

## 14/ 使用 --agent 为 Claude Code 提供自定义系统提示和工具

Custom agent 是一个强大且经常被忽视的原语。要使用它，只需在 `.claude/agents/` 中定义一个新 agent，然后运行：

```bash
claude --agent=<your agent's name>
```

- Agent 可以有受限的工具、自定义描述和特定模型
- 它们非常适合创建只读 agent、专门的审查 agent 或领域特定的工具

<a href="https://x.com/bcherny/status/2038454360418787764"><img src="assets/boris-30-mar-26/14.png" alt="--agent 自定义系统提示" width="50%" /></a>

---

## 15/ 使用 /voice 启用语音输入

有趣的事实：Boris 通过对 Claude 说话来完成大部分编码，而不是打字。

- 在 CLI 中运行 `/voice` 然后按住空格键说话
- 在 Desktop 应用中按语音按钮
- 或者在 iOS 设置中启用听写功能

<a href="https://x.com/bcherny/status/2038454362226467112"><img src="assets/boris-30-mar-26/15.png" alt="/voice 语音输入" width="50%" /></a>

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 3 月 30 日](https://x.com/bcherny/status/2038454336355999749)
