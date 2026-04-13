# 10 个使用 Claude Code 的技巧 — 来自 Claude Code 团队

Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 2 月 1 日分享的团队技巧摘要。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 背景

Boris 分享了直接来自 Claude Code 团队的使用技巧。团队使用 Claude 的方式与 Boris 个人使用的方式不同。记住：没有一种"正确"的 Claude Code 使用方式 — 每个人的设置都不同。你应该实验看看什么适合你！

---

## 1/ 多做并行工作

一次启动 3-5 个 git worktree，每个并行运行自己的 Claude 会话。这是最大的生产力提升，也是团队的榜首技巧。Boris 个人使用多个 git checkout，但 Claude Code 团队更偏好 worktree — 这就是 `@amorisscode` 在 Claude 桌面应用中构建原生支持的原因！

有些人会给 worktree 命名并设置 shell 别名（`2a`、`2b`、`2c`），这样一键就能切换。还有人有一个专用的"分析" worktree，仅用于读取日志和运行 BigQuery。

---

## 2/ 每个复杂任务都在 Plan 模式开始

把精力投入计划中，让 Claude 能一次性完成实现。

一个人让一个 Claude 写计划，然后启动第二个 Claude 以 Staff Engineer 的身份审查。

另一个人说，一旦事情出错了，他们就切换回 Plan 模式重新规划。不要继续硬推。他们还会明确告诉 Claude 进入 Plan 模式来进行验证步骤，而不仅仅是构建。

---

## 3/ 投资你的 CLAUDE.md

每次纠正后，以这句话结束："更新你的 CLAUDE.md 以免再犯这个错误。"Claude 在为自己编写规则方面出奇地擅长。

随着时间推移无情地编辑你的 `CLAUDE.md`。持续迭代，直到 Claude 的错误率明显下降。

一位工程师让 Claude 为每个任务/项目维护一个笔记目录，每次 PR 后更新。然后将 `CLAUDE.md` 指向它。

---

## 4/ 创建你自己的 Skills 并提交到 Git

在每个项目中复用。团队的技巧：

- 如果你每天做某件事超过一次，把它变成 Skill 或 Command
- 构建一个 `/techdebt` slash 命令，在每个会话结束时运行以查找和消灭重复代码
- 设置一个 slash 命令，将 7 天的 Slack、GDrive、Asana 和 GitHub 同步到一个上下文中
- 构建分析工程师风格的 agent，编写 dbt 模型、审查代码并在开发中测试更改

---

## 5/ Claude 自己能修复大部分 Bug

团队的做法：

启用 Slack MCP，然后把 Slack bug 线程粘贴到 Claude 中，只说"修复"。零上下文切换。

或者，直接说"去修复失败的 CI 测试"。不要微管理怎么做。

将 Claude 指向 Docker 日志来排查分布式系统 — 它在这方面出人意料地能干。

---

## 6/ 提升你的提示技巧

a. **挑战 Claude。** 说"严格审查这些更改，在我通过你的测试之前不要创建 PR。"让 Claude 做你的审查者。或者说"向我证明这有效"，让 Claude 对比 main 和你的功能分支之间的行为差异。

b. **修复不太理想时，** 说："知道你现在知道的一切，放弃这个并实现优雅的方案。"

c. **写详细的规格说明**，在交接工作之前减少歧义。你越具体，输出越好。

---

## 7/ 终端和环境设置

团队喜欢 Ghostty！多人喜欢它的同步渲染、24 位颜色和正确的 Unicode 支持。

为了更方便地管理多个 Claude 会话，使用 `/statusline` 自定义状态栏，始终显示上下文使用量和当前 git 分支。很多人还会用颜色编码和命名他们的终端标签，有时使用 tmux — 每个标签对应一个任务/worktree。

使用语音听写。你说话的速度是打字的 3 倍，而且你的提示会因此更加详细。（在 macOS 上按 fn x2）

---

## 8/ 使用 Subagents

a. 在任何你想让 Claude 投入更多计算来解决问题的请求后面加上"使用 subagents"。

b. 将各个任务卸载到 subagent，以保持主 agent 的上下文窗口干净和聚焦。

c. 通过 hook 将权限请求路由到 Opus — 让它扫描攻击并自动批准安全的请求。

---

## 9/ 用 Claude 做数据和分析

让 Claude Code 使用 "bq" CLI 实时拉取和分析指标。团队有一个 BigQuery Skill 提交在代码库中，每个人都在 Claude Code 中直接用于分析查询。Boris 个人已经 6 个多月没写过一行 SQL 了。

这适用于任何有 CLI、MCP 或 API 的数据库。

---

## 10/ 用 Claude 学习

团队使用 Claude Code 学习的几个技巧：

a. 在 `/config` 中启用"Explanatory"或"Learning"输出样式，让 Claude 解释其更改背后的"原因"。

b. 让 Claude 生成一个可视化 HTML 演示文稿来解释不熟悉的代码。它制作幻灯片出人意料地好！

c. 让 Claude 绘制新协议和代码库的 ASCII 图，帮助你理解它们。

d. 构建一个间隔重复学习 Skill：你解释你的理解，Claude 提出后续问题填补空白，存储结果。

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 2 月 1 日](https://x.com/bcherny/status/2017742741636321619)
