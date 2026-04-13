# Development Workflows Changelog

**状态说明：**

| 状态 | 含义 |
|------|------|
| `COMPLETE (原因)` | 操作已执行并成功解决 |
| `INVALID (原因)` | 发现不正确、不适用或为有意为之 |
| `ON HOLD (原因)` | 操作已推迟，等待外部依赖或用户决定 |

---

## [2026-03-19 05:25 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 仓库变更 | 将 humanlayer 从仅文章仓库更改为 humanlayer/humanlayer（★ 10k，6 个 agents，27 个 commands） | COMPLETE (用户请求，仓库有实际实现) |
| 2 | HIGH | 计数更新 | 添加 context-hub 的计数：0 agents · 7 skills · 7 commands | COMPLETE (之前显示 —) |
| 3 | HIGH | 计数更新 | 添加 agent-os 的计数：0 agents · 0 skills · 5 commands | COMPLETE (之前显示 —) |
| 4 | MED | 计数更新 | 将 spec-kit commands 从 14 更新到 9+（9 个核心，扩展为社区贡献） | COMPLETE (agents 确认了 9 个核心命令模板) |
| 5 | MED | 计数更新 | 将 OpenSpec commands 从 10+ 更新到 11（确认确切数量） | COMPLETE (agents 确认了 11 个命令) |
| 6 | MED | 计数更新 | 将 gstack 从"21 skills · 21 commands"更新为"21 skills/commands"（skills 作为 command 表面） | COMPLETE (没有单独的 commands/ 目录，skills 就是 commands) |
| 7 | MED | 描述 | 添加 context-hub、agent-os、humanlayer 的独特性描述 | COMPLETE (之前显示通用描述) |
| 8 | LOW | 排序顺序 | 将 humanlayer 从 ★ 1.6k 位置上移到 ★ 10k 位置（context-hub 之后） | COMPLETE (仓库变更导致更高的 star 数) |
| 9 | LOW | 报告更新 | 用所有 9 个 workflows 更新跨 workflow 分析报告"Workflows at a Glance"表 | COMPLETE (之前仅 6 个，现在包含所有 9 个按 stars 排序) |

---

## [2026-03-19 05:29 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 计数更新 | 将 obra/superpowers agents 从 7 更新到 5（v5.0.4 将审查循环合并为全计划评估，移除了 2 个隐式 agents） | COMPLETE (已更新 README 表和报告) |
| 2 | HIGH | 计数更新 | 将 obra/superpowers skills 从 44+ 更新到 14 核心（社区仓库 obra/superpowers-skills 于 2025 年 10 月归档） | COMPLETE (已更新 README 表和报告) |
| 3 | HIGH | 计数更新 | 更新 spec-kit：skills 10→0（v0.3.0 替换为 preset 系统），commands 保持在 9+ 并在报告中注明 22 个扩展 | COMPLETE (已更新 README 表和报告) |
| 4 | HIGH | 计数更新 | 将 context-hub 计数从 7 skills · 7 commands 更新为：0 agents · 1 skill · 0 commands | COMPLETE (更正了上次运行的不准确计数；仅有 1 个 SKILL.md 在 cli/skills/get-api-docs/) |
| 5 | MED | Star 更新 | 将 spec-kit stars 从 78k 更新到 79k（显示 78.5k） | COMPLETE (已更新 README 表和报告) |
| 6 | MED | 计数更新 | agent-os 计数已在上次运行中出现在 README 中：0 agents · 0 skills · 5 commands | COMPLETE (验证了计数匹配) |
| 7 | MED | Star 更新 | 将 agent-os stars 从 4.1k 更新到 4k（实际 4,100） | COMPLETE (已更新 README 表和报告) |
| 8 | MED | 报告更新 | 用当前计数更新跨 workflow 分析报告：obra、spec-kit、context-hub、agent-os | COMPLETE (已更新 Workflows at a Glance 表) |
| 9 | LOW | 计数验证 | OpenSpec commands：表显示 11，研究发现 9-11 取决于计数方式 | INVALID (11 在发现范围内，保留当前值) |
| 10 | LOW | 独特性 | 更新 spec-kit 独特性以提及可插拔扩展/preset 生态系统（v0.3.0） | COMPLETE (将"pre-implementation gates"替换为"pluggable extension/preset ecosystem") |

