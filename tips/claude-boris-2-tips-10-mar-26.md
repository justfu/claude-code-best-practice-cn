# 代码审查与测试时计算 — Boris Cherny 的技巧

Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 3 月 10 日分享的见解摘要。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 1/ 引入 Code Review

Claude Code 新功能：**Code Review**。一个 Agent 团队对每个 PR 进行深度审查。

- 首先为 Anthropic 自家团队打造 — 今年每位工程师的代码产出增加了 **200%**，而审查是瓶颈
- Boris 使用了几周，发现它能捕捉到许多他原本不会注意到的真实 bug
- 当 PR 打开时，Claude 派遣一组 Agent 来寻找 bug

---

## 2/ 测试时计算与多上下文窗口

粗略地说，你向一个编码问题投入越多的 token，结果越好。Boris 将此称为**测试时计算 (test time compute)**。

- 使用**独立的上下文窗口**使结果更好 — 这正是 subagents 的工作原理，也是一个 agent 能制造 bug 而另一个（使用完全相同的模型）能发现它的原因
- 类似于工程团队：如果 Boris 制造了一个 bug，他的同事审查代码时可能比他自己更可靠地发现它
- 在极限情况下，agent 大概会写出完美的无 bug 代码 — 在此之前，**多个不相关的上下文窗口**通常是一个好方法

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 3 月 10 日](https://x.com/bcherny)
