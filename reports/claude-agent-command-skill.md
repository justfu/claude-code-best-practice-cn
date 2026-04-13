# Agent vs Command vs Skill — 何时使用哪个

Claude Code 中三种扩展机制的对比：subagent、command 和 skill。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

![显示 time-skill、time-command 和 time-agent 的 Slash 菜单](assets/agent-command-skill-1.jpg)

---

## 一览

| | Agent | Command | Skill |
|---|---|---|---|
| **位置** | `.claude/agents/<name>.md` | `.claude/commands/<name>.md` | `.claude/skills/<name>/SKILL.md` |
| **上下文** | 独立的 subagent 进程 | 内联（主对话） | 内联（主对话） |
| **用户可调用** | 无 `/` 菜单 — 由 Claude 或通过 Agent 工具调用 | 是 — `/command-name` | 是 — `/skill-name`（除非 `user-invocable: false`） |
| **Claude 自动调用** | 是 — 通过 `description` 字段 | 否 | 是 — 通过 `description` 字段（除非 `disable-model-invocation: true`） |
| **接受参数** | 通过 `prompt` 参数 | `$ARGUMENTS`、`$0`、`$1` | `$ARGUMENTS`、`$0`、`$1` |
| **动态上下文注入** | 否 | 是 — `` !`command` `` | 是 — `` !`command` `` |
| **自有上下文窗口** | 是 — 隔离的 | 否 — 共享主上下文 | 否 — 共享主上下文（除非 `context: fork`） |
| **模型覆盖** | `model:` frontmatter | `model:` frontmatter | `model:` frontmatter |
| **工具限制** | `tools:` / `disallowedTools:` | `allowed-tools:` | `allowed-tools:` |
| **Hooks** | `hooks:` frontmatter | — | `hooks:` frontmatter |
| **Memory** | `memory:` frontmatter（user/project/local） | — | — |
| **可预加载 Skills** | 是 — `skills:` frontmatter | — | — |
| **MCP 服务器** | `mcpServers:` frontmatter | — | — |

---

## 何时使用各机制

### 使用 Agent 当：

- 任务是**自主多步骤的** — agent 需要探索、决策和行动，不需要持续指导
- 你需要**上下文隔离** — 工作不应污染主对话窗口
- Agent 需要**跨会话的持久化记忆**（例如学习模式的代码审查者）
- 你想通过 Skills **预加载领域知识**，而不弄乱主上下文
- 任务受益于**后台运行**或在 **git worktree** 中运行
- 你需要**工具限制**或**不同的权限模式**（如 `acceptEdits`、`plan`）

**示例**：`weather-agent` — 使用其预加载的 `weather-fetcher` Skill 自主获取天气数据，在受限工具的独立上下文中运行。

### 使用 Command 当：

- 你需要一个**用户发起的入口点** — 用户显式触发的工作流
- 工作流涉及**编排**其他 agents 或 skills
- 你想**保持上下文精简** — Command 内容在用户触发之前不会注入到会话上下文中

**示例**：`weather-orchestrator` — 用户触发它，询问 C/F 偏好，调用 agent，然后调用 SVG skill。

### 使用 Skill 当：

- 你希望 **Claude 根据用户意图自动调用** — Skill 描述被注入到会话上下文中进行语义匹配
- 任务是一个**可复用的程序**，可以从多个地方调用（commands、agents 或 Claude 自身）
- 你需要 **agent 预加载** — 在启动时将领域知识烘焙到特定 agent 中

**示例**：`weather-svg-creator` — Claude 在用户要求天气卡片时自动调用；也可从 commands 调用。

---

## Command → Agent → Skill 架构

本仓库演示了一个分层编排模式：

```
用户触发 /command
    ↓
Command 编排工作流
    ↓
Command 调用 Agent（独立上下文，自主）
    ↓
Agent 使用预加载的 Skill（领域知识）
    ↓
Command 调用 Skill（内联，用于输出生成）
```

**具体示例** — 天气系统：

```
/weather-orchestrator（command — 入口点，询问 C/F）
    ↓
weather-agent（agent — 自主获取温度）
    ├── weather-fetcher（agent skill — 预加载的 API 指令）
    ↓
weather-svg-creator（skill — 内联创建 SVG）
```

---

## Frontmatter 对比

### Agent Frontmatter

