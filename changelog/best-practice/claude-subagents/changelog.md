# Subagents 报告 — 变更历史

## 状态说明

| 状态 | 含义 |
|------|------|
| ✅ `COMPLETE (原因)` | 操作已执行并成功解决 |
| ❌ `INVALID (原因)` | 发现不正确、不适用或为有意为之 |
| ✋ `ON HOLD (原因)` | 操作已推迟 — 等待外部依赖或用户决定 |

---

## [2026-02-28 03:22 PM PKT] Claude Code v2.1.63

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Agents 表 | 将 `workflow-changelog-claude-agents-frontmatter-agent` 添加到 Agents in This Repository 表 | ✅ COMPLETE (已添加，model: opus，继承所有 tools，无 skills/memory) |
| 2 | HIGH | Agents 表 | 修复 presentation-curator 的 skills 列 — 为 skill 名称添加 `presentation/` 前缀 | ✅ COMPLETE (更新为 presentation/vibe-to-agentic-framework 等) |
| 3 | MED | 字段文档 | 在 `color` 字段中添加注释，说明其功能正常但不在官方 frontmatter 表中 | ✅ COMPLETE (在描述列中添加了非官方状态说明) |
| 4 | MED | 调用章节 | 扩展调用章节，添加 --agents CLI 标志、/agents 命令、claude agents CLI、agent 恢复 | ✅ COMPLETE (添加了包含 5 种方法的调用方法表) |

---

## [2026-03-07 08:35 AM PKT] Claude Code v2.1.71

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 链接损坏 | 修复 agent memory 链接到 `reports/claude-agent-memory.md` | ✅ COMPLETE |
| 2 | HIGH | 行为变更 | 更新 `tools` 字段描述：`Task(agent_type)` → `Agent(agent_type)`（v2.1.63 重命名） | ✅ COMPLETE |
| 3 | HIGH | 行为变更 | 更新调用章节：Task tool → Agent tool（v2.1.63 重命名） | ✅ COMPLETE (更新了标题、代码示例并添加了重命名说明) |
| 4 | HIGH | 示例更新 | 更新完整示例：`Task(monitor, rollback)` → `Agent(monitor, rollback)` | ✅ COMPLETE |
| 5 | HIGH | 内置 Agent | 将 `Bash` agent 添加到 Official Claude Agents 表（model: inherit，用途：在单独上下文中执行终端命令） | ✅ COMPLETE (已添加到表中) |
| 6 | HIGH | Agents 表 | 将 `workflow-concepts-agent` 添加到 Agents in This Repository 表（model: opus，color: green） | ✅ COMPLETE |
| 7 | HIGH | Agents 表 | 将 `workflow-claude-settings-agent` 添加到 Agents in This Repository 表（model: opus，color: yellow） | ✅ COMPLETE |
| 8 | MED | 内置 Agent | 修复 `statusline-setup` model：`inherit` → `Sonnet` | ✅ COMPLETE |
| 9 | MED | 内置 Agent | 修复 `claude-code-guide` model：`inherit` → `Haiku` | ❌ NOT APPLICABLE (已从表中移除) |
| 10 | MED | Agents 表 | 修复 `weather-agent` color：`teal` → `green` | ✅ COMPLETE |
| 11 | MED | 调用方法 | 将 `--agent <name>` CLI 标志添加到调用方法表 | ✅ COMPLETE (添加为调用方法表的第一行) |
| 12 | MED | 行为变更 | 更新第 147 行文本："Task tool" → "Agent tool"在 Official Claude Agents 表标题中 | ✅ COMPLETE (用户重写了标题文本) |
| 13 | MED | 跨文件 | 更新 CLAUDE.md：`Task(...)` → `Agent(...)` 引用（第 50-53、61 行） | ✅ COMPLETE (更新了编排章节和 tools 字段描述) |

---

## [2026-03-12 12:17 PM PKT] Claude Code v2.1.74

未检测到偏差 — 报告与官方文档完全同步。所有 13 个 frontmatter 字段和 6 个内置 agent 匹配。

---

## [2026-03-13 04:21 PM PKT] Claude Code v2.1.74

未检测到偏差 — 报告与官方文档完全同步。所有 13 个 frontmatter 字段和 6 个内置 agent 匹配。

---

## [2026-03-15 12:50 PM PKT] Claude Code v2.1.76

未检测到偏差 — 报告与官方文档完全同步。所有 13 个 frontmatter 字段和 6 个内置 agent 匹配。

---

## [2026-03-17 12:42 PM PKT] Claude Code v2.1.77

未检测到偏差 — 报告与官方文档完全同步。所有 13 个 frontmatter 字段和 6 个内置 agent 匹配。

---

## [2026-03-18 11:41 PM PKT] Claude Code v2.1.78

未检测到偏差 — 报告与官方文档完全同步。所有 13 个 frontmatter 字段和 6 个内置 agent 匹配。