---

## [2026-03-20 08:37 AM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 98k 更新到 100k（实际 99,603 — 接近 100k 里程碑） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 Everything Claude Code ★ 从 87k 更新到 89k（实际 88,580） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 Get Shit Done ★ 从 35k 更新到 36k（实际 36,307） | COMPLETE (已更新 README 表) |
| 4 | HIGH | 计数更新 | 将 Get Shit Done commands 从 46 更新到 50（v1.26.0 添加了 /gsd:ship、/gsd:next、/gsd:do、/gsd:ui-phase） | COMPLETE (已更新 README 表) |
| 5 | MED | Star 更新 | 将 gstack ★ 从 26k 更新到 29k（实际 28,889 — v0.9.0 多 AI 扩展） | COMPLETE (已更新 README 表) |
| 6 | MED | 计数更新 | 将 BMAD-METHOD skills 从 43 更新到 42（v6.2.0 重新计数：30 bmm-skills + 12 core-skills） | COMPLETE (已更新 README 表) |
| 7 | LOW | 排序顺序 | 按 Plan 类型组重新排列表格（commands → agents → skills，组内按 stars 降序） | COMPLETE (commands: Spec Kit, OpenSpec, HumanLayer; agents: ECC, GSD; skills: Superpowers, BMAD, gstack) |

---

## [2026-03-21 09:20 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 100k 更新到 103k（实际 102,767） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 Everything Claude Code ★ 从 89k 更新到 93k（实际 93,145） | COMPLETE (已更新 README 表) |
| 3 | HIGH | 计数更新 | 更新 ECC agents 25→28，commands 57→59，skills 108+→116（v1.9.0：选择性安装、ECC Tools Pro、12 种语言生态系统） | COMPLETE (已更新 README 表) |
| 4 | HIGH | Star 更新 | 将 Get Shit Done ★ 从 36k 更新到 38k（实际 37,748） | COMPLETE (已更新 README 表) |
| 5 | HIGH | 计数更新 | 更新 GSD agents 16→18，commands 50→52（v1.27.0：advisor mode、多 repo 工作区、/gsd:fast、/gsd:review） | COMPLETE (已更新 README 表) |
| 6 | HIGH | Star 更新 | 将 gstack ★ 从 29k 更新到 34k（实际 34,456 — v0.9.4 Codex 审查、Windows 11 支持） | COMPLETE (已更新 README 表) |
| 7 | HIGH | 架构变更 | 将 BMAD agents 从 9 更新到 0（v6.x 纯 skills 重写 — agent 人设现在作为 skills 在 bmm-skills/ 中实现） | COMPLETE (已更新 README 表) |
| 8 | MED | Star 更新 | 将 BMAD ★ 从 41k 更新到 42k（实际 41,629） | COMPLETE (已更新 README 表) |
| 9 | MED | Star 更新 | 将 OpenSpec ★ 从 32k 更新到 33k（实际 32,862） | COMPLETE (已更新 README 表) |
| 10 | MED | 排序顺序 | 将 gstack（34k）交换到 OpenSpec（33k）上方 — stars 降序排列 | COMPLETE (已更新 README 表) |

---

