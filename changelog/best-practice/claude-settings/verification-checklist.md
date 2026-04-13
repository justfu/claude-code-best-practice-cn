# 验证清单 — Settings 报告

规则会随时间积累。每次 workflow-changelog 运行时必须以指定深度执行所有规则。当捕获到现有规则应该发现但未能发现（因为规则不存在或深度不够）的新型偏差时，在此追加新规则。

## 深度级别

| 深度 | 含义 | 示例 |
|-------|------|------|
| `exists` | 检查某个章节/表格/文件是否存在 | "报告是否有 Sandbox Settings 表？" |
| `presence-check` | 检查特定项是否存在或不存在 | "Hook Events 表中是否有 `ConfigChange` 事件？" |
| `content-match` | 将实际值与来源逐字比较 | "`model` 设置描述是否与官方文档匹配？" |
| `field-level` | 验证每个单独的字段都被覆盖 | "官方文档中的每个设置键是否都出现在正确的表格中？" |
| `cross-file` | 同一个值必须在多个文件间保持一致 | "CLAUDE.md 中的 hooks 章节是否与报告的 hook events 匹配？" |

---

## 1. Settings 键表格

验证 settings 键表格与官方文档一致的规则。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 1A | 键完整性 | 对于官方文档中的每个设置键，验证它出现在报告的正确章节表格中 | field-level | settings 文档页面 | 2026-03-05 | 初始清单 — 确保不遗漏新的设置键 |
| 1B | 键类型 | 对于表格中的每个键，验证 Type 列与官方文档匹配 | content-match | settings 文档页面 | 2026-03-05 | 初始清单 — 类型不匹配会导致用户困惑 |
| 1C | 键默认值 | 对于每个有默认值的键，验证 Default 列与官方文档匹配 | content-match | settings 文档页面 | 2026-03-05 | 初始清单 — 错误的默认值会导致意外行为 |
| 1D | 键描述 | 对于每个键，验证 Description 列准确反映官方文档的行为 | content-match | settings 文档页面 | 2026-03-05 | 初始清单 — 过时的描述会误导用户 |
| 1E | Scope 列 | 对于每个有 Scope 列的键（MCP、Plugin、Permission 表格），验证 scope 值与官方文档匹配（如 "Managed only"、"Any"、"Project"） | content-match | settings 文档页面 | 2026-03-15 | v2.1.71 发现 `extraKnownMarketplaces` scope 错误（"Any" → "Project"），v2.1.75 发现 `autoMemoryDirectory` scope 限制。没有规则系统地验证 scope 列 |
| 1F | 反向完整性 | 对于报告表格中的每个键，验证它存在于官方文档中，或明确标记为"不在官方文档中 — 未验证"。没有官方依据的键必须添加注释 | field-level | settings 文档页面 + JSON schema | 2026-03-15 | 可疑键（`sandbox.ignoreViolations`、`skipWebFetchPreflight` 等）连续 6 次运行保持 ON HOLD，因为没有规则检查反向方向 — 报告中不应存在的项 |
| 1G | 边界情况语义 | 对于在边界值有特殊行为的设置（如 `0`、空字符串、`null`），验证边界行为是否已记录并与官方文档匹配 | content-match | settings 文档页面 | 2026-03-15 | v2.1.75 较晚发现 `cleanupPeriodDays` 零值行为；v2.1.76 添加了"hooks receive empty transcript_path"细节。边界情况验证不足 |
| 1H | 文件 Scope 检查 | 对于报告中列为 `settings.json` 键的每个键（特别是 Display Settings），验证它确实是 `settings.json` 键，而不是仅在 `~/.claude.json` 中可用的偏好设置。官方文档将"Available settings"（settings.json）与"Global config settings"（~/.claude.json）分开。错误 scope 的键会误导用户，并可能导致 schema 验证错误 | content-match | settings 文档页面"Available settings"与"Global config settings"章节 | 2026-03-18 | v2.1.78 发现 `showTurnDuration` 和 `terminalProgressBarEnabled` 被列为 settings.json 键，但官方文档明确说明它们属于 `~/.claude.json`，且"添加到 settings.json 将触发 schema 验证错误"。没有规则验证文件 scope |

