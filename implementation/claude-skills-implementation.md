# Skills 实现示例

![Last Updated](https://img.shields.io/badge/Last_Updated-Mar_02%2C_2026-white?style=flat&labelColor=555)

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

<a href="#weather-svg-creator"><img src="../!/tags/implemented-hd.svg" alt="已实现"></a>

本仓库中实现了两个 Skill，作为 **Command → Agent → Skill** 架构模式的一部分，展示了两种不同的 Skill 调用模式：**agent skill**（预加载）和 **skill**（直接调用）。

---

## Weather SVG Creator（Skill）

**文件**: [`.claude/skills/weather-svg-creator/SKILL.md`](../.claude/skills/weather-svg-creator/SKILL.md)

```yaml
---
name: weather-svg-creator
description: 创建显示迪拜当前温度的 SVG 天气卡片。
  将 SVG 写入 orchestration-workflow/weather.svg 并更新
  orchestration-workflow/output.md。
---

# Weather SVG Creator Skill

此 skill 创建可视化 SVG 天气卡片并写入输出文件。

## 任务
创建一个 SVG 天气卡片，显示阿联酋迪拜的温度，
并连同摘要一起写入输出文件。

## 指令
你将从调用上下文中接收温度值和单位（摄氏或华氏）。

### 1. 创建 SVG 天气卡片
生成一个简洁的 SVG 天气卡片...

### 2. 写入 SVG 文件
将 SVG 内容写入 `orchestration-workflow/weather.svg`。

### 3. 写入输出摘要
写入 `orchestration-workflow/output.md`...

...
```

这是一个 **Skill** — 由 command 通过 Skill 工具直接调用。它从对话上下文中接收温度数据，创建 SVG 天气卡片和输出摘要。

---

## Weather Fetcher（Agent Skill）

**文件**: [`.claude/skills/weather-fetcher/SKILL.md`](../.claude/skills/weather-fetcher/SKILL.md)

```yaml
---
name: weather-fetcher
description: 从 Open-Meteo API 获取阿联酋迪拜当前天气温度数据的指令
user-invocable: false
---

# Weather Fetcher Skill

此 skill 提供获取当前天气数据的指令。

## 任务
获取阿联酋迪拜的当前温度，使用请求的单位（摄氏或华氏）。

## 指令
1. 获取天气数据：使用 WebFetch 工具获取当前天气数据
   - 摄氏 URL: https://api.open-meteo.com/v1/forecast?latitude=25.2048&longitude=55.2708&current=temperature_2m&temperature_unit=celsius
   - 华氏 URL: https://api.open-meteo.com/v1/forecast?latitude=25.2048&longitude=55.2708&current=temperature_2m&temperature_unit=fahrenheit
2. 提取温度：从 JSON 响应中提取 `current.temperature_2m`
3. 返回结果：清楚地返回温度值和单位。

...
```

这是一个 **Agent Skill** — 通过 `skills:` frontmatter 字段在启动时预加载到 `weather-agent` 中。它不直接调用；而是作为注入到 agent 上下文中的领域知识。注意 `user-invocable: false` 隐藏了它，不会出现在 `/` 命令菜单中。

---

## 两种 Skill 模式

| 模式 | 调用方式 | 示例 | 关键区别 |
|---------|-----------|---------|----------------|
| **Skill** | `Skill(skill: "name")` | `weather-svg-creator` | 通过 Skill 工具直接调用 |
| **Agent Skill** | 通过 `skills:` 字段预加载 | `weather-fetcher` | 启动时注入到 agent 上下文中 |

---

## ![使用方法](../!/tags/how-to-use.svg)

**Skill** — 通过 slash 命令直接调用：
```bash
$ claude
> /weather-svg-creator
```

---

## ![实现方法](../!/tags/how-to-implement.svg)

让 Claude 为你创建 — 它会在 `.claude/skills/my-skill/SKILL.md` 中生成带有 YAML frontmatter 和正文的 markdown 文件

# My Skill

描述此 skill 做什么的指令。
```
