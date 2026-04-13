# Sub-agents 实现示例

![Last Updated](https://img.shields.io/badge/Last_Updated-Mar_02%2C_2026_07%3A59_PM_PKT-white?style=flat&labelColor=555)

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

<a href="#weather-agent"><img src="../!/tags/implemented-hd.svg" alt="已实现"></a>

Weather agent 在本仓库中作为 **Command → Agent → Skill** 架构模式的示例实现，展示了两种不同的 Skill 模式。

---

## Weather Agent

**文件**: [`.claude/agents/weather-agent.md`](../.claude/agents/weather-agent.md)

```yaml
---
name: weather-agent
description: 当需要获取阿联酋迪拜的天气数据时，PROACTIVELY（主动）使用此 agent。
  该 agent 使用其预加载的 weather-fetcher skill 从 Open-Meteo 获取实时温度。
tools: WebFetch, Read, Write, Edit
model: sonnet
color: green
maxTurns: 5
permissionMode: acceptEdits
memory: project
skills:
  - weather-fetcher
---

# Weather Agent

你是一个专门的天气 agent，负责获取阿联酋迪拜的天气数据。

## 你的任务

按照预加载 skill 的指令执行天气工作流：

1. **获取**：按照 `weather-fetcher` skill 的指令获取当前温度
2. **报告**：将温度值和单位返回给调用者
3. **记忆**：更新你的 agent 记忆，记录读取详情以进行历史跟踪

...
```

该 agent 有一个预加载的 skill（`weather-fetcher`），提供了从 Open-Meteo 获取数据的指令。它将温度值和单位返回给调用它的 command。

---

## ![使用方法](../!/tags/how-to-use.svg)

```bash
$ claude
> 迪拜的天气怎么样？
```

---

## ![实现方法](../!/tags/how-to-implement.svg)

你可以使用 `/agents` 命令创建 agent，
```bash
$ claude
> /agents
```

或者让 Claude 为你创建 — 它会在 `.claude/agents/<name>.md` 中生成带有 YAML frontmatter 和正文的 markdown 文件

---

<a href="https://github.com/shanraisshan/claude-code-best-practice#orchestration-workflow"><img src="../!/tags/orchestration-workflow-hd.svg" alt="编排工作流"></a>

Weather agent 是 Command → Agent → Skill 编排模式中的 **Agent**。它从 `/weather-orchestrator` 命令接收工作流，并使用其预加载的 skill（`weather-fetcher`）获取温度。然后命令调用独立的 `weather-svg-creator` skill 创建可视化输出。

<p align="center">
  <img src="../orchestration-workflow/orchestration-workflow.svg" alt="Command Skill Agent 架构流程" width="100%">
</p>

| 组件 | 角色 | 本仓库 |
|-----------|------|-----------|
| **Command** | 入口点，用户交互 | [`/weather-orchestrator`](../.claude/commands/weather-orchestrator.md) |
| **Agent** | 使用预加载 skill 获取数据（agent skill） | [`weather-agent`](../.claude/agents/weather-agent.md) 搭配 [`weather-fetcher`](../.claude/skills/weather-fetcher/SKILL.md) |
| **Skill** | 独立创建输出（skill） | [`weather-svg-creator`](../.claude/skills/weather-svg-creator/SKILL.md) |