## [2026-03-23 09:53 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 103k 更新到 107k（实际 107,308） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 93k 更新到 101k（实际 101,098 — 跨越 100k 里程碑！） | COMPLETE (已更新 README 表) |
| 3 | HIGH | 计数更新 | 更新 ECC commands 59→60，skills 116→125（v1.9.0 持续：新增 skills pytorch-patterns、documentation-lookup、claude-devfleet、prompt-optimizer） | COMPLETE (已更新 README 表) |
| 4 | HIGH | Star 更新 | 将 gstack ★ 从 34k 更新到 41k（实际 41,224 — v0.9.x 多 AI 扩展、CSO 安全审计） | COMPLETE (已更新 README 表) |
| 5 | HIGH | 计数更新 | 将 gstack skills 21→27（6 个新增：gstack-autoplan、gstack-benchmark、gstack-cso、gstack-design-consultation、gstack-office-hours、gstack-freeze/unfreeze） | COMPLETE (已更新 README 表) |
| 6 | HIGH | 排序顺序 | 将 gstack（41k）上移到 GSD（40k）上方 — stars 降序排列 | COMPLETE (已更新 README 表) |
| 7 | HIGH | Star 更新 | 将 GSD ★ 从 38k 更新到 40k（实际 39,588） | COMPLETE (已更新 README 表) |
| 8 | HIGH | 计数更新 | 更新 GSD commands 52→57（v1.28.0：/gsd:forensics、/gsd:milestone-summary、/gsd:plant-seed、/gsd:profile-user、/gsd:workstreams） | COMPLETE (已更新 README 表) |
| 9 | MED | Star 更新 | 将 Spec Kit ★ 从 79k 更新到 81k（实际 81,349 — v0.4.0 嵌入式核心包、24 平台支持） | COMPLETE (已更新 README 表) |
| 10 | MED | Plan 更新 | 将 gstack Plan 从 plan-eng-review 更新为 autoplan（更高级别的编排器，按顺序读取 CEO、design、eng review） | COMPLETE (已更新 README 表) |
| 11 | LOW | 计数更新 | 将 OpenSpec commands 11→10（重新计数：/opsx:propose、apply、archive、new、continue、ff、verify、sync、bulk-archive、onboard） | COMPLETE (已更新 README 表) |
| 12 | LOW | 计数更正 | 更正 OpenSpec skills 11→0（不存在 skills/ 或 .claude/skills/ 目录 — OpenSpec 是 CLI 工具，非基于 skills） | COMPLETE (已更新 README 表) |

---

## [2026-03-24 08:12 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 107k 更新到 110k（实际 109,846） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 101k 更新到 104k（实际 103,960） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 gstack ★ 从 41k 更新到 44k（实际 44,300 — v0.11.x 三重语音多 model 审查） | COMPLETE (已更新 README 表) |
| 4 | HIGH | 排序顺序 | 将 gstack（44k）上移到 BMAD（42k）上方 — stars 降序排列 | COMPLETE (已更新 README 表) |
| 5 | HIGH | 计数更新 | 将 BMAD skills 从 42 更新到 44（重新计数：32 bmm-skills + 12 core-skills，包括 3 个嵌套的研究子 skills） | COMPLETE (已更新 README 表) |
| 6 | HIGH | 计数更新 | 将 gstack skills 从 27 更新到 28（README 说明 28；已确认 27 个） | COMPLETE (已更新 README 表) |
| 7 | MED | Star 更新 | 将 Spec Kit ★ 从 81k 更新到 82k（实际 81,780） | COMPLETE (已更新 README 表) |
| 8 | MED | Star 更新 | 将 GSD ★ 从 40k 更新到 41k（实际 40,500） | COMPLETE (已更新 README 表) |
| 9 | MED | Star 更新 | 将 OpenSpec ★ 从 33k 更新到 34k（实际 33,800） | COMPLETE (已更新 README 表) |

---

## [2026-03-25 08:12 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 110k 更新到 112k（实际 112,163） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 104k 更新到 107k（实际 106,913） | COMPLETE (已更新 README 表) |
| 3 | HIGH | 计数更新 | 将 ECC commands 从 60 更新到 63（3 个新增在 .claude/commands/ 中：add-language-rules、database-migration、feature-development） | COMPLETE (已更新 README 表) |
| 4 | HIGH | Star 更新 | 将 gstack ★ 从 44k 更新到 47k（实际 46,703 — 基础设施加固、测试覆盖率门控） | COMPLETE (已更新 README 表) |
| 5 | MED | 计数更新 | 将 BMAD skills 从 44 更新到 42（重新计数：30 bmm-skills + 12 core-skills；v6.2.1 合并了 2 个子 skills） | COMPLETE (已更新 README 表) |
| 6 | LOW | 计数更新 | 将 gstack skills 从 28 更新到 27（确认了 27 个根级目录；第 28 个可能是根 SKILL.md 模板） | COMPLETE (已更新 README 表) |

---

