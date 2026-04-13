# 如何使用 Claude Code — Boris Cherny 的 13 条技巧

Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 1 月 3 日分享的设置技巧总结。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 背景

Boris 分享了他个人的 Claude Code 设置，并指出它"出人意料地朴实"——Claude Code 开箱即用就非常出色，所以他不需要太多自定义。使用它没有唯一正确的方式：团队刻意将其构建为你可以随心所欲地使用、定制和改造的工具。Claude Code 团队中的每个人使用方式都截然不同。

<a href="https://x.com/bcherny/status/2007179832300581177"><img src="assets/boris-3-jan-26/0.png" alt="Boris Cherny 介绍推文" width="50%" /></a>

---

## 1/ 并行运行 5 个 Claude

在终端中并行运行 5 个 Claude。将标签页编号为 1-5，并使用系统通知来了解某个 Claude 何时需要输入。

参见：[终端设置文档](https://code.claude.com/docs/en/terminal)

<a href="https://x.com/bcherny/status/2007179833990885678"><img src="assets/boris-3-jan-26/1.png" alt="并行运行 5 个 Claude" width="50%" /></a>

---

## 2/ 使用 claude.ai/code 实现更大规模并行

在 claude.ai/code 上并行运行 5-10 个 Claude，与本地 Claude 同时使用。使用 `claude.ai/code` 将本地会话交接给 Web 会话，在 Chrome 中手动启动会话，并在两者之间来回切换。

<a href="https://x.com/bcherny/status/2007179836704600237"><img src="assets/boris-3-jan-26/2.png" alt="claude.ai/code 并行" width="50%" /></a>

---

## 3/ 所有任务都使用带思考的 Opus

所有任务都使用带思考功能的 Opus 4.5。这是 Boris 用过的最好的编码模型——虽然它比 Sonnet 更大更慢，但因为你需要引导它的次数更少，而且它在工具使用方面更强，最终几乎总是比使用更小的模型更快。

<a href="https://x.com/bcherny/status/2007179838864666847"><img src="assets/boris-3-jan-26/3.png" alt="带思考的 Opus" width="50%" /></a>

---

## 4/ 与团队共享一个 CLAUDE.md

为仓库共享一个 `CLAUDE.md`。将其提交到 git，并让整个团队每周多次贡献内容。每当 Claude 做错了什么，就将其添加到 `CLAUDE.md` 中，这样 Claude 下次就知道不该这么做了。

<a href="https://x.com/bcherny/status/2007179840848597422"><img src="assets/boris-3-jan-26/4.png" alt="共享 CLAUDE.md" width="50%" /></a>

---

## 5/ 在 PR 上 @claude 以更新 CLAUDE.md

在代码审查期间，在同事的 PR 上标记 `@claude`，将内容添加到 `CLAUDE.md` 作为 PR 的一部分。使用 Claude Code GitHub action（[install-@hub-action](https://github.com/apps/claude)）来完成此操作——这是 Boris 版本的"复利工程"。

<a href="https://x.com/bcherny/status/2007179842928947333"><img src="assets/boris-3-jan-26/5.png" alt="在 PR 上标记 @claude" width="50%" /></a>

---

## 6/ 大多数会话从 Plan 模式开始

大多数会话从 Plan 模式开始（按两次 shift+tab）。如果目标是编写一个 Pull Request，请使用 Plan 模式，与 Claude 来回交流直到你对它的方案满意。然后切换到自动接受编辑模式，Claude 通常可以一次完成。一个好的方案真的很重要。

<a href="https://x.com/bcherny/status/2007179845336527000"><img src="assets/boris-3-jan-26/6.png" alt="Plan 模式" width="50%" /></a>

---

## 7/ 使用 Slash 命令处理内循环工作流

对每个你每天要做很多次的"内循环"工作流使用 slash 命令。这可以避免你反复输入提示词，也让 Claude 能够使用这些工作流。命令被提交到 git 并存放在 `.claude/commands/` 中。

例如：`/commit-push-pr`——提交、推送并创建 PR。

<a href="https://x.com/bcherny/status/2007179847949500714"><img src="assets/boris-3-jan-26/7.png" alt="Slash 命令" width="50%" /></a>

---

## 8/ 使用 Subagent 自动化常见工作流

定期使用几个 subagent：`code-simplifier` 在 Claude 完成工作后简化代码，`verify-app` 包含了端到端测试 Claude Code 的详细说明，等等。可以将 subagent 视为自动化最常见工作流——类似于 slash 命令。

Subagent 存放在 `.claude/agents/` 中。

<a href="https://x.com/bcherny/status/2007179850139000872"><img src="assets/boris-3-jan-26/8.png" alt="Subagent" width="50%" /></a>

---

## 9/ 使用 PostToolUse Hook 自动格式化代码

使用 `PostToolUse` hook 来格式化 Claude 生成的代码。Claude 通常开箱即用就能生成格式良好的代码，而 hook 处理最后的 10%，以避免 CI 中的格式化错误。

```json
"PostToolUse": [
  {
    "matcher": "Write|Edit",
    "hooks": [
      {
        "type": "command",
        "command": "bun run format || true"
      }
    ]
  }
]
```

<a href="https://x.com/bcherny/status/2007179852047335529"><img src="assets/boris-3-jan-26/9.png" alt="PostToolUse hook 用于格式化" width="50%" /></a>

---

## 10/ 预授权权限而非使用 --dangerously-skip-permissions

不要使用 `--dangerously-skip-permissions`。相反，使用 `/permissions` 预先授权你确认在环境中安全的常见 bash 命令，以避免不必要的权限提示。其中大部分会被提交到 `.claude/settings.json` 并与团队共享。

<a href="https://x.com/bcherny/status/2007179854077407667"><img src="assets/boris-3-jan-26/10.png" alt="预授权权限" width="50%" /></a>

---

## 11/ 通过 MCP 让 Claude 使用你所有的工具

Claude Code 使用你所有的工具。它经常搜索和发布到 Slack（通过 MCP server），运行 BigQuery 查询来回答分析问题（使用 `bq` CLI），从 Sentry 获取错误日志等。Slack MCP 配置被提交到 `.mcp.json` 并与团队共享。

<a href="https://x.com/bcherny/status/2007179856266789204"><img src="assets/boris-3-jan-26/11.png" alt="MCP 工具" width="50%" /></a>

---

## 12/ 使用 Background Agent 验证长时间运行的任务

对于非常长时间运行的任务，可以 (a) 提示 Claude 在完成后使用 background agent 验证其工作，(b) 使用 agent Stop hook 更确定性地完成此操作，或者 (c) 使用 ralph-wiggum 插件（最初由 @GeoffreyHuntley 构想）。

<a href="https://x.com/bcherny/status/2007179858435281082"><img src="assets/boris-3-jan-26/12.png" alt="长时间运行任务验证" width="50%" /></a>

---

## 13/ 给 Claude 一种验证其工作的方式

这可能是从 Claude Code 获得出色结果最重要的一点——给 Claude 一种验证其工作的方式。如果 Claude 有了这个反馈循环，它将把最终结果的质量提高 2-3 倍。

Claude 会测试 Boris 提交的每一个更改。

<a href="https://x.com/bcherny/status/2007179861115511237"><img src="assets/boris-3-jan-26/13.png" alt="给 Claude 验证方式" width="50%" /></a>

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 1 月 3 日](https://x.com/bcherny/status/2007179832300581177)
