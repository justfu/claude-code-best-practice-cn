# Changelog — README CONCEPTS 章节

跟踪 README CONCEPTS 表与官方 Claude Code 文档之间的偏差。

## 状态说明

| 状态 | 含义 |
|------|------|
| ✅ `COMPLETE (原因)` | 操作已执行并成功解决 |
| ❌ `INVALID (原因)` | 发现不正确、不适用或为有意为之 |
| ✋ `ON HOLD (原因)` | 操作已推迟 — 等待外部依赖或用户决定 |

---

## [2026-03-02 11:14 AM PKT] Claude Code v2.1.63

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 链接损坏 | 修复 Permissions URL 从 `/iam` 到 `/permissions` | ✅ COMPLETE (URL 已更新为 /permissions) |
| 2 | HIGH | 缺失概念 | 添加 Agent Teams 行到 CONCEPTS 表 | ✅ COMPLETE (已添加行，位置为 ~\/\.claude\/teams\/) |
| 3 | HIGH | 缺失概念 | 添加 Keybindings 行到 CONCEPTS 表 | ✅ COMPLETE (已添加行，位置为 ~\/\.claude\/keybindings\.json) |
| 4 | HIGH | 缺失概念 | 添加 Model Configuration 行到 CONCEPTS 表 | ✅ COMPLETE (已添加行，位置为 \.claude\/settings\.json) |
| 5 | HIGH | 缺失概念 | 添加 Auto Memory 行到 CONCEPTS 表 | ✅ COMPLETE (已添加行，位置为 ~\/\.claude\/projects\/<project>\/memory\/) |
| 6 | HIGH | 过时锚点 | 修复 Rules URL 锚点从 `#modular-rules-with-clauderules` 到 `#organize-rules-with-clauderules` | ✅ COMPLETE (锚点已更新) |
| 7 | MED | 缺失概念 | 添加 Checkpointing 行到 CONCEPTS 表 | ✅ COMPLETE (已添加行，位置为基于 git 的自动方式) |
| 8 | MED | 缺失概念 | 添加 Status Line 行到 CONCEPTS 表 | ✅ COMPLETE (已添加行，位置为 ~\/\.claude\/settings\.json) |
| 9 | MED | 缺失概念 | 添加 Remote Control 行到 CONCEPTS 表 | ✅ COMPLETE (已添加行，位置为 CLI \/ claude\.ai) |
| 10 | MED | 缺失概念 | 添加 Fast Mode 行到 CONCEPTS 表 | ✅ COMPLETE (已添加行，位置为 \.claude\/settings\.json) |
| 11 | MED | 缺失概念 | 添加 Headless Mode 行到 CONCEPTS 表 | ✅ COMPLETE (已添加行，位置为 CLI 标志 -p) |
| 12 | LOW | 描述变更 | 更新 Memory 描述以提及自动记忆 | ✅ COMPLETE (描述和位置已更新) |
| 13 | LOW | 位置变更 | 更新 MCP Servers 位置以包含 `.mcp.json` | ✅ COMPLETE (位置已更新以包含 .mcp.json) |
| 14 | LOW | 缺失 Badge | 添加 Implemented badge 到 Hooks 行 | ✅ COMPLETE (已添加 Implemented badge，链接到 .claude/hooks/) |

---