---

## [2026-03-19 11:56 AM PKT] Claude Code v2.1.79

未检测到偏差 — 报告与官方文档完全同步。所有 13 个 frontmatter 字段和 6 个内置 agent 匹配。

---

## [2026-03-20 08:35 AM PKT] Claude Code v2.1.80

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新字段 | 将 `effort` 字段添加到 Frontmatter Fields 表（字符串，可选 — effort 级别覆盖：`low`、`medium`、`high`、`max`） | ✅ COMPLETE (添加在 `background` 和 `isolation` 之间，计数更新 14→15) |

---

## [2026-03-21 09:07 PM PKT] Claude Code v2.1.81

未检测到偏差 — 报告与官方文档完全同步。所有 15 个 frontmatter 字段和 6 个内置 agent 匹配。

---

## [2026-03-23 09:49 PM PKT] Claude Code v2.1.81

未检测到偏差 — 报告与官方文档完全同步。所有 15 个 frontmatter 字段（14 个官方 + 1 个非官方 `color`）和 6 个内置 agent 匹配。

---

## [2026-03-25 08:07 PM PKT] Claude Code v2.1.83

未检测到偏差 — 报告与官方文档完全同步。所有 15 个 frontmatter 字段（14 个官方 + 1 个非官方 `color`）和 6 个内置 agent 匹配。

**关注项：** `initialPrompt` 在 v2.1.83 changelog 中添加，但尚未出现在官方文档支持的 frontmatter 字段表中。当出现时，报告需要更新。

---

## [2026-03-26 01:01 PM PKT] Claude Code v2.1.84

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新字段 | 将 `initialPrompt` 添加到 Frontmatter Fields 表（字符串，可选 — 当 agent 通过 `--agent` 或 `agent` 设置作为主会话 agent 运行时自动作为第一个用户轮次提交） | ✅ COMPLETE (添加在 `isolation` 和 `color` 之间，计数更新 15→16) |

---

## [2026-03-27 06:28 PM PKT] Claude Code v2.1.85

未检测到偏差 — 报告与官方文档完全同步。所有 16 个 frontmatter 字段（15 个官方 + 1 个非官方 `color`）和 6 个内置 agent 匹配。

---

## [2026-03-28 06:00 PM PKT] Claude Code v2.1.86

未检测到偏差 — 报告与官方文档完全同步。所有 16 个 frontmatter 字段（15 个官方 + 1 个非官方 `color`）和 6 个内置 agent 匹配。

---

## [2026-04-01 12:26 PM PKT] Claude Code v2.1.89

未检测到偏差 — 报告与官方文档完全同步。所有 16 个 frontmatter 字段（15 个官方 + 1 个非官方 `color`）和 6 个内置 agent 匹配。

---

## [2026-04-02 09:11 PM PKT] Claude Code v2.1.90

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 移除 Agent | 从 Official Claude Agents 表中移除 `Bash` — 官方文档列出 5 个内置 agent，`Bash` 不在其中 | ✅ COMPLETE (移除了 Bash 行，重新编号 6→5 个 agent) |
| 2 | LOW | 字段文档 | 更新 `color` 字段描述 — 移除"不在官方 frontmatter 表中"注释；`color` 现在出现在官方支持的 frontmatter 字段表中 | ✅ COMPLETE (从 color 字段描述中移除了非官方注释) |

---

## [2026-04-03 08:30 PM PKT] Claude Code v2.1.91

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | LOW | 字段文档 | 更新 `permissionMode` 字段描述 — 添加 `auto` 作为有效值（官方文档现在列出：`default`、`acceptEdits`、`auto`、`dontAsk`、`bypassPermissions`、`plan`） | ✅ COMPLETE (在 permissionMode 描述中将 `auto` 添加在 `acceptEdits` 和 `dontAsk` 之间) |

---

## [2026-04-04 10:43 PM PKT] Claude Code v2.1.92

未检测到偏差 — 报告与官方文档完全同步。所有 16 个 frontmatter 字段和 5 个内置 agent 匹配。

---

## [2026-04-08 09:34 PM PKT] Claude Code v2.1.96

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | LOW | 字段文档 | 更新 `model` 字段描述 — 添加完整 model ID 支持（如 `claude-opus-4-6`）以及别名 | ✅ COMPLETE (更新描述以匹配官方文档措辞) |
| 2 | LOW | 字段文档 | 更新 `effort` 字段描述 — 添加 `max (Opus 4.6 only)` 限定符 | ✅ COMPLETE (在 max 选项中添加了 Opus 4.6 only 说明) |
| 3 | LOW | 字段文档 | 更新 `color` 字段描述 — 将 `(e.g., green, magenta)` 替换为明确的有效值：`red`、`blue`、`green`、`yellow`、`purple`、`orange`、`pink`、`cyan` | ✅ COMPLETE (将基于示例的描述替换为穷举的有效值列表) |