```yaml
---
name: my-agent
description: 当...时 PROACTIVELY 使用此 agent
tools: Read, Write, Edit, Bash
model: sonnet
maxTurns: 10
permissionMode: acceptEdits
memory: user
skills:
  - my-skill
---
```

### Command Frontmatter

```yaml
---
description: 做一些有用的事
argument-hint: [issue-number]
allowed-tools: Read, Edit, Bash(gh *)
model: sonnet
---
```

### Skill Frontmatter

```yaml
---
name: my-skill
description: 当用户要求...时执行某些操作
argument-hint: [file-path]
disable-model-invocation: false
user-invocable: true
allowed-tools: Read, Grep, Glob
model: sonnet
context: fork
agent: general-purpose
---
```

---

## 关键区别

### 自动调用

| 机制 | Claude 能自动调用吗？ | 如何阻止 |
|-----------|------------------------|----------------|
| Agent | 是 — 通过 `description`（使用 "PROACTIVELY" 鼓励） | 移除或弱化 description |
| Command | 否 — 始终由用户通过 `/` 发起 | N/A |
| Skill | 是 — 通过 `description` | 设置 `disable-model-invocation: true` |

### 在 `/` 菜单中的可见性

| 机制 | 出现在 `/` 菜单中？ | 如何隐藏 |
|-----------|---------------------|-------------|
| Agent | 否 | N/A |
| Command | 是 — 始终 | 无法隐藏 |
| Skill | 是 — 默认 | 设置 `user-invocable: false` |

### 上下文隔离

| 机制 | 在自己上下文中运行？ | 如何配置 |
|-----------|---------------------|-----------------|
| Agent | 始终 | 内置行为 |
| Command | 从不 | N/A |
| Skill | 可选 | 设置 `context: fork` |

---

## 实例："现在几点？"

本仓库为同一任务（显示巴基斯坦标准时间）定义了全部三种机制。当用户输入 **"现在几点？"** 而未显式调用任何 `/` 命令时：

| 机制 | 会触发吗？ | 为什么/为什么不 |
|-----------|--------------|---------------|
| `time-command` | 否 | Command **永远不会被自动调用**。用户需要显式输入 `/time-command` 才能运行。Command 没有自动发现路径 — 它们严格由用户发起。 |
| `time-agent` | **是**（可能） | Agent 的 `description` 写着*"使用此 agent 显示巴基斯坦标准时间的当前时间"*。Claude 将此与用户意图匹配，可能通过 Agent 工具生成它。但 Agent 在**独立上下文窗口**中运行，对这个简单任务来说太重了。 |
| `time-skill` | **是**（最可能） | Skill 的 `description` 写着*"显示巴基斯坦标准时间（PKT, UTC+5）的当前时间。当用户询问当前时间、巴基斯坦时间或 PKT 时使用。"* Claude 匹配并通过 Skill 工具调用。由于它**内联运行**且无上下文开销，是最高效的匹配。 |

### 解析顺序

当多个机制匹配同一意图时，Claude 偏好满足请求的**最轻量选项**：

```
1. Skill（内联，无上下文开销）     ← 首选
2. Agent（独立上下文，自主）      ← 当 Skill 不可用或任务复杂时使用
3. Command（从不 — 需要显式 /）   ← 仅当用户输入 /time-command 时
```

### 如果 Skill 设置了 `disable-model-invocation: true`？

那么 Claude **无法**自动调用该 Skill。Agent 成为唯一可自动调用的选项，Claude 会生成 `time-agent` — 代价是为一个单行 bash 命令使用了独立的上下文窗口。

### 如果 Skill 和 Agent 都禁用了自动调用？

那么**没有任何东西自动触发**。Claude 会回退到其自身的通用知识，很可能直接运行 `TZ='Asia/Karachi' date` — 不涉及任何扩展机制。用户需要显式输入 `/time-command` 或 `/time-skill` 来使用。

![当用户问"现在几点？"时 Claude 自动调用 time-skill](assets/agent-command-skill-2.png)

---

## 来源

- [Claude Code Skills — 文档](https://code.claude.com/docs/en/skills)
- [Claude Code Sub-agents — 文档](https://code.claude.com/docs/en/sub-agents)
- [Claude Code Slash Commands — 文档](https://code.claude.com/docs/en/slash-commands)
- [Skills 最佳实践](../best-practice/claude-skills.md)
- [Commands 最佳实践](../best-practice/claude-commands.md)
- [Sub-agents 最佳实践](../best-practice/claude-subagents.md)
