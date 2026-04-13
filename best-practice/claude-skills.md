# Skills 最佳实践

![Last Updated](https://img.shields.io/badge/Last_Updated-Apr%2008%2C%202026%209%3A33%20PM%20PKT-white?style=flat&labelColor=555) ![Version](https://img.shields.io/badge/Claude_Code-v2.1.96-blue?style=flat&labelColor=555)<br>
[![Implemented](https://img.shields.io/badge/Implemented-2ea44f?style=flat)](../implementation/claude-skills-implementation.md)

Claude Code Skills — frontmatter 字段和官方内置 Skills。

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
| `description` | string | 推荐 | Skill 的功能描述。显示在自动补全中，Claude 用它进行自动发现 |
| `argument-hint` | string | 否 | 自动补全时显示的提示（如 `[issue-number]`、`[filename]`） |
| `disable-model-invocation` | boolean | 否 | 设为 `true` 阻止 Claude 自动调用此 Skill |
| `user-invocable` | boolean | 否 | 设为 `false` 从 `/` 菜单中隐藏 — Skill 变为仅供后台加载的知识，用于 agent 预加载 |
| `allowed-tools` | string | 否 | 当此 Skill 激活时，允许无需权限提示即可使用的工具 |
| `model` | string | 否 | 此 Skill 运行时使用的模型（如 `haiku`、`sonnet`、`opus`） |
| `effort` | string | 否 | 调用时覆盖模型的 effort 级别（`low`、`medium`、`high`、`max`） |
| `context` | string | 否 | 设为 `fork` 在隔离的 subagent 上下文中运行此 Skill |
| `agent` | string | 否 | 当 `context: fork` 时设置的 subagent 类型（默认：`general-purpose`） |
| `hooks` | object | 否 | 限定于此 Skill 作用域的生命周期 hooks |
| `paths` | string/list | 否 | 限制 Skill 自动激活的 Glob 模式。接受逗号分隔的字符串或 YAML 列表 — Claude 仅在与匹配文件工作时才加载该 Skill |
| `shell` | string | 否 | `` !`command` `` 块的 Shell — `bash`（默认）或 `powershell`。需要 `CLAUDE_CODE_USE_POWERSHELL_TOOL=1` |

---

## ![官方](../!/tags/official.svg) **（5 个）**

| # | Skill | 描述 |
|---|-------|-------------|
| 1 | `simplify` | 审查已更改的代码，检查复用性、质量和效率 — 重构以消除重复 |
| 2 | `batch` | 批量对多个文件运行命令 |
| 3 | `debug` | 调试失败的命令或代码问题 |
| 4 | `loop` | 在循环间隔中运行提示或 slash 命令（最长 3 天） |
| 5 | `claude-api` | 使用 Claude API 或 Anthropic SDK 构建应用 — 在导入 `anthropic` / `@anthropic-ai/sdk` 时触发 |

另见：[官方 Skills 仓库](https://github.com/anthropics/skills/tree/main/skills) 获取社区维护的可安装 Skills。

---

## 来源

- [Claude Code Skills — 官方文档](https://code.claude.com/docs/en/skills)
- [Monorepo 中的 Skills 发现](../reports/claude-skills-for-larger-mono-repos.md)
- [Claude Code 更新日志](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