## [2026-03-26 01:05 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 112k 更新到 114k（实际 114,107） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 107k 更新到 109k（实际 108,839） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 gstack ★ 从 47k 更新到 48k（实际 48,303） | COMPLETE (已更新 README 表) |
| 4 | HIGH | Star 更新 | 将 GSD ★ 从 41k 更新到 42k（实际 42,092） | COMPLETE (已更新 README 表) |
| 5 | MED | 计数更新 | 将 OpenSpec commands 从 10 更新到 11（v1.2.0 添加了 /opsx:explore） | COMPLETE (已更新 README 表) |

---

## [2026-03-27 06:32 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 114k 更新到 118k（实际 117,568） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 109k 更新到 111k（实际 111,487） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 gstack ★ 从 48k 更新到 52k（实际 51,544 — v0.12.x skill 命名空间、Codex 回退、worktree 并行化） | COMPLETE (已更新 README 表) |
| 4 | HIGH | 计数更新 | 将 gstack skills 从 27 更新到 31（4 个新增：canary、codex、connect-chrome、land-and-deploy 等） | COMPLETE (已更新 README 表) |
| 5 | HIGH | Star 更新 | 将 GSD ★ 从 42k 更新到 43k（实际 43,136） | COMPLETE (已更新 README 表) |
| 6 | HIGH | 排序顺序 | 将 GSD（43,136）交换到 BMAD（42,529）上方 — 两者都四舍五入为 43k 但 GSD 有更多 stars | COMPLETE (已更新 README 表) |
| 7 | MED | Star 更新 | 将 Spec Kit ★ 从 82k 更新到 83k（实际 82,878） | COMPLETE (已更新 README 表) |
| 8 | MED | Star 更新 | 将 BMAD ★ 从 42k 更新到 43k（实际 42,529） | COMPLETE (已更新 README 表) |
| 9 | MED | Star 更新 | 将 OpenSpec ★ 从 34k 更新到 35k（实际 34,821） | COMPLETE (已更新 README 表) |
| 10 | MED | 计数更新 | 将 Compound Engineering agents 从 43 更新到 47（4 个新增 review/workflow agents） | COMPLETE (已更新 README 表) |
| 11 | MED | 计数更新 | 将 Compound Engineering skills 从 44 更新到 42（重新计数：41 compound-engineering + 1 coding-tutor） | COMPLETE (已更新 README 表) |

---

## [2026-03-28 09:29 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 118k 更新到 120k（实际 120,147） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 111k 更新到 114k（实际 114,134） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 gstack ★ 从 52k 更新到 54k（实际 53,533 — v0.13.x design binary、安全审计） | COMPLETE (已更新 README 表) |
| 4 | HIGH | Star 更新 | 将 GSD ★ 从 43k 更新到 44k（实际 43,816 — v1.30.0 GSD SDK headless CLI） | COMPLETE (已更新 README 表) |
| 5 | MED | 计数更新 | 将 gstack skills 从 31 更新到 29（确认了 29 个根级 SKILL.md 目录；2 个在 v0.13.x 中移除/合并） | COMPLETE (已更新 README 表) |
| 6 | MED | 计数更新 | 将 BMAD skills 从 42 更新到 43（31 bmm-skills + 12 core-skills） | COMPLETE (已更新 README 表) |
| 7 | MED | 计数更新 | 将 Compound Engineering skills 从 42 更新到 43（42 compound-eng + 1 coding-tutor） | COMPLETE (已更新 README 表) |

---

## [2026-03-29 08:00 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 120k 更新到 122k（实际 122,129） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 114k 更新到 116k（实际 115,898） | COMPLETE (已更新 README 表) |
| 3 | HIGH | 计数更新 | 更新 ECC agents 从 28 到 30，skills 从 125 到 135（healthcare agent、token-budget-advisor 等新增项） | COMPLETE (已更新 README 表) |
| 4 | HIGH | Star 更新 | 将 gstack ★ 从 54k 更新到 55k（实际 55,000） | COMPLETE (已更新 README 表) |
| 5 | MED | 计数更新 | 将 gstack skills 从 29 更新到 28（README 确认了 28 个根级 SKILL.md 目录） | COMPLETE (已更新 README 表) |
| 6 | MED | 计数更新 | 将 BMAD skills 从 43 更新到 40（重新计数：29 bmm-skills + 11 core-skills；最近补丁中的合并） | COMPLETE (已更新 README 表) |
| 7 | MED | Star 更新 | 将 Compound Engineering ★ 从 11k 更新到 12k（实际 11,500） | COMPLETE (已更新 README 表) |
| 8 | MED | 计数更新 | 更新 Compound Eng agents 从 47 到 48（1 个新增），skills 从 43 到 42（41 compound-eng + 1 coding-tutor） | COMPLETE (已更新 README 表) |