## [2026-03-02 11:57 AM PKT] Claude Code v2.1.63

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 表格合并 | 将 CONCEPTS 表从 22 行合并为 10 行 — 将相关概念折叠为内联文档链接 | ✅ COMPLETE (22 → 10 行) |
| 2 | MED | 合并概念 | 将 Marketplaces 折叠到 Plugins 行作为内联链接 | ✅ COMPLETE (链接到 /discover-plugins) |
| 3 | MED | 合并概念 | 将 Agent Teams 折叠到 Sub-Agents 行作为内联链接 | ✅ COMPLETE (链接到 /agent-teams) |
| 4 | MED | 合并概念 | 将 Permissions、Model Config、Output Styles、Sandboxing、Keybindings、Status Line、Fast Mode 折叠到 Settings 行作为内联链接 | ✅ COMPLETE (7 个概念折叠并带有文档链接) |
| 5 | MED | 合并概念 | 将 Auto Memory 和 Rules 折叠到 Memory 行作为内联链接 | ✅ COMPLETE (链接到 /memory 和 /memory#organize-rules-with-clauderules) |
| 6 | MED | 合并概念 | 将 Headless Mode 折叠到 Remote Control 行作为内联链接 | ✅ COMPLETE (链接到 /headless) |
| 7 | LOW | 重排序 | 按逻辑分组重新排列表格：基础组件 → 扩展 → 配置 → 上下文 → 运行时 | ✅ COMPLETE (按关注点分组，而非按时间) |

---

## [2026-03-07 08:40 AM PKT] Claude Code v2.1.71

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 链接损坏 | 修复 TIPS 中的 `context-management` → `interactive-mode`（第 112、115、135 行） | ✅ COMPLETE (3 处替换为 interactive-mode) |
| 2 | HIGH | 链接损坏 | 修复 TIPS 中的 `model-configuration` → `model-config`（第 115、116、135 行） | ✅ COMPLETE (3 处替换为 model-config) |
| 3 | HIGH | 链接损坏 | 修复 TIPS 中的 `usage-billing` → `costs`（第 115 行） | ✅ COMPLETE (替换为 costs) |
| 4 | HIGH | 链接损坏 | 移除 STARTUPS 中的 `cowork` URL（第 167 行）— 页面不存在 | ✅ COMPLETE (超链接已移除，纯文本保留) |
| 5 | HIGH | 缺失概念 | 添加 Scheduled Tasks 行到 CONCEPTS 和 Hot 章节（`/loop`，cron 工具） | ✅ COMPLETE (由用户添加到两个表 + /loop 提示 + Boris 推文) |
| 6 | MED | 位置变更 | 更新 Agent Teams 位置从 `.claude/agents/<name>.md` 到 `built-in (env var)` | ✅ COMPLETE (位置已更新为 built-in env var) |

---

## [2026-03-10 01:18 PM PKT] Claude Code v2.1.72

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 链接损坏 | 修复 CONCEPTS 表（第 24 行）中的 Commands URL 从 `/slash-commands` 到 `/skills` — `/slash-commands` 提供 Skills 页面内容；文档说明"commands merged into skills" | ❌ INVALID (URL 仍然有效；用户选择保持原样) |
| 2 | HIGH | 链接损坏 | 修复 TIPS 章节（第 108 行）中的 Commands URL 从 `/slash-commands` 到 `/skills` — 同一个过时的 URL | ❌ INVALID (URL 仍然有效；用户选择保持原样) |
| 3 | MED | 缺失内联链接 | 添加 Interactive Mode（`/interactive-mode`）作为内联链接到 CLI Startup Flags 行 — 覆盖 /compact、/clear、/context、/extra-usage | ✅ COMPLETE (内联链接已添加到 CLI Startup Flags 描述) |
| 4 | MED | 缺失内联链接 | 添加 Costs（`/costs`）作为内联链接到 Settings 行 — 覆盖 /usage、billing、pay-as-you-go | ❌ INVALID (用户选择跳过) |
| 5 | LOW | 缺失概念 | 考虑添加 IDE Integrations 行（VS Code、JetBrains、Desktop App、Web）或内联链接到 Best Practices | ❌ INVALID (用户选择跳过 — 平台表面，非配置概念) |
| 6 | HIGH | 缺失概念 | 添加 Code Review 行到 Hot 表 — 多 agent PR 分析（研究预览版，Teams 和 Enterprise） | ✅ COMPLETE (添加为 Hot 表第一个条目，附带博客链接和最佳实践推文) |
| 7 | MED | 新 Badge | 创建 `!/tags/beta.svg` 标签（黄色，38x20px）并添加到 Hot 表中的 Code Review 和 Agent Teams | ✅ COMPLETE (beta.svg 已创建；已添加到 Code Review 和 Agent Teams 行) |
| 8 | MED | 重排序 | 按发布日期排序 Hot 表（最近的在前）：Code Review → Scheduled Tasks → Voice Mode → Agent Teams → Remote Control → Git Worktrees → Ralph Wiggum | ✅ COMPLETE (Voice Mode 和 Agent Teams 互换以匹配时间顺序) |

---

## [2026-03-12 12:22 PM PKT] Claude Code v2.1.74

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 链接损坏 | 修复 CONCEPTS 表（第 24 行）中的 Commands URL 从 `/slash-commands` 到 `/skills` — `/slash-commands` 重定向到 `/skills` 页面 | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | LOW | 验证 | 所有外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 20+ URL 返回有效页面) |
| 3 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 badge 目标存在于文件系统) |
| 4 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 在目标页面上已验证 | ✅ COMPLETE (标题存在于 /memory 页面) |
| 5 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 | ✅ COMPLETE (未检测到描述偏差) |

