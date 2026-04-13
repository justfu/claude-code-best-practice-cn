# Claude Code：用量、速率限制与额外用量

了解 Claude Code 的用量限制如何运作，以及在达到限制时如何继续工作。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 概述

Claude Code 的订阅计划（Pro、Max 5x、Max 20x）有使用量限制，按滚动窗口重置。三个内置 slash 命令帮助你监控和管理用量：

| 命令 | 描述 | 适用对象 |
|---------|-------------|--------------|
| `/usage` | 检查计划限制和速率限制状态 | Pro、Max 5x、Max 20x |
| `/extra-usage` | 在达到限制时配置按量付费溢出 | Pro、Max 5x、Max 20x |
| `/cost` | 显示当前会话的 token 使用量和花费 | API Key 用户 |

---

## `/usage` — 检查你的限制

显示你当前计划的使用量限制和速率限制状态。用于检查在达到限制前还剩多少容量。

---

## `/extra-usage` — 超过限制后继续工作

`/extra-usage` 命令配置**按量付费溢出计费**，使 Claude Code 在达到计划限制后继续无缝工作，而不是阻止你。

### 工作原理

1. 你达到了计划的速率限制（限制每 5 小时重置一次）
2. 如果额外用量已启用且有可用余额，Claude Code 将不中断地继续
3. 溢出 token 按**标准 API 费率**计费，与你的订阅费分开

### 设置方法

CLI 中的 `/extra-usage` 命令会引导你完成配置。你也可以在 claude.ai 的 **设置 > 用量** 页面进行配置：

1. 启用额外用量
2. 添加支付方式
3. 设置**每月消费上限**（或选择无限制）
4. 可选添加**预付资金**，余额低于阈值时自动充值

### 关键详情

| 详情 | 值 |
|--------|-------|
| 每日消费上限 | $2,000/天 |
| 计费 | 与订阅分开，按标准 API 费率 |
| 限制重置窗口 | 每 5 小时 |

### 已知问题

截至 2026 年 2 月，`/extra-usage` CLI 命令是[未公开文档的](https://github.com/anthropics/claude-code/issues/12396)，可能会打开一个登录窗口而没有清晰的配置选项。目前通过 **claude.ai Web 界面**配置是更可靠的方式。

---

## `/cost` — 会话花费（API 用户）

对于使用 API Key 认证的用户（非订阅计划），`/cost` 显示：

- 当前会话的总费用
- API 持续时间和实际时间
- Token 使用量明细
- 代码更改记录

此命令不适用于 Pro/Max 订阅用户。

---

## 快速模式与额外用量

快速模式（`/fast`）使用 Claude Opus 4.6 配合更快的输出。它与额外用量有特殊的计费关系：

- 快速模式使用量**从一开始就始终计费到额外用量**
- 即使你的订阅计划还有剩余用量，这也适用
- 快速模式不消耗计划中包含的速率限制额度

这意味着你需要启用额外用量并充值才能使用 `/fast`。

---

## CLI 启动标志

两个与用量预算相关的启动标志（仅限 API Key 用户，print 模式）：

| 标志 | 描述 |
|------|-------------|
| `--max-budget-usd <AMOUNT>` | API 调用的最大美元金额上限 |
| `--max-turns <NUMBER>` | 限制 agentic 轮次数 |

完整列表参见 [CLI 启动标志参考](../best-practice/claude-cli-startup-flags.md)。

---

## 来源

- [付费 Claude 计划的额外用量 — Claude 帮助中心](https://support.claude.com/en/articles/12429409-extra-usage-for-paid-claude-plans)
- [使用 Pro 或 Max 计划使用 Claude Code — Claude 帮助中心](https://support.claude.com/en/articles/11145838-using-claude-code-with-your-pro-or-max-plan)
- [/extra-usage slash 命令未公开文档 — GitHub Issue #12396](https://github.com/anthropics/claude-code/issues/12396)
- [Claude Code CLI 参考](https://code.claude.com/docs/en/cli-reference)