---

## 2. Settings 层级

验证设置层级表格的规则。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 2A | 优先级级别 | 验证层级表格中的所有优先级级别与官方文档匹配（5 级链 + managed policy） | field-level | settings 文档页面 | 2026-03-05 | 初始清单 — 错误的优先级会导致覆盖混淆 |
| 2B | 文件位置 | 对于每个优先级级别，验证文件位置路径与官方文档匹配 | content-match | settings 文档页面 | 2026-03-05 | 初始清单 — 错误的路径会导致设置被忽略 |
| 2C | 合并语义 | 验证数组/对象合并行为描述（如"concatenated and deduplicated"）与官方文档措辞完全一致 | content-match | settings 文档页面 | 2026-03-15 | v2.1.75 发现"merged" → "concatenated and deduplicated"变更。没有规则检查合并行为措辞 |
| 2D | Managed 内部机制 | 验证 managed 层的传递方式（server-managed、MDM、registry、file）和内部优先级顺序与官方文档匹配。验证平台特定的文件路径和弃用说明 | field-level | settings 文档页面 | 2026-03-15 | v2.1.75 重构了 managed 层，增加了内部优先级和 Windows 路径弃用。这些子细节没有专用规则 |

---

## 3. 权限

验证权限配置准确性的规则。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 3A | 权限模式 | 验证表格中的所有权限模式与官方文档匹配 | field-level | settings 文档页面 | 2026-03-05 | 初始清单 — 缺少模式会限制用户选项 |
| 3B | 工具语法模式 | 验证所有工具权限语法模式和示例与官方文档匹配 | content-match | settings 文档页面 | 2026-03-05 | 初始清单 — 错误的语法会导致权限失败 |
| 3C | 双向模式检查 | 验证报告中的每个权限模式存在于官方文档中，且官方文档中的每个模式也存在于报告中。报告中存在但文档中不存在的模式必须标记为"未验证" | field-level | settings + permissions 文档页面 | 2026-03-15 | v2.1.74 发现 `askEdits`/`viewOnly` 在报告中但不在官方文档中 — 它们自第 1 次运行以来就未经验证。单向检查（文档→报告）连续 3 次运行遗漏了此问题 |
| 3D | 评估语义 | 验证权限评估顺序（deny-first）、远程环境限制和路径前缀解析含义（`//`、`~/`、`/`、`./`）是否已记录并与官方文档匹配 | content-match | permissions 文档页面 | 2026-03-15 | v2.1.75 发现缺少评估顺序；v2.1.76 发现缺少路径前缀模式。语义行为规则没有专用检查 |

---

## 4. Hooks（已重定向）