---

## [2026-03-31 07:43 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 122k 更新到 127k（实际 127,473） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 116k 更新到 124k（实际 124,279） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 gstack ★ 从 55k 更新到 59k（实际 59,046 — v0.14.x Review Army、可组合 skills、对抗性审查） | COMPLETE (已更新 README 表) |
| 4 | HIGH | Star 更新 | 将 GSD ★ 从 44k 更新到 46k（实际 45,773） | COMPLETE (已更新 README 表) |
| 5 | HIGH | 计数更新 | 将 gstack skills 从 28 更新到 32（4 个新增：design-html、sidebar CSS inspector、可组合 skill resolver、scope drift detection） | COMPLETE (已更新 README 表) |
| 6 | MED | Star 更新 | 将 Spec Kit ★ 从 83k 更新到 84k（实际 84,042） | COMPLETE (已更新 README 表) |
| 7 | MED | Star 更新 | 将 OpenSpec ★ 从 35k 更新到 36k（实际 35,985） | COMPLETE (已更新 README 表) |
| 8 | MED | 计数更新 | 将 BMAD skills 从 40 更新到 43（32 bmm-skills + 11 core-skills；3 个新 bmm-skills 包括 PRFAQ） | COMPLETE (已更新 README 表) |
| 9 | LOW | 计数验证 | ECC commands 63→3，skills 135→30 — 研究 agent 仅检查了 .claude/ 目录，遗漏了根 commands/ 和 .agents/skills/ 的广度 | INVALID (agent 计数不足 — 保留当前值 63 commands，135 skills) |
| 10 | LOW | 计数验证 | Superpowers agents 5→8 — agent 计算了 1 个显式 + 7 个隐式子 agents，但 v5.0.6 将子 agent 审查循环替换为内联自审查 | ON HOLD (矛盾信号 — v5.0.6 减少了审查 agents 但 brainstorm 添加了新 ones，需要手动验证) |

---

## [2026-04-01 12:35 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 Superpowers ★ 从 127k 更新到 129k（实际 128,925） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 124k 更新到 129k（实际 128,606 — 与 Superpowers 并驾齐驱） | COMPLETE (已更新 README 表) |
| 3 | HIGH | 计数更新 | 更新 ECC agents 30→36，commands 63→71，skills 135→143（6 个新 agents 包括 gan-evaluator/generator/planner、cpp/kotlin/flutter reviewers；8 个新 commands；8 个新 skills） | COMPLETE (已更新 README 表) |
| 4 | MED | Star 更新 | 将 gstack ★ 从 59k 更新到 60k（实际 60,036 — v0.15.0 /checkpoint、/health、跨会话时间线） | COMPLETE (已更新 README 表) |
| 5 | MED | 计数更新 | 将 gstack skills 32→33（v0.15.0 添加了 /checkpoint 和 /health，但部分合并 — 净增 +1） | COMPLETE (已更新 README 表) |
| 6 | LOW | 计数更新 | 将 CE commands 4→3（.claude/commands/ 现为空；3 个 coding-tutor commands 保留），skills 42→40（39 CE + 1 CT） | COMPLETE (已更新 README 表) |
| 7 | LOW | 计数验证 | BMAD skills 43→34 — agent 从 module-help.csv 计数（25 bmm + 9 core），之前的目录计数发现 43（32 bmm + 11 core） | ON HOLD (agent 可能计数不足 — module-help.csv 可能未列出所有 skills；保留 43 直到手动验证) |

---

