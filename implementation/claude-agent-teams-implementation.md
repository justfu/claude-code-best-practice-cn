# Agent Teams 实现示例

![Last Updated](https://img.shields.io/badge/Last_Updated-Mar_12%2C_2026-white?style=flat&labelColor=555)

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

<a href="#time-orchestration"><img src="../!/tags/implemented-hd.svg" alt="已实现"></a>

<p align="center">
  <img src="assets/impl-agent-teams.png" alt="Agent Teams 运行中 — 使用 tmux 的分屏模式" width="100%">
</p>

Agent Teams 会生成**多个独立的 Claude Code 会话**，通过共享任务列表进行协调。与 subagent（一个会话内的隔离上下文 fork）不同，每个 teammate 都有自己完整的上下文窗口，自动加载 CLAUDE.md、MCP 服务器和 Skills。

---

## ![使用方法](../!/tags/how-to-use.svg)

时间编排工作流完全由一个 Agent 团队构建。要运行成品：

```bash
cd agent-teams
claude
/time-orchestrator
```

这会调用 **Command → Agent → Skill** 流水线：agent 获取迪拜的当前时间，skill 渲染 SVG 时间卡片到 `agent-teams/output/dubai-time.svg`。

---

## ![实现方法](../!/tags/how-to-implement.svg)

你可以使用 Agent Teams 复刻天气编排工作流 — 在这个示例中，时间编排工作流完全由一个 Agent 团队构建。

### 1. 安装 [iTerm2](https://iterm2.com/) 和 tmux

```bash
brew install --cask iterm2
brew install tmux
```

### 2. 启动 iTerm2 → tmux → Claude

```bash
tmux new -s dev
CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1 claude
```

### 3. 用团队结构提示

<a id="time-orchestration"></a>

将以下提示粘贴到 Claude 中，使用 Agent Teams 启动一个完整的时间编排工作流：

主提示：**[agent-teams-prompt.md](../agent-teams/agent-teams-prompt.md)**

### 团队协调流程

```
┌──────────────────────────────────────────────────────────────┐
│                         LEAD (你)                            │
│       "创建一个 Agent 团队来构建时间编排"                       │
└──────────────────────────┬───────────────────────────────────┘
                           │ 生成团队（全部并行）
              ┌────────────┼────────────┐
              ▼            ▼            ▼
   ┌────────────────┐ ┌──────────┐ ┌──────────────┐
   │ Command        │ │ Agent    │ │ Skill        │
   │ 架构师         │ │ 工程师   │ │ 设计师       │
   │                │ │          │ │              │
   │ agent-teams/   │ │ agent-   │ │ agent-teams/ │
   │ .claude/       │ │ teams/   │ │ .claude/     │
   │ commands/      │ │ .claude/ │ │ skills/      │
   │ time-          │ │ agents/  │ │ time-svg-    │
   │ orchestrator.md│ │ time-    │ │ creator/     │
   │                │ │ agent.md │ │              │
   └───────┬────────┘ └────┬─────┘ └──────┬───────┘
           │               │              │
           ▼               ▼              ▼
   ┌──────────────────────────────────────────────────┐
   │            共享任务列表                            │
   │  ☐ 约定数据契约: {time, tz, formatted}           │
   │  ☐ Command 使用 Agent 工具（不是 bash）           │
   │  ☐ Agent 预加载 time-fetcher skill               │
   │  ☐ Skill 从上下文读取时间（不重新获取）           │
   │  ☐ 所有文件放在 agent-teams/.claude/ 内           │
   └──────────────────────────────────────────────────┘
                       │
                       ▼
          ┌──────────────────────────────┐
          │  cd agent-teams && claude    │
          │    /time-orchestrator        │
          │   Command → Agent → Skill    │
          └──────────────────────────────┘
```

