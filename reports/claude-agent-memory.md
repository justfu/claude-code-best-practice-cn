# Claude Code：Agent Memory Frontmatter

Sub-agent 的持久化记忆 — 让 agent 能够跨会话学习、记忆和积累知识。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 概述

在 **Claude Code v2.1.33**（2026 年 2 月）中引入，`memory` frontmatter 字段为每个 subagent 提供了自己的持久化基于 markdown 的知识存储。在此之前，每次 agent 调用都从零开始。

```yaml
---
name: code-reviewer
description: 审查代码质量和最佳实践
tools: Read, Write, Edit, Bash
model: sonnet
memory: user
---

你是一个代码审查者。在审查代码时，将你发现的模式、约定和常见问题更新到你的 agent 记忆中。
```

---

## Memory 作用域

| 作用域 | 存储位置 | 版本控制 | 共享 | 适用场景 |
|-------|-----------------|-------------------|--------|----------|
| `user` | `~/.claude/agent-memory/<agent-name>/` | 否 | 否 | 跨项目知识（推荐默认值） |
| `project` | `.claude/agent-memory/<agent-name>/` | 是 | 是 | 团队应共享的项目特定知识 |
| `local` | `.claude/agent-memory-local/<agent-name>/` | 否（git-ignored） | 否 | 个人的项目特定知识 |

这些作用域镜像了设置层级（`~/.claude/settings.json` → `.claude/settings.json` → `.claude/settings.local.json`）。

---

## 工作原理

1. **启动时**：`MEMORY.md` 的前 200 行被注入到 agent 的系统提示中
2. **工具访问**：`Read`、`Write`、`Edit` 自动启用，agent 可以管理自己的记忆
3. **执行期间**：Agent 可以自由读写其记忆目录
4. **管理**：如果 `MEMORY.md` 超过 200 行，agent 会将详情移到特定主题文件中

```
~/.claude/agent-memory/code-reviewer/     # user 作用域示例
├── MEMORY.md                              # 主文件（前 200 行加载）
├── react-patterns.md                      # 特定主题文件
└── security-checklist.md                  # 特定主题文件
```

---

## Agent Memory 与其他 Memory 系统

| 系统 | 谁写入 | 谁读取 | 作用域 |
|--------|-----------|-----------|-------|
| **CLAUDE.md** | 你（手动） | 主 Claude + 所有 agent | 项目 |
| **Auto-memory** | 主 Claude（自动） | 仅主 Claude | 每项目每用户 |
| **`/memory` 命令** | 你（通过编辑器） | 仅主 Claude | 每项目每用户 |
| **Agent memory** | Agent 自身 | 仅该特定 agent | 可配置（user/project/local） |

这些系统是**互补的** — agent 同时读取 CLAUDE.md（项目上下文）和自己的记忆（agent 特定知识）。

---

## 实用示例

```yaml
---
name: api-developer
description: 按照团队约定实现 API 端点
tools: Read, Write, Edit, Bash
model: sonnet
memory: project
skills:
  - api-conventions
  - error-handling-patterns
---

实现 API 端点。遵循你预加载 Skills 中的约定。
在工作过程中，将架构决策和模式保存到你的记忆中。
```

这结合了 **Skills**（启动时的静态知识）和 **Memory**（随时间积累的动态知识）。

---

## 提示

- **提示使用记忆** — 包含明确指令：`"开始前，审查你的记忆。完成后，用你学到的东西更新你的记忆。"`
- **调用 agent 时请求记忆检查**：`"审查这个 PR，并检查你的记忆中之前见过的模式。"`
- **选择正确的作用域** — `user` 用于跨项目，`project` 用于团队共享，`local` 用于个人

---

## 来源

- [创建自定义 subagents — Claude Code 文档](https://code.claude.com/docs/en/sub-agents)
- [管理 Claude 的记忆 — Claude Code 文档](https://code.claude.com/docs/en/memory)
- [Claude Code v2.1.33 发布说明](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