## [2026-04-02 09:22 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 排序顺序 | 将 ECC（133k）上移到 Superpowers（132k）上方 — ECC 现在有更多 stars | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 ECC ★ 从 129k 更新到 133k（实际 133,114 — 超越了 Superpowers） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 Superpowers ★ 从 129k 更新到 132k（实际 131,818） | COMPLETE (已更新 README 表) |
| 4 | HIGH | 计数更新 | 更新 ECC commands 71→68，skills 143→152（旧 commands 合并到 skills；+9 个新 skills 包括 brand-voice、network-ops） | COMPLETE (已更新 README 表) |
| 5 | HIGH | Star 更新 | 将 gstack ★ 从 60k 更新到 62k（实际 61,800 — v0.15.1 design-html 路由、Session Intelligence Layer） | COMPLETE (已更新 README 表) |
| 6 | HIGH | 计数更新 | 更新 GSD agents 18→21，commands 57→59（v1.31.0：3 个新 agents、skills 发现、Gemini CLI 修复） | COMPLETE (已更新 README 表) |
| 7 | MED | Star 更新 | 将 Spec Kit ★ 从 84k 更新到 85k（实际 84,701） | COMPLETE (已更新 README 表) |
| 8 | MED | Star 更新 | 将 GSD ★ 从 46k 更新到 47k（实际 46,900） | COMPLETE (已更新 README 表) |
| 9 | MED | 计数更新 | 将 BMAD skills 43→40（29 bmm-skills + 11 core-skills；移除了 QA Quinn + Barry solo-dev，添加了 checkpoint-preview） | COMPLETE (已更新 README 表) |
| 10 | MED | Star 更新 | 将 OpenSpec ★ 从 36k 更新到 37k（实际 36,600） | COMPLETE (已更新 README 表) |
| 11 | MED | Star 更新 | 将 CE ★ 从 12k 更新到 13k（实际 12,600） | COMPLETE (已更新 README 表) |
| 12 | MED | 计数更新 | 更新 CE agents 48→49，commands 3→4，skills 40→42（添加了 triage-prs command；+1 agent，+2 skills） | COMPLETE (已更新 README 表) |

---

## [2026-04-03 10:56 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 ECC ★ 从 133k 更新到 136k（实际 135,765 — 拉开与 Superpowers 的差距） | COMPLETE (已更新 README 表) |
| 2 | HIGH | 计数更新 | 更新 ECC agents 36→38，commands 68→75，skills 152→156（NestJS patterns、Jira 集成、C#/Dart 支持、web frontend rules） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 Superpowers ★ 从 132k 更新到 134k（实际 133,718 — v5.0.7 Copilot CLI 支持、contributor guardrails） | COMPLETE (已更新 README 表) |
| 4 | MED | Star 更新 | 将 gstack ★ 从 62k 更新到 63k（实际 63,065 — Session Intelligence Layer、AquaVoice 别名） | COMPLETE (已更新 README 表) |
| 5 | MED | 计数更新 | 将 gstack skills 从 33 更新到 31（确认了 31 个根级 SKILL.md 目录；checkpoint/health 可能是子命令） | COMPLETE (已更新 README 表) |
| 6 | LOW | 计数更新 | 将 GSD commands 从 59 更新到 60（v1.31.0：添加了 /gsd:docs-update） | COMPLETE (已更新 README 表) |
| 7 | LOW | 计数更新 | 将 BMAD skills 从 40 更新到 39（28 bmm-skills + 11 core-skills；少量合并） | COMPLETE (已更新 README 表) |

---

## [2026-04-04 10:45 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | MED | Star 更新 | 将 ECC ★ 从 136k 更新到 137k（实际 137,404） | COMPLETE (已更新 README 表) |
| 2 | MED | Star 更新 | 将 Superpowers ★ 从 134k 更新到 135k（实际 134,933） | COMPLETE (已更新 README 表) |
| 3 | MED | Star 更新 | 将 gstack ★ 从 63k 更新到 64k（实际 63,841 — GStack Browser .app 支持 CDP、反机器人隐身） | COMPLETE (已更新 README 表) |
| 4 | MED | Star 更新 | 将 GSD ★ 从 47k 更新到 48k（实际 47,705 — v1.32.0 Trae/Kilo/Augment/Cline 运行时） | COMPLETE (已更新 README 表) |
| 5 | LOW | Star 更新 | 将 BMAD ★ 从 43k 更新到 44k（实际 43,538） | COMPLETE (已更新 README 表) |
| 6 | LOW | Star 更新 | 将 oh-my-claudecode ★ 从 23k 更新到 24k（实际 23,709 — v4.10.2 HUD、Bedrock 加固） | COMPLETE (已更新 README 表) |