---

## [2026-03-15 12:48 PM PKT] Claude Code v2.1.76

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | MED | 缺失 Badges | Remote Control（Hot）没有 badge — 唯一没有任何 BP 或 Impl badge 的 Hot 项 | ✅ COMPLETE (添加了 BP badge，链接到官方文档页面) |
| 3 | LOW | 命名 | README 中的"Sub-Agents"与官方文档中的"subagents"（一个词）— 装饰性不一致 | ✅ COMPLETE (在 CONCEPTS 表中重命名为"Subagents") |
| 4 | LOW | 验证 | 所有 27 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面) |
| 5 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 badge 目标存在于文件系统) |
| 6 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 7 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有 13 个 CONCEPTS + 9 个 Hot 行的描述准确) |

---

## [2026-03-17 12:46 PM PKT] Claude Code v2.1.77

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | HIGH | 描述变更 | Hooks 描述说"Deterministic scripts"，但 hooks 现在包括 4 种类型：command、HTTP、prompt 和 agent — 只有 command hooks 是确定性的 | ✅ COMPLETE (在 CONCEPTS 表中更新为"User-defined handlers (scripts, HTTP, prompts, agents)") |
| 3 | MED | 缺失概念 | Desktop App 在 `/desktop` 有专门的文档页面 — 不在 CONCEPTS 或 Hot 表中 | ❌ INVALID (用户选择跳过 — Desktop 是平台表面，非配置概念) |
| 4 | MED | URL 变更 | Hooks 文档现在分为 Guide（`/hooks-guide`）和 Reference（`/hooks`）— CONCEPTS 仅链接到 Reference | ✅ COMPLETE (Guide 链接已作为内联链接添加到 Hooks 行描述) |
| 5 | LOW | 验证 | 所有 28 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 6 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20 个 badge 目标存在于文件系统) |
| 7 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 8 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 | ✅ COMPLETE (检测到 Hooks 描述偏差 — 见 #2) |

---

## [2026-03-18 11:43 PM PKT] Claude Code v2.1.78

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | HIGH | URL+名称变更 | Hot 表中的 Voice Mode 链接到推文而非官方文档 `/voice-dictation`；官方名称为"Voice Dictation" | ✅ COMPLETE (重命名为"Voice Dictation"，链接到 /voice-dictation，描述已更新；BP badge 保留链接到推文；同时更新了 STARTUPS 表) |
| 3 | LOW | 验证 | 所有 29 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 4 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 5 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 6 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-03-19 11:59 AM PKT] Claude Code v2.1.79

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | LOW | 验证 | 所有 30 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 3 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 4 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 5 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-03-20 08:38 AM PKT] Claude Code v2.1.80

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失概念 | 添加 Channels 行到 Hot 表 — 从 Telegram/Discord/webhooks 将推送事件接入运行中的会话（研究预览版，v2.1.80） | ✅ COMPLETE (添加为 Hot 表第一个条目，附带 beta badge 和 Reference 链接) |
| 2 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 3 | MED | 缺失深度链接 | Git Worktrees URL 应锚点到 `#run-parallel-claude-code-sessions-with-git-worktrees` | ✅ COMPLETE (锚点已添加到 Hot 表中的 Git Worktrees URL) |
| 4 | LOW | 缺失内联链接 | Plugins 行可以添加 `[Marketplaces](https://code.claude.com/docs/en/plugin-marketplaces)` 子链接 | ✅ COMPLETE (Create Marketplaces 内联链接已添加到 Plugins 行) |
| 5 | LOW | 验证 | 所有 31 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 6 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 7 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 8 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-03-21 09:12 PM PKT] Claude Code v2.1.81

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | LOW | 验证 | 所有 32 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 3 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 4 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 5 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 6 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-03-23 09:53 PM PKT] Claude Code v2.1.81

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | LOW | 验证 | 所有 33 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 3 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 4 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 5 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 6 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-03-25 08:12 PM PKT] Claude Code v2.1.83

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | MED | URL 变更 | 简化 & Batch 主链接指向推文而非官方文档 `/skills#bundled-skills` — 现在是官方 bundled skills | ✅ COMPLETE (主链接已更新为 /skills#bundled-skills；BP badge 保留链接到 Boris 的推文) |
| 3 | LOW | 验证 | 所有 34 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 4 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 5 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 6 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 7 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |
| 8 | HIGH | 缺失概念 | 添加 Auto Mode 行到 Hot 表 — 后台安全分类器替代权限提示（研究预览版，Team/Enterprise） | ✅ COMPLETE (添加为 Hot 表第一个条目，附带 beta badge、BP badge 链接到 @claudeai 推文和博客链接) |

---

## [2026-03-26 01:05 PM PKT] Claude Code v2.1.84

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | MED | 缺失概念 | 添加 Slack 集成到 Hot 表 — 在 Slack 中 @Claude 将编码任务路由到 Claude Code web 会话 | ✅ COMPLETE (在 Channels 之后添加行，位置为 @Claude，描述为 web 会话) |
| 3 | MED | 缺失概念 | 添加 GitHub Actions / CI-CD 到 Hot 表 — 在 CI/CD 管道中自动化 PR 审查、issue 分类和代码生成 | ✅ COMPLETE (在 Code Review 之后添加行，位置为 .github/workflows/，GitLab CI/CD 内联链接) |
| 4 | LOW | 验证 | 所有 35 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 5 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 6 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 7 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 8 | LOW | 验证 | Auto Mode 锚点 `#eliminate-prompts-with-auto-mode` 已在 /permission-modes 页面确认 | ✅ COMPLETE (章节标题存在) |
| 9 | LOW | 验证 | Bundled Skills 锚点 `#bundled-skills` 已在 /skills 页面确认 | ✅ COMPLETE (章节标题存在) |
| 10 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-03-27 06:37 PM PKT] Claude Code v2.1.85

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | MED | 缺失概念 | 添加 Chrome 集成到 Hot 表 — 通过 Claude in Chrome 扩展进行浏览器自动化（beta，专门文档在 `/chrome`） | ✅ COMPLETE (在 GitHub Actions 之后添加行，位置为 --chrome，附带 beta badge) |
| 3 | LOW | 验证 | 所有 36 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 4 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 5 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 6 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 7 | LOW | 验证 | Auto Mode 锚点 `#eliminate-prompts-with-auto-mode` 已在 /permission-modes 页面确认 | ✅ COMPLETE (章节标题存在) |
| 8 | LOW | 验证 | Bundled Skills 锚点 `#bundled-skills` 已在 /skills 页面确认 | ✅ COMPLETE (章节标题存在) |
| 9 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-03-28 06:04 PM PKT] Claude Code v2.1.86

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | MED | 缺失 Badge | Hot 表中的 Chrome 行没有 BP badge — 报告存在于 `reports/claude-in-chrome-v-chrome-devtools-mcp.md` | ✅ COMPLETE (添加了 BP badge，链接到 reports/claude-in-chrome-v-chrome-devtools-mcp.md) |
| 3 | LOW | 描述变更 | Plugins 描述缺少 LSP servers — 官方文档列出 `.lsp.json` 为插件组件 | ✅ COMPLETE (在 Plugins 描述中添加了"and LSP servers") |
| 4 | LOW | 验证 | 所有 37 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 5 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 6 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题 `.claude/rules/` 存在) |
| 7 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 8 | LOW | 验证 | Auto Mode 锚点 `#eliminate-prompts-with-auto-mode` 已在 /permission-modes 页面确认 | ✅ COMPLETE (章节标题存在) |
| 9 | LOW | 验证 | Bundled Skills 锚点 `#bundled-skills` 已在 /skills 页面确认 | ✅ COMPLETE (章节标题存在) |
| 10 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确，Plugins LSP 说明除外 — 见 #3) |