Hook 分析从此 workflow 中排除。Hooks 在 [claude-code-hooks](https://github.com/shanraisshan/claude-code-hooks) 仓库中维护。只需验证重定向链接仍然有效。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 4A | Hooks 重定向 | 验证报告中的 hooks 章节包含有效的重定向链接到 claude-code-hooks 仓库 | exists | 报告文件 | 2026-03-05 | Hooks 已外部化到专用仓库 — 只需检查重定向链接有效性 |

---

## 5. 环境变量

验证环境变量完整性和归属的规则。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 5A | 环境变量完整性 | 验证官方文档中所有可通过 `env` 配置的环境变量都出现在报告中 | field-level | settings 文档页面 | 2026-03-05 | 初始清单 — 缺少环境变量会限制用户配置选项 |
| 5B | 归属边界 | 验证 `best-practice/claude-cli-startup-flags.md` 中的环境变量不会在 settings 报告中重复，反之亦然 | cross-file | claude-cli-startup-flags.md 与 settings 报告 | 2026-03-05 | 初始清单 — 环境变量重构将变量分散到两个文件中，必须防止重复 |
| 5C | 环境变量描述 | 对于表格中的每个环境变量，验证描述（格式、值、行为）与官方 /en/env-vars 页面匹配 | content-match | env-vars 文档页面 | 2026-03-15 | v2.1.74 发现 `ANTHROPIC_CUSTOM_HEADERS` 被描述为"JSON string"而不是"Name: Value format, newline-separated"。规则 5A 仅检查存在性，不检查描述准确性 |
| 5D | 反向环境变量检查 | 对于报告表格中的每个环境变量，验证它存在于官方 /en/env-vars 页面上，或明确标记为"不在官方文档中 — 未验证" | field-level | env-vars 文档页面 | 2026-03-15 | v2.1.76 发现报告中有 7 个环境变量没有官方依据。没有反向检查，未记录的变量会静默积累 |

---

## 6. 示例

验证示例准确性的规则。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 6A | 快速参考示例 | 验证快速参考完整示例使用有效的当前设置，具有正确的语法和合理的值 | content-match | settings 文档页面 | 2026-03-05 | 初始清单 — 示例必须展示当前最佳实践 |
| 6B | 示例 URL 验证 | 验证 JSON 示例块中嵌入的任何 URL（如 `$schema`、API 端点）正确解析并使用当前域名 | exists | HTTP 响应 | 2026-03-15 | v2.1.74 发现 `$schema` URL 使用了错误的域名（`www.schemastore.org` vs `json.schemastore.org`）。代码块中的 URL 未被仅检查 markdown 链接的规则 9B 覆盖 |

---

## 7. 跨文件一致性

验证报告与仓库中其他文件一致性的规则。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 7A | CLAUDE.md 同步 | 验证 CLAUDE.md 的 Configuration Hierarchy 和 Hooks System 章节与报告一致 | cross-file | CLAUDE.md 与报告 | 2026-03-05 | 初始清单 — CLAUDE.md 可能与报告产生偏差 |

---

## 8. 流程

关于 workflow 验证流程本身的元规则。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 8A | 来源可信度守卫 | 仅在官方来源（settings 文档页面、CLI 参考页面、GitHub changelog）确认后才标记为偏差。第三方博客来源可能已过时或错误 — 仅将其用作线索，在标记前与官方文档验证 | content-match | 仅限官方文档 | 2026-03-05 | 沿用自 subagents workflow — 防止博客来源导致的误报 |

---

## 10. 版本元数据与可疑键生命周期

验证报告元数据准确性并防止未解决项无限积累的元规则。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 10A | 版本元数据 | 验证报告的版本徽章、标题设置计数和环境变量计数反映实际审计版本和当前表格行数 | content-match | 报告文件内部一致性 | 2026-03-15 | v2.1.71 发现版本徽章不匹配；v2.1.69 发现标题计数错误。没有规则验证这些元字段 |
| 10B | 可疑键升级 | 连续 5 次运行 ON HOLD 后，可疑键必须得到解决：(a) 通过 JSON schema 确认并注释为"in JSON schema, not on official page"，或 (b) 从报告中移除。报告每个可疑键的运行次数 | exists | changelog 历史 | 2026-03-15 | 可疑键（`sandbox.ignoreViolations`、`skipWebFetchPreflight` 等）跨 6 次运行保持 ON HOLD，没有解决机制。无限积累没有价值 |
| 10C | 双向完整性 | 通用元规则：报告中的每个设置键、权限模式和环境变量必须可追溯到官方来源或明确标记为"未验证"。这是规则 1A/3A/5A 的反向。是 1F、3C、5D 的超集 | field-level | 官方文档 vs 报告 | 2026-03-15 | 从研究中综合的跨领域规则：6 个项较晚被发现，因为只有文档→报告的检查。反向（报告→文档）能捕获孤立条目 |

---

## 9. 超链接

验证报告中所有超链接有效的规则。

| # | 类别 | 检查内容 | 深度 | 对比来源 | 添加日期 | 来源 |
|---|------|----------|------|----------|----------|------|
| 9A | 本地文件链接 | 验证所有相对文件链接解析到现有文件 | exists | 本地文件系统 | 2026-03-05 | 初始清单 — 文件移动可能破坏相对链接 |
| 9B | 外部 URL 链接 | 验证所有外部 URL 返回有效页面（非 404 或错误） | exists | HTTP 响应 | 2026-03-05 | 初始清单 — 外部文档页面可能被重构或删除 |
| 9C | 锚点链接 | 验证所有内部锚点链接指向同一文件中的现有标题 | exists | 文件标题 | 2026-03-05 | 初始清单 — 章节重命名可能破坏锚点链接 |
