# Claude Code：全局 vs 项目级功能

全面比较哪些 Claude Code 功能仅限全局（`~/.claude/`），哪些同时有全局和项目级（`.claude/`）对应物。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

## 目录

1. [概述](#概述)
2. [仅限全局的功能](#仅限全局的功能)
3. [双作用域功能](#双作用域功能)
4. [设置优先级](#设置优先级)
5. [目录结构对比](#目录结构对比)
6. [任务系统](#任务系统)
7. [Agent Teams](#agent-teams)
8. [设计原则](#设计原则)
9. [来源](#来源)

---

## 概述

Claude Code 使用**作用域层级**，某些功能同时存在于全局（`~/.claude/`）和项目级（`.claude/`），而其他功能仅限全局。设计原则：属于*个人状态*或*跨项目协调*的全局存在；属于*团队可共享的项目配置*的可以在项目级存在。

- `~/.claude/` 是你的**用户级主目录**（全局，所有项目）
- 仓库内的 `.claude/` 是你的**项目级主目录**（限定于该项目）

---

## 仅限全局的功能

这些**仅**存在于 `~/.claude/` 下，不能限定到项目：

| 功能 | 位置 | 用途 |
|---------|----------|---------|
| **Tasks** | `~/.claude/tasks/` | 跨会话和 agent 的持久化任务列表 |
| **Agent Teams** | `~/.claude/teams/` | 多 Agent 协调配置（实验性，2026 年 2 月） |
| **Auto Memory** | `~/.claude/projects/<hash>/memory/` | Claude 自写的每个项目的学习（个人，永不共享） |
| **凭证与 OAuth** | 系统钥匙串 + `~/.claude.json` | API Key、OAuth 令牌（永远不在项目文件中） |
| **快捷键** | `~/.claude/keybindings.json` | 自定义键盘快捷键 |
| **MCP 用户服务器** | `~/.claude.json`（`mcpServers` 键） | 所有项目中的个人 MCP 服务器 |
| **偏好/缓存** | `~/.claude.json` | 主题、模型、输出样式、会话状态 |

---

## 双作用域功能

这些同时存在于两个层级，**项目级优先**于全局：

| 功能 | 全局（`~/.claude/`） | 项目级（`.claude/`） | 优先级 |
|---------|----------------------|---------------------|------------|
| **CLAUDE.md** | `~/.claude/CLAUDE.md` | `./CLAUDE.md` 或 `.claude/CLAUDE.md` | 项目覆盖全局 |
| **Settings** | `~/.claude/settings.json` | `.claude/settings.json` + `.claude/settings.local.json` | 项目 > 全局 |
| **Rules** | `~/.claude/rules/*.md` | `.claude/rules/*.md` | 项目覆盖 |
| **Agents/Subagents** | `~/.claude/agents/*.md` | `.claude/agents/*.md` | 项目覆盖 |
| **Commands** | `~/.claude/commands/*.md` | `.claude/commands/*.md` | 两者都可用 |
| **Skills** | `~/.claude/skills/` | `.claude/skills/` | 两者都可用 |
| **Hooks** | `~/.claude/hooks/` | `.claude/hooks/` | 两者都执行 |
| **MCP 服务器** | `~/.claude.json`（用户作用域） | `.mcp.json`（项目作用域） | 三个作用域：本地 > 项目 > 用户 |

---

## 设置优先级

用户可写的设置按以下覆盖顺序应用（从高到低）：

| 优先级 | 位置 | 作用域 | 版本控制 | 用途 |
|----------|----------|-------|-----------------|---------|
| 1 | 命令行标志 | 会话 | N/A | 单会话覆盖 |
| 2 | `.claude/settings.local.json` | 项目 | 否（git-ignored） | 个人的项目特定设置 |
| 3 | `.claude/settings.json` | 项目 | 是（已提交） | 团队共享设置 |
| 4 | `~/.claude/settings.local.json` | 用户 | N/A | 个人全局覆盖 |
| 5 | `~/.claude/settings.json` | 用户 | N/A | 全局个人设置 |

策略层：`managed-settings.json` 是组织强制执行的，不能被本地文件覆盖。

**重要**：`deny` 规则具有最高安全优先级，不能被低优先级的 allow/ask 规则覆盖。

---

## 目录结构对比

### 全局作用域（`~/.claude/`）

```
~/.claude/
├── settings.json              # 用户级设置（所有项目）
├── settings.local.json        # 个人覆盖
├── CLAUDE.md                  # 用户记忆（所有项目）
├── agents/                    # 用户 subagents（所有项目可用）
│   └── *.md
├── rules/                     # 用户级模块化规则
│   └── *.md
├── commands/                  # 用户级命令
│   └── *.md
├── skills/                    # 用户级 Skills
│   └── */SKILL.md
├── tasks/                     # 仅限全局: 任务列表
│   └── {task-list-id}/
├── teams/                     # 仅限全局: Agent 团队配置
│   └── {team-name}/
│       └── config.json
├── projects/                  # 仅限全局: 每项目自动记忆
│   └── {project-hash}/
│       └── memory/
│           ├── MEMORY.md
│           └── *.md
├── keybindings.json           # 仅限全局: 键盘快捷键
└── hooks/                     # 用户级 hooks
    ├── scripts/
    └── config/

~/.claude.json                 # 仅限全局: MCP 服务器、OAuth、偏好、缓存
```

### 项目作用域（`.claude/`）

```
.claude/
├── settings.json              # 团队共享设置
├── settings.local.json        # 个人项目覆盖（git-ignored）
├── CLAUDE.md                  # 项目记忆（./CLAUDE.md 的替代）
├── agents/                    # 项目 subagents
│   └── *.md
├── rules/                     # 项目级模块化规则
│   └── *.md
├── commands/                  # 自定义 slash 命令
│   └── *.md
├── skills/                    # 自定义 Skills
│   └── {skill-name}/
│       ├── SKILL.md
│       └── supporting-files/
├── hooks/                     # 项目级 hooks
│   ├── scripts/
│   └── config/
└── plugins/                   # 已安装的插件

.mcp.json                      # 项目级 MCP 服务器（仓库根目录）
```

---

## 任务系统

在 **Claude Code v2.1.16**（2026 年 1 月 22 日）中引入，取代已弃用的 TodoWrite 系统。

### 存储

任务存储在本地文件系统的 `~/.claude/tasks/`（不在云数据库中）。这使得任务状态可审计、可版本控制、可从崩溃中恢复。

### 工具

| 工具 | 用途 |
|------|---------|
| **TaskCreate** | 创建新任务，包含 `subject`、`description` 和 `activeForm` |
| **TaskGet** | 通过 ID 检索特定任务的完整详情 |
| **TaskUpdate** | 更改状态、设置负责人、添加依赖或删除 |
| **TaskList** | 列出所有任务及其当前状态 |

### 任务生命周期

```
pending  →  in_progress  →  completed
```

### 依赖管理

任务可以通过 `addBlockedBy`/`addBlocks` 阻止其他任务，创建依赖图以防止过早执行。

### 多会话协作

```bash
CLAUDE_CODE_TASK_LIST_ID=my-project-tasks claude
```

所有共享相同 ID 的会话可以实时看到任务更新，实现并行工作流和会话恢复。

### 与旧 Todos 的主要区别

| 功能 | 旧 Todos | 新 Tasks |
|---------|-----------|-----------|
| 作用域 | 单会话 | 跨会话、跨 agent |
| 依赖 | 无 | 完整依赖图 |
| 存储 | 仅内存 | 文件系统（`~/.claude/tasks/`） |
| 持久化 | 会话结束时丢失 | 在重启和崩溃后存活 |
| 多会话 | 不可能 | 通过 `CLAUDE_CODE_TASK_LIST_ID` |

---

## Agent Teams

于 **2026 年 2 月 5 日** 宣布为实验性功能。Agent Teams 允许多个 Claude Code 会话在共享工作上协调。

### 启用

```json
// 在 ~/.claude/settings.json 中
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

### 配置

团队配置位于 `~/.claude/teams/{team-name}/`，支持模式：

| 模式 | 描述 | 要求 |
|------|-------------|--------------|
| **In-process**（默认） | 所有 teammates 在你的终端内运行 | 无 |
| **Split panes** | 每个 teammate 有自己的面板 | tmux 或 iTerm2（不支持 VS Code 终端） |

---

## 设计原则

仅限全局 vs 双作用域的划分遵循清晰的模式：

| 类别 | 作用域 | 理由 |
|----------|-------|-----------|
| **协调状态**（tasks、teams） | 仅限全局 | 需要在任何单一项目之外持久化 |
| **安全状态**（凭证、OAuth） | 仅限全局 | 防止意外提交到版本控制 |
| **个人学习**（auto-memory） | 仅限全局 | 用户特定，不可团队共享 |
| **输入偏好**（快捷键） | 仅限全局 | 用户肌肉记忆，非项目特定 |
| **配置**（settings、rules、agents） | 两个层级 | 团队需要共享项目特定行为 |
| **工作流定义**（commands、skills） | 两个层级 | 可以是个人或团队共享 |

Auto-memory（`~/.claude/projects/<hash>/memory/`）是一个值得注意的混合体：它是*关于*特定项目的，但*全局*存储，因为它代表个人学习而非团队可共享的配置。

---

## 来源

- [Claude Code Settings 文档](https://code.claude.com/docs/en/settings)
- [编排 Claude Code 会话团队](https://code.claude.com/docs/en/agent-teams)
- [Claude Code 中的 Tasks 是什么 - ClaudeLog](https://claudelog.com/faqs/what-are-tasks-in-claude-code/)
- [Claude Code 任务管理 - ClaudeFast](https://claudefa.st/blog/guide/development/task-management)
- [Claude Code Tasks 更新 - VentureBeat](https://venturebeat.com/orchestration/claude-codes-tasks-update-lets-agents-work-longer-and-coordinate-across)
- [Claude Code 全局设置在哪里 - ClaudeLog](https://claudelog.com/faqs/where-are-claude-code-global-settings/)
- [Claude Opus 4.6 Agent Teams - VentureBeat](https://venturebeat.com/technology/anthropics-claude-opus-4-6-brings-1m-token-context-and-agent-teams-to-take)
- [如何设置 Claude Code Agent Teams（完整指南）- r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1qz8tyy/how_to_set_up_claude_code_agent_teams_full/)
- [Anthropic 用 Tasks 替换了旧的 Todos - r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1qkjznp/anthropic_replaced_claude_codes_old_todos_with/)