---

## [2026-04-01 12:33 PM PKT] Claude Code v2.1.89

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失概念 | 添加 Computer Use 行到 Hot 表 — 通过内置 MCP server 在 macOS 上进行屏幕控制（研究预览版，v2.1.85+） | ✅ COMPLETE (在 Fullscreen Rendering 之后添加行，附带 beta badge 和 Desktop 内联链接) |
| 2 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 3 | MED | 缺失概念 | 添加 Fullscreen Rendering 行到 Hot 表 — 无闪烁的备用屏幕渲染，支持鼠标（研究预览版，v2.1.88+） | ✅ COMPLETE (添加为 Hot 表第一个条目，位置为 CLAUDE_CODE_NO_FLICKER=1) |
| 4 | LOW | 验证 | 所有 38 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 5 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 6 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题存在) |
| 7 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 8 | LOW | 验证 | Auto Mode 锚点 `#eliminate-prompts-with-auto-mode` 已在 /permission-modes 页面确认 | ✅ COMPLETE (章节标题存在) |
| 9 | LOW | 验证 | Bundled Skills 锚点 `#bundled-skills` 已在 /skills 页面确认 | ✅ COMPLETE (章节标题存在) |
| 10 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-04-02 09:17 PM PKT] Claude Code v2.1.90

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 提供 Skills 页面 — 文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然有效；用户选择保持原样) |
| 2 | LOW | 验证 | 所有 39 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 3 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 4 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题"Organize rules with `.claude/rules/`"存在) |
| 5 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 6 | LOW | 验证 | Auto Mode 锚点 `#eliminate-prompts-with-auto-mode` 已在 /permission-modes 页面确认 | ✅ COMPLETE (章节标题存在) |
| 7 | LOW | 验证 | Bundled Skills 锚点 `#bundled-skills` 已在 /skills 页面确认 | ✅ COMPLETE (章节标题存在) |
| 8 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-04-03 08:35 PM PKT] Claude Code v2.1.91

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 不在官方站点地图（llms.txt）中 — 重定向到 `/skills` 页面；文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然通过重定向有效；用户选择保持原样) |
| 2 | LOW | 验证 | 所有 40 个外部文档 URL 已与 llms.txt 站点地图（80 个页面）验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 3 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件（检查了 17 个本地目标） | ✅ COMPLETE (所有 badge 目标存在于文件系统) |
| 4 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题"Organize rules with `.claude/rules/`"存在) |
| 5 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 6 | LOW | 验证 | Auto Mode 锚点 `#eliminate-prompts-with-auto-mode` 已在 /permission-modes 页面确认 | ✅ COMPLETE (章节标题存在) |
| 7 | LOW | 验证 | Bundled Skills 锚点 `#bundled-skills` 已在 /skills 页面确认 | ✅ COMPLETE (章节标题存在) |
| 8 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |

---

## [2026-04-04 10:46 PM PKT] Claude Code v2.1.92

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失概念 | 添加 Ultraplan 行到 Hot 表 — 基于云的计划起草，浏览器审查，内联评论和灵活执行（`/ultraplan`） | ✅ COMPLETE (在 Power-ups 之后添加行，附带 beta badge 和 /ultraplan 位置) |
| 2 | HIGH | 缺失概念 | 添加 Claude Code Web 行到 Hot 表 — 在 claude.ai/code 云基础设施上运行任务，支持 PR 自动修复和并行会话 | ✅ COMPLETE (在 Ultraplan 之后添加行，附带 beta badge，claude.ai/code 位置和 Web Scheduled Tasks 内联链接) |
| 3 | HIGH | 过时 URL | Commands URL `/slash-commands` 不在官方站点地图中 — 重定向到 `/skills` 页面；文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然通过重定向有效；用户选择保持原样) |
| 4 | MED | 缺失概念 | 添加 Desktop App 行到 Hot 表 — 独立应用，带 visual diff、Dispatch、computer use 和并行会话 | ❌ INVALID (从 2026-03-17 重复出现；用户认为它是平台表面，非配置概念) |

---

## [2026-04-08 09:37 PM PKT] Claude Code v2.1.96

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 过时 URL | Commands URL `/slash-commands` 不在官方站点地图中 — 重定向到 `/skills` 页面；文档说明"commands merged into skills" | ❌ INVALID (从 2026-03-10 重复出现；URL 仍然通过重定向有效；用户选择保持原样) |
| 2 | MED | 名称变更 | Hot 表中的"No Flicker Mode" — 官方文档页面标题为"Fullscreen rendering"；考虑重命名或添加副标题 | ❌ INVALID (用户选择保留"No Flicker Mode"，沿用 Boris 的推文命名惯例；环境变量为 `CLAUDE_CODE_NO_FLICKER`) |
| 3 | MED | 缺失概念 | 添加 Desktop App 行到 Hot 表 — 独立应用，带 visual diff、Dispatch、computer use 和并行会话 | ❌ INVALID (从 2026-03-17 重复出现；用户认为它是平台表面，非配置概念) |
| 4 | LOW | 验证 | 所有 41 个外部文档 URL 已验证 — 未发现损坏链接 | ✅ COMPLETE (所有 URL 返回有效页面，包括 /slash-commands 重定向) |
| 5 | LOW | 验证 | 所有本地 badge 文件路径已验证 — 未发现缺失文件 | ✅ COMPLETE (所有 20+ 个 badge 目标存在于文件系统) |
| 6 | LOW | 验证 | Memory 锚点 `#organize-rules-with-clauderules` 已在 /memory 页面确认 | ✅ COMPLETE (章节标题"Organize rules with `.claude/rules/`"存在) |
| 7 | LOW | 验证 | Git Worktrees 锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 已在 /common-workflows 页面确认 | ✅ COMPLETE (章节标题存在) |
| 8 | LOW | 验证 | Auto Mode 锚点 `#eliminate-prompts-with-auto-mode` 已在 /permission-modes 页面确认 | ✅ COMPLETE (章节标题存在) |
| 9 | LOW | 验证 | Bundled Skills 锚点 `#bundled-skills` 已在 /skills 页面确认 | ✅ COMPLETE (章节标题存在) |
| 10 | LOW | 验证 | 所有 CONCEPTS 描述已与官方文档对比检查 — 未检测到偏差 | ✅ COMPLETE (所有描述准确) |