---

## [2026-04-06 09:49 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 ECC ★ 从 137k 更新到 142k（实际 142,218 — v1.10.0 Surface Refresh，仅 4 月 6 日就有 10 个 commits） | COMPLETE (已更新 README 表) |
| 2 | HIGH | 计数更新 | 更新 ECC agents 38→47，commands 75→82，skills 156→182（agent-introspection-debugging、hookify bundle 恢复、26 个新 skills） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 Superpowers ★ 从 135k 更新到 137k（实际 137,166） | COMPLETE (已更新 README 表) |
| 4 | HIGH | 计数更新 | 更新 GSD agents 21→24，commands 60→68（v1.33.0：统一行为引用、STATE.md drift detection、自主 --to N） | COMPLETE (已更新 README 表) |
| 5 | MED | Star 更新 | 将 gstack ★ 从 64k 更新到 65k（实际 65,279 — v0.15.15.0 token 脱敏、team mode） | COMPLETE (已更新 README 表) |
| 6 | MED | 计数更新 | 将 gstack skills 从 31 更新到 34（3 个新增：retro、setup-deploy、learn 等） | COMPLETE (已更新 README 表) |
| 7 | MED | Star 更新 | 将 Spec Kit ★ 从 85k 更新到 86k（实际 85,617 — v0.5.0 原生 skills 架构） | COMPLETE (已更新 README 表) |
| 8 | LOW | Star 更新 | 将 OpenSpec ★ 从 37k 更新到 38k（实际 37,604） | COMPLETE (已更新 README 表) |
| 9 | LOW | Star 更新 | 将 oh-my-claudecode ★ 从 24k 更新到 25k（实际 24,921 — v4.10.0 HUD 升级、LSP 诊断） | COMPLETE (已更新 README 表) |
| 10 | LOW | 计数更新 | 将 CE agents 从 49 更新到 50（1 个新 agent 添加） | COMPLETE (已更新 README 表) |

---

## [2026-04-08 09:38 PM PKT] Development Workflows 更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Star 更新 | 将 ECC ★ 从 142k 更新到 146k（实际 146,462 — v1.10.0 Surface Refresh 势头、ecc2 alpha 开发） | COMPLETE (已更新 README 表) |
| 2 | HIGH | Star 更新 | 将 Superpowers ★ 从 137k 更新到 141k（实际 141,071） | COMPLETE (已更新 README 表) |
| 3 | HIGH | Star 更新 | 将 gstack ★ 从 65k 更新到 67k（实际 67,178 — v0.16.0.0 浏览器数据平台、每标签页状态隔离） | COMPLETE (已更新 README 表) |
| 4 | HIGH | 计数更新 | 将 gstack skills 从 34 更新到 37（3 个新确认：setup-browser-cookies、pair-agent、open-gstack-browser 等） | COMPLETE (已更新 README 表) |
| 5 | MED | Star 更新 | 将 GSD ★ 从 48k 更新到 49k（实际 49,343 — v1.34.0 四类门控分类法、合并后验证） | COMPLETE (已更新 README 表) |
| 6 | MED | Star 更新 | 将 oh-my-claudecode ★ 从 25k 更新到 26k（实际 26,203 — v4.11.1 git status HUD、hostname 元素） | COMPLETE (已更新 README 表) |
| 7 | MED | 计数更新 | 将 oh-my-claudecode skills 从 36 更新到 37（添加了 skillify skill） | COMPLETE (已更新 README 表) |
| 8 | MED | Star 更新 | 将 CE ★ 从 13k 更新到 14k（实际 13,671 — v2.62.0 决策矩阵、headless mode） | COMPLETE (已更新 README 表) |
| 9 | LOW | 计数更新 | 将 CE agents 从 50 更新到 51（1 个新 agent 添加） | COMPLETE (已更新 README 表) |
| 10 | LOW | 计数更新 | 将 CE skills 从 42 更新到 44（2 个新：onboarding skill、interactive deepening mode） | COMPLETE (已更新 README 表) |
