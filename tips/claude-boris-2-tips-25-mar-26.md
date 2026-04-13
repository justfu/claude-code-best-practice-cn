# Squash 合并与 PR 大小分布 — Boris Cherny 的技巧

Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 3 月 25 日分享的见解摘要。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 1/ 一天 266 次提交 — 始终 Squash

Boris 分享了他的 GitHub 贡献图，显示 **3 月 24 日有 266 次贡献** — 来自 **141 个 PR，全部 squash 合并**，每个 PR 中位 **118 行**。

- Squash 合并将分支的所有提交合并为目标分支上的一个提交 — 保持历史干净和线性
- 每个 PR = 一个提交，方便回滚整个功能并简化 `git bisect`
- 在高速 AI 辅助工作流中（每天 141 个 PR），Squash 是务实的选择 — 分支中个别的"修复 lint"、"试试这个"提交都是噪音

---

## 2/ PR 大小分布 — 保持 PR 小而精

Boris 分享了这 141 个 PR 的大小分布，总计 **45,032 行更改**（增加 + 删除）：

| 指标 | 行数（增+删） | 含义 |
|--------|---------------:|---------|
| **p50** | **118** | PR 大小的中位数 — 一半的 PR 不超过 118 行 |
| p90 | 498 | 90% 的 PR 低于 500 行 |
| **p99** | **2,978** | 只有约 1 个 PR 超过 ~3K 行 |
| min | 2 | 最小的 PR — 一个快速的 2 行修复 |
| max | 10,459 | 最大的单个 PR — 可能是迁移或生成代码 |

- **118 行的中位数**意味着大多数 PR 都聚焦且可审查，即使每天 141 个 PR 也是如此
- 分布严重右偏 — 偶尔的大型 PR 不可避免（批量重命名、迁移），但常态是紧凑的
- 小 PR 减少合并冲突风险，更容易审查，与 Squash 合并完美配合实现干净回滚

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 3 月 25 日](https://x.com/bcherny)
