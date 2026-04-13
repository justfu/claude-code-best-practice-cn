# Settings 报告 — 变更历史

## 状态说明

| 状态 | 含义 |
|------|------|
| ✅ `COMPLETE (原因)` | 操作已执行并成功解决 |
| ❌ `INVALID (原因)` | 发现不正确、不适用或为有意为之 |
| ✋ `ON HOLD (原因)` | 操作已推迟 — 等待外部依赖或用户决定 |

---

## [2026-03-05 06:18 AM PKT] Claude Code v2.1.69

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失 Settings | 添加 13 个非 hook 缺失的 settings 键（`$schema`、`availableModels`、`fastModePerSessionOptIn`、`teammateMode`、`prefersReducedMotion`、`sandbox.filesystem.*`、`sandbox.network.allowManagedDomainsOnly`、`sandbox.enableWeakerNetworkIsolation`、`allowManagedMcpServersOnly`、`blockedMarketplaces`、`includeGitInstructions`、`pluginTrustMessage`、`fileSuggestion` 表条目） | ✅ COMPLETE (已添加到报告) |
| 2 | HIGH | 缺失环境变量 | 添加缺失的环境变量，包括 `CLAUDE_CODE_DISABLE_ADAPTIVE_THINKING`、`CLAUDE_CODE_DISABLE_1M_CONTEXT`、`CLAUDE_CODE_ACCOUNT_UUID`、`CLAUDE_CODE_DISABLE_GIT_INSTRUCTIONS`、`ENABLE_CLAUDEAI_MCP_SERVERS` 等 | ✅ COMPLETE (已添加 13 个缺失的环境变量到报告) |
| 3 | HIGH | Effort 默认值 | 将 effort 级别默认值从"High"更新为"Medium"（适用于 Max/Team 订阅者）；添加 Sonnet 4.6 支持（v2.1.68 变更） | ✅ COMPLETE (已更新默认值并添加 Sonnet 说明) |
| 4 | MED | Settings 层级 | 添加通过 macOS plist/Windows Registry 的 managed settings（v2.1.61/v2.1.69）；记录跨 scope 的数组合并行为 | ✅ COMPLETE (已添加 plist/registry 和合并说明) |
| 5 | MED | Sandbox 文件系统 | 添加 `sandbox.filesystem.allowWrite`、`denyWrite`、`denyRead` 及路径前缀语义（`//`、`~/`、`/`、`./`） | ✅ COMPLETE (已添加到 sandbox 表) |
| 6 | MED | 权限语法 | 添加 `Agent(name)` 权限模式；记录 `MCP(server:tool)` 语法形式 | ✅ COMPLETE (已添加到工具语法表) |
| 7 | MED | Plugin 缺口 | 添加 `blockedMarketplaces`、`pluginTrustMessage` | ✅ COMPLETE (已添加到 plugins 表) |
| 8 | MED | Model 配置 | 添加 `availableModels` 设置 | ✅ COMPLETE (已添加到通用设置表) |
| 9 | MED | 可疑键 | 验证 `sandbox.network.deniedDomains`、`sandbox.ignoreViolations`、`pluginConfigs` — 存在于报告中但不在官方文档中 | ✋ ON HOLD (保留在报告中等待验证) |
| 10 | LOW | 标题计数 | 将标题从"38 settings and 84 env vars"更新以反映实际计数（~55+ settings，~110+ env vars） | ✅ COMPLETE (已更新标题) |
| 11 | LOW | CLAUDE.md 同步 | 更新 CLAUDE.md 配置层级（添加 managed/CLI/user 级别） | ✋ ON HOLD (等待用户批准) |
| 12 | LOW | 示例更新 | 使用 `$schema`、sandbox filesystem、`Agent(*)`更新快速参考示例，移除 hooks 示例 | ✅ COMPLETE (已更新示例) |
| 13 | MED | Hooks 重定向 | 用到 claude-code-hooks 仓库的重定向替换 hooks 章节 | ✅ COMPLETE (hooks 已外部化到专用仓库) |

---

## [2026-03-07 02:17 PM PKT] Claude Code v2.1.71

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 行为变更 | 修复 `teammateMode`：类型 `boolean` → `string`，默认 `false` → `"auto"`，描述 → "Agent team display: auto, in-process, tmux" | ✅ COMPLETE (类型、默认值和描述已更新) |
| 2 | HIGH | 新 Setting | 将 `allowManagedPermissionRulesOnly` 添加到 Permissions 表（布尔值，仅 managed） | ✅ COMPLETE (已添加到 Permission Keys 表) |
| 3 | HIGH | 缺失环境变量 | 添加约 31 个缺失的环境变量，包括已确认的（`CLAUDE_CODE_MAX_OUTPUT_TOKENS`、`CLAUDE_CODE_DISABLE_FAST_MODE`、`CLAUDE_CODE_DISABLE_AUTO_MEMORY`、`CLAUDE_CODE_USER_EMAIL`、`CLAUDE_CODE_ORGANIZATION_UUID`、`CLAUDE_CONFIG_DIR`）和 agent 报告的（Foundry、Bedrock、mTLS、shell 前缀等） | ✅ COMPLETE (已添加 31 个环境变量到表) |
| 4 | MED | 默认值变更 | 修复 `plansDirectory` 默认值从 `.claude/plans/` 到 `~/.claude/plans` | ✅ COMPLETE (默认值已更新) |
| 5 | MED | 描述变更 | 修复 `sandbox.enableWeakerNetworkIsolation` 描述为"（macOS only）允许访问系统 TLS 信任；降低安全性" | ✅ COMPLETE (描述已更新) |
| 6 | MED | Scope 修复 | 修复 `extraKnownMarketplaces` scope 从"Any"到"Project" | ✅ COMPLETE (scope 和描述已更新) |
| 7 | MED | 边界违规 | 将 `claude-cli-startup-flags.md` 中的 `CLAUDE_CODE_EFFORT_LEVEL` 替换为对 settings 报告的交叉引用 | ✅ COMPLETE (已替换为链接) |
| 8 | MED | 版本徽章 | 将报告版本从 v2.1.69 更新到 v2.1.71 | ✅ COMPLETE (徽章和标题已更新) |
| 9 | LOW | 可疑键 | 验证 `skipWebFetchPreflight`、`sandbox.ignoreViolations`、`sandbox.network.deniedDomains`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` | ✋ ON HOLD (保留在报告中等待验证 — 从 2026-03-05 重复) |
| 10 | LOW | CLAUDE.md 同步 | 更新 CLAUDE.md 配置层级（3 级 → 5+） | ✅ COMPLETE (已更新为包含 managed 层的 5 级层级) |

---

## [2026-03-12 12:23 PM PKT] Claude Code v2.1.74

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 行为变更 | 修复 `dontAsk` 权限模式描述："Auto-accept all tools" → "Auto-denies tools unless pre-approved via `/permissions` or `permissions.allow` rules" | ✅ COMPLETE (描述已根据官方权限文档更正) |
| 2 | HIGH | 新 Setting | 将 `modelOverrides` 添加到 Model Configuration 章节（对象，将 Anthropic model ID 映射到提供商特定的 ID，如 Bedrock ARN） | ✅ COMPLETE (已添加示例和描述) |
| 3 | HIGH | 新 Setting | 将 `allow_remote_sessions` 添加到 managed-only 设置列表（布尔值，默认 `true`，控制 Remote Control/web 会话访问） | ✅ COMPLETE (已添加到 Permission Keys 表) |
| 4 | HIGH | 默认值变更 | 修复 `$schema` URL 从 `https://www.schemastore.org/...` 到 `https://json.schemastore.org/...`（按官方文档） | ✅ COMPLETE (已在描述、示例和 Sources 中更新) |
| 5 | MED | 描述变更 | 修复 `ANTHROPIC_CUSTOM_HEADERS` 格式描述从"JSON string"到"Name: Value format, newline-separated" | ✅ COMPLETE (描述已根据官方文档更新) |
| 6 | MED | 未验证模式 | `askEdits` 和 `viewOnly` 权限模式不在官方文档中 — 仅记录了 5 个模式（default、acceptEdits、plan、dontAsk、bypassPermissions） | ✅ COMPLETE (在表中标记为"not in official docs — unverified") |
| 7 | MED | 缺失环境变量 | 添加 `CLAUDE_CODE_SESSIONEND_HOOKS_TIMEOUT_MS`、`CLAUDE_CODE_DISABLE_FEEDBACK_SURVEY`、`CLAUDE_CODE_DISABLE_TERMINAL_TITLE`、`CLAUDE_CODE_IDE_SKIP_AUTO_INSTALL`、`CLAUDE_CODE_OTEL_HEADERS_HELPER_DEBOUNCE_MS` | ✅ COMPLETE (已添加 5 个环境变量及 `CLAUDE_CODE_OTEL_HEADERS_HELPER_DEBOUNCE_MS`) |
| 8 | MED | 新 Setting | 将 `autoMemoryDirectory` 添加到 Core Configuration（字符串，自定义自动记忆目录）— 版本不确定（agent 意见不一致：v2.1.68 vs v2.1.74），不在 settings 页面上 | ✅ COMPLETE (已添加在 plansDirectory 附近 — 版本未解决) |
| 9 | LOW | 可疑键 | 验证 `skipWebFetchPreflight`、`sandbox.ignoreViolations`、`sandbox.network.deniedDomains`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 仍不在官方文档中 | ✋ ON HOLD (保留在报告中等待验证 — 从 2026-03-05 重复) |
| 10 | LOW | 缺失环境变量 | 将 `CLAUDE_CODE_SUBAGENT_MODEL` 添加到环境变量表（已在 Model 环境示例块中但缺失于表中） | ✅ COMPLETE (已添加到环境变量表) |
| 11 | LOW | 示例更新 | 更新快速参考示例以包含 `modelOverrides` 和更正的 `$schema` URL | ✅ COMPLETE (示例已更新包含两者) |

---

## [2026-03-14 01:35 AM PKT] Claude Code v2.1.75

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | Settings 层级 | 重构以匹配官方 5 级层级：Managed (#1) > CLI args > Local > Project > User。移除 `~/.claude/settings.local.json` 行。添加 managed 层内部优先级（server-managed > MDM > file > HKCU）。注明 Managed"不能被任何其他级别覆盖，包括 CLI args" | ✅ COMPLETE (已重构为 5 级，Managed 为 #1，添加了传递方式、内部优先级和文件路径) |
| 2 | HIGH | 行为变更 | 修复 `availableModels` 描述：从复杂的对象数组（`title`/`modelId`/`effortOptions`）更改为简单的字符串数组 `["sonnet", "haiku"]`（按官方文档） | ✅ COMPLETE (描述已更新为匹配官方文档格式) |
| 3 | HIGH | 行为变更 | 添加 `cleanupPeriodDays` 的 `0` 值行为："设置为 `0` 会在启动时删除所有现有 transcript 并完全禁用会话持久化" | ✅ COMPLETE (0 值行为已添加到描述) |
| 4 | HIGH | 权限语法 | 在 Permissions 章节添加评估顺序说明："规则按顺序评估：先 deny，再 ask，再 allow。第一个匹配的规则生效。" | ✅ COMPLETE (在 Bash 通配符说明之前添加了评估顺序) |
| 5 | MED | 描述变更 | 添加 `autoMemoryDirectory` scope 限制："Not accepted in project settings（`.claude/settings.json`）。仅接受来自 policy、local 和 user settings" | ✅ COMPLETE (scope 限制已添加到描述) |
| 6 | MED | 描述变更 | 添加 `permissions.defaultMode` Remote 环境说明：仅 `acceptEdits` 和 `plan` 在 Remote 环境中生效（v2.1.70） | ✅ COMPLETE (Remote 限制已添加到描述) |
| 7 | MED | Model 配置 | 添加 Opus 4.6 1M 上下文默认说明：截至 v2.1.75，1M 上下文为 Max/Team/Enterprise 计划的默认值 | ✅ COMPLETE (已添加到 Effort Level 说明) |
| 8 | MED | Settings 层级 | 添加 Windows managed 路径说明：v2.1.75 移除了已弃用的 `C:\ProgramData\ClaudeCode\` 回退 — 使用 `C:\Program Files\ClaudeCode\managed-settings.json` | ✅ COMPLETE (在层级章节中添加了弃用说明) |
| 9 | MED | Display & UX | 添加 `fileSuggestion` stdin JSON 格式（`{"query": "..."}`）和 15 路径输出限制详情 | ✅ COMPLETE (stdin 格式和输出限制已添加到 File Suggestion 章节) |
| 10 | MED | Settings 层级 | 将数组合并说明从"merged"更新为"concatenated and deduplicated"（按官方文档） | ✅ COMPLETE (层级 Important 章节中的措辞已更新) |
| 11 | LOW | 可疑键 | `sandbox.ignoreViolations`、`sandbox.network.deniedDomains` 仍不在官方文档或 JSON schema 顶层中 | ✋ ON HOLD (保留在报告中等待验证 — 从 2026-03-05 重复) |
| 12 | LOW | 可疑键 | `skipWebFetchPreflight`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 已在 JSON schema 中确认但不在官方 settings 页面上 | ✋ ON HOLD (保留在报告中 — schema 验证通过，从 2026-03-05 重复) |

---

## [2026-03-15 12:52 PM PKT] Claude Code v2.1.76

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新 Setting | 将 `effortLevel` 添加到 General Settings 或 Model Configuration — 跨会话持久化 effort 级别（`"low"`、`"medium"`、`"high"`）。已在官方 settings 页面确认 | ✋ ON HOLD (等待用户批准) |
| 2 | HIGH | 新 Settings | 添加 Worktree Settings 章节，包含 `worktree.sparsePaths`（数组，sparse-checkout cone 模式）和 `worktree.symlinkDirectories`（数组，避免重复的符号链接目录）。已在官方 settings 页面确认 | ✋ ON HOLD (等待用户批准) |
| 3 | HIGH | 新 Setting | 将 `feedbackSurveyRate` 添加到 General Settings — 会话质量调查的概率（0-1）。已在官方 settings 页面确认 | ✋ ON HOLD (等待用户批准) |
| 4 | HIGH | 缺失环境变量 | 将 20 个缺失的环境变量添加到表：`CLAUDE_CODE_AUTO_COMPACT_WINDOW`、`CLAUDE_CODE_ENABLE_PROMPT_SUGGESTION`、`CLAUDE_CODE_PLAN_MODE_REQUIRED`、`CLAUDE_CODE_TEAM_NAME`、`CLAUDE_CODE_TASK_LIST_ID`、`CLAUDE_ENV_FILE`、`FORCE_AUTOUPDATE_PLUGINS`、`HTTP_PROXY`、`HTTPS_PROXY`、`NO_PROXY`、`MCP_TOOL_TIMEOUT`、`MCP_CLIENT_SECRET`、`MCP_OAUTH_CALLBACK_PORT`、`IS_DEMO`、`SLASH_COMMAND_TOOL_CHAR_BUDGET`、`VERTEX_REGION_CLAUDE_3_5_HAIKU`、`VERTEX_REGION_CLAUDE_3_7_SONNET`、`VERTEX_REGION_CLAUDE_4_0_OPUS`、`VERTEX_REGION_CLAUDE_4_0_SONNET`、`VERTEX_REGION_CLAUDE_4_1_OPUS`。已在官方 /en/env-vars 页面确认 | ✋ ON HOLD (等待用户批准) |
| 5 | HIGH | 缺失环境变量 | 将 `ANTHROPIC_DEFAULT_OPUS_MODEL`、`ANTHROPIC_DEFAULT_SONNET_MODEL`、`MAX_THINKING_TOKENS` 从仅代码块移动到 Common Environment Variables 表 | ✋ ON HOLD (等待用户批准) |
| 6 | HIGH | 链接损坏 | 修复 `https://claudelog.com/configuration/` — 返回 ECONNREFUSED。移除或替换为有效的来源 | ✋ ON HOLD (等待用户批准) |
| 7 | MED | 描述变更 | 更新 `cleanupPeriodDays` 描述添加："hooks receive an empty `transcript_path`"当设置为 0 时。按官方文档 | ✋ ON HOLD (等待用户批准) |
| 8 | MED | 未验证环境变量 | 将报告中 7 个不在官方文档中的环境变量标记为未验证：`CLAUDE_CODE_DISABLE_MCP`、`CLAUDE_CODE_DISABLE_TOOLS`、`CLAUDE_CODE_HIDE_ACCOUNT_INFO`、`CLAUDE_CODE_MAX_TURNS`、`CLAUDE_CODE_PROMPT_CACHING_ENABLED`、`CLAUDE_CODE_SKIP_SETTINGS_SETUP`、`DISABLE_NON_ESSENTIAL_MODEL_CALLS` | ✋ ON HOLD (等待用户批准) |
| 9 | MED | 新来源 | 将 `https://code.claude.com/docs/en/env-vars` 添加到 Sources 章节 — 官方环境变量参考页面 | ✋ ON HOLD (等待用户批准) |
| 10 | MED | 示例更新 | 更新快速参考示例以包含 `effortLevel` 和 `worktree` 设置 | ✋ ON HOLD (等待用户批准) |
| 11 | LOW | 可疑键 | `sandbox.ignoreViolations`、`sandbox.network.deniedDomains` 仍不在官方文档 sandbox 表中 | ✋ ON HOLD (保留在报告中等待验证 — 从 2026-03-05 重复) |
| 12 | LOW | 可疑键 | `skipWebFetchPreflight`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 仍在 JSON schema 中但不在官方 settings 页面上 | ✋ ON HOLD (保留在报告中 — schema 验证通过，从 2026-03-05 重复) |

---

## [2026-03-15 01:10 PM PKT] Claude Code v2.1.76

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新 Setting | 将 `effortLevel` 添加到 Model Configuration — 跨会话持久化 effort 级别（`"low"`、`"medium"`、`"high"`）。同时将 `/effort` 命令添加到 Useful Commands 并更新 Effort Level 操作说明 | ✅ COMPLETE (已添加到 Model Overrides 表，更新了操作说明，添加了 /effort 命令) |
| 2 | HIGH | 新 Settings | 添加 Worktree Settings 章节，包含 `worktree.sparsePaths`（数组，sparse-checkout cone 模式）和 `worktree.symlinkDirectories`（数组，避免重复的符号链接目录） | ✅ COMPLETE (Core Configuration 中新建了 Worktree Settings 子章节，包含表格和示例) |
| 3 | HIGH | 新 Setting | 将 `feedbackSurveyRate` 添加到 General Settings — 会话质量调查的概率（0-1） | ✅ COMPLETE (已添加到 General Settings 表) |
| 4 | HIGH | 缺失环境变量 | 将 23 个缺失的环境变量添加到表（20 个真正新的 + 3 个从仅代码块移出） | ✅ COMPLETE (已添加全部 23 个环境变量到 Common Environment Variables 表) |
| 5 | HIGH | 链接损坏 | 上次运行标记 `https://claudelog.com/configuration/` 为 ECONNREFUSED — 现在成功加载 | ✅ COMPLETE (链接已恢复，无需操作) |
| 6 | MED | 权限语法 | 添加 Read/Edit gitignore 风格路径模式（`//path`、`~/path`、`/path`、`./path`），词边界通配符详情和旧版 `:*` 弃用说明 | ✅ COMPLETE (已添加路径模式表、词边界说明和 `:*` 弃用) |
| 7 | MED | 描述变更 | 更新 `cleanupPeriodDays` 添加"hooks receive an empty `transcript_path`"当设置为 0 时 | ✅ COMPLETE (已添加到描述) |
| 8 | MED | 未验证环境变量 | 将 7 个不在官方文档中的环境变量标记为未验证 | ✅ COMPLETE (已添加"not in official docs — unverified"标记) |
| 9 | MED | 新来源 | 将 `https://code.claude.com/docs/en/env-vars` 和 `https://code.claude.com/docs/en/permissions` 添加到 Sources 章节 | ✅ COMPLETE (已添加两个 URL) |
| 10 | MED | 示例更新 | 更新快速参考示例以包含 `effortLevel` 和 `worktree` 设置 | ✅ COMPLETE (在示例中添加了 effortLevel 和 worktree 块) |
| 11 | LOW | 可疑键 | `sandbox.ignoreViolations`、`sandbox.network.deniedDomains` 仍不在官方文档 sandbox 表中 | ✋ ON HOLD (保留在报告中等待验证 — 从 2026-03-05 重复) |
| 12 | LOW | 可疑键 | `skipWebFetchPreflight`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 仍在 JSON schema 中但不在官方 settings 页面上 | ✋ ON HOLD (保留在报告中 — schema 验证通过，从 2026-03-05 重复) |

---

## [2026-03-17 12:54 PM PKT] Claude Code v2.1.77

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新 Setting | 将 `sandbox.filesystem.allowRead` 添加到 Sandbox Settings 表 — 重新允许在 `denyRead` 区域内的读取访问（数组，默认 `[]`）。已在 v2.1.77 changelog 中确认 | ✅ COMPLETE (已添加到 Sandbox Settings 表 denyRead 行之后) |
| 2 | HIGH | 描述变更 | 更新 `CLAUDE_CODE_MAX_OUTPUT_TOKENS` 描述：Opus 4.6 默认值增加到 64k，Opus 4.6 和 Sonnet 4.6 上限增加到 128k（v2.1.77 changelog） | ✅ COMPLETE (描述已更新，包含 model 特定的默认值和上限) |
| 3 | HIGH | 缺失环境变量 | 将 `CLAUDECODE` 添加到 Common Environment Variables 表 — 在生成的 shell 环境中设置为 `1`。已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已添加到环境变量表) |
| 4 | HIGH | 缺失环境变量 | 将 `CLAUDE_CODE_SKIP_FAST_MODE_NETWORK_ERRORS` 添加到 Common Environment Variables 表 — 在 org 状态检查失败时允许 fast mode。已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已添加到环境变量表) |
| 5 | MED | 环境变量表 | 将 `ANTHROPIC_MODEL` 和 `ANTHROPIC_DEFAULT_HAIKU_MODEL` 从仅代码块移动到 Common Environment Variables 表。两者已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已添加两者到其他 ANTHROPIC_ 变量附近的环境变量表) |
| 6 | MED | 可疑键升级 | `sandbox.network.deniedDomains` — 连续 8 次 ON HOLD 运行（自 2026-03-05 起）。不在官方文档页面或 JSON schema 中。按规则 10B：标记为"not in official docs — unverified" | ✅ COMPLETE (已添加未验证注释到描述) |
| 7 | MED | 可疑键升级 | `allow_remote_sessions` — 不在官方文档页面或 JSON schema 中。标记为"not in official docs — unverified" | ✅ COMPLETE (已添加未验证注释到描述) |
| 8 | LOW | 可疑键解决 | `sandbox.ignoreViolations` — 连续 8 次 ON HOLD 运行。已在 JSON schema 中确认。注释："in JSON schema, not on official settings page" | ✅ COMPLETE (已添加 schema 注释到描述) |
| 9 | LOW | 可疑键解决 | `skipWebFetchPreflight`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 连续 8 次 ON HOLD 运行。全部已在 JSON schema 中确认。注释："in JSON schema, not on official settings page" | ✅ COMPLETE (已添加 schema 注释到所有 4 个描述) |
| 10 | LOW | 标题计数 | 将标题环境变量计数从"160+"更新为"100+" — 实际表中有 97 个环境变量 | ✅ COMPLETE (标题已更新为"100+ environment variables"，版本更新为 v2.1.77) |

---

## [2026-03-18 11:53 PM PKT] Claude Code v2.1.78

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失 Setting | 将 `voiceEnabled` 添加到 General Settings 表 — 启用按住说话语音听写（布尔值，由 `/voice` 写入，需要 Claude.ai 账户）。已在官方 settings 页面确认 | ✅ COMPLETE (已添加到 General Settings 表 feedbackSurveyRate 之前) |
| 2 | HIGH | 缺失 Setting | 将 `filesystem.allowManagedReadPathsOnly` 添加到 Sandbox Settings 表 — 仅 managed，仅尊重 managed `allowRead` 路径（布尔值，默认 false）。已在官方 settings 页面确认 | ✅ COMPLETE (已添加到 Sandbox Settings 表 enableWeakerNetworkIsolation 之前) |
| 3 | HIGH | Display 位置 | 将 `showTurnDuration` 和 `terminalProgressBarEnabled` 从 Display Settings 表移动到单独的"Global Config Settings (~/.claude.json)"子章节。官方文档说明："Adding them to settings.json will trigger a schema validation error" | ✅ COMPLETE (创建了新子章节和表；从 settings.json Display Settings 表和示例中移除) |
| 4 | HIGH | 默认值变更 | 修复 `MAX_MCP_OUTPUT_TOKENS` 默认值从 50000 到 25000。官方 /en/env-vars 页面确认默认值：25000 | ✅ COMPLETE (默认值已更新，添加了警告阈值说明) |
| 5 | HIGH | 缺失环境变量 | 添加 `CLAUDE_CODE_NEW_INIT`、`CLAUDE_CODE_PLUGIN_SEED_DIR`、`DISABLE_FEEDBACK_COMMAND` 到环境变量表。全部已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已添加全部 3 个环境变量到表) |
| 6 | MED | 验证修复 | 移除 `allow_remote_sessions` 的"unverified"注释 — 现在已在官方 permissions 页面确认为 managed-only 设置。上次运行（v2.1.77 #7）错误地标记为未验证 | ✅ COMPLETE (已移除"unverified"注释) |
| 7 | MED | 环境变量重命名 | 将 `DISABLE_BUG_COMMAND` 更新为 `DISABLE_FEEDBACK_COMMAND` — 官方文档说 `DISABLE_FEEDBACK_COMMAND` 是当前名称，`DISABLE_BUG_COMMAND` 是"旧名称" | ✅ COMPLETE (已重命名并添加别名说明) |
| 8 | MED | 描述变更 | 更新 `CLAUDE_CODE_EFFORT_LEVEL` 包含 `max`（仅 Opus 4.6）和 `auto` 值。官方 /en/env-vars 页面确认："Values: low, medium, high, max (Opus 4.6 only), or auto" | ✅ COMPLETE (描述已更新包含所有值和优先级说明) |
| 9 | MED | 描述变更 | 修复 `CLAUDE_CODE_ENABLE_TASKS` 描述 — 官方："Set to true to enable task tracking in non-interactive mode (-p flag). Tasks are on by default in interactive mode." 报告当前说"Set to false to disable" | ✅ COMPLETE (描述已更正以匹配官方文档) |
| 10 | MED | 描述变更 | 更新 `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC` 添加："Equivalent of setting DISABLE_AUTOUPDATER, DISABLE_FEEDBACK_COMMAND, DISABLE_ERROR_REPORTING, and DISABLE_TELEMETRY" | ✅ COMPLETE (描述已更新包含等效变量列表) |
| 11 | MED | 示例更新 | 从快速参考示例中移除 `showTurnDuration` — 按官方文档它不属于 settings.json | ✅ COMPLETE (已从快速参考示例和 Display & UX 示例中移除) |
| 12 | LOW | 环境变量默认值 | 验证 `MCP_TIMEOUT` 默认值（报告说 10000）— 官方文档未指定默认值 | ✅ COMPLETE (已移除未验证的默认值 — 官方文档省略了它) |

---

## [2026-03-19 12:38 PM PKT] Claude Code v2.1.79

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失环境变量 | 将 `ANTHROPIC_CUSTOM_MODEL_OPTION`、`ANTHROPIC_CUSTOM_MODEL_OPTION_NAME`、`ANTHROPIC_CUSTOM_MODEL_OPTION_DESCRIPTION` 添加到 Common Environment Variables 表 — 用于向 `/model` 选择器添加自定义条目的 model-config 变量。已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已在表中 ANTHROPIC_BASE_URL 之后添加 3 个环境变量) |
| 2 | HIGH | 描述变更 | 更新 `CLAUDE_CODE_PLUGIN_SEED_DIR` 从单数到复数："Path to one or more read-only plugin seed directories, separated by `:` on Unix or `;` on Windows"。在 v2.1.79 changelog 中更改。已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (描述已更新为多目录支持) |
| 3 | HIGH | Sandbox 路径前缀 | 修复 sandbox.filesystem 路径前缀文档：`/` = 绝对路径（标准 Unix），`./` = 项目相对路径，`//` = 旧版仍有效。报告当前显示反转的约定。官方文档明确说明："This syntax differs from Read and Edit permission rules" | ✅ COMPLETE (已更新所有 4 个 sandbox.filesystem 条目为正确的前缀约定，添加了对 Read/Edit 权限规则的交叉引用说明和跨 scope 合并详情) |
| 4 | MED | 描述变更 | 扩展 `CLAUDE_CODE_AUTO_COMPACT_WINDOW` 描述 — 当前"Auto-compact window behavior configuration"过于简略。官方文档描述：token 容量、默认值（200K 标准 / 1M 扩展）、与 `CLAUDE_AUTOCOMPACT_PCT_OVERRIDE` 的交互、状态行解耦 | ✅ COMPLETE (扩展描述包含 token 容量、model 默认值、AUTOCOMPACT_PCT 交互和状态行解耦) |

---

## [2026-03-20 08:41 AM PKT] Claude Code v2.1.80

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新 Setting | 将 `channelsEnabled` 添加到 MCP Settings 表 — 仅 managed 布尔值，控制 Team 和 Enterprise 用户的 channel 消息传递。已在官方 settings 页面确认 | ✅ COMPLETE (已添加到 MCP Settings 表 allowManagedMcpServersOnly 之后) |
| 2 | MED | 版本徽章 | 将报告版本从 v2.1.79 更新到 v2.1.80 | ✅ COMPLETE (徽章和标题已更新) |

---

## [2026-03-21 09:17 PM PKT] Claude Code v2.1.81

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失 Settings (~/.claude.json) | 将 `autoConnectIde`（布尔值，默认 `false`）和 `autoInstallIdeExtension`（布尔值，默认 `true`）添加到 Global Config Settings 表。已在官方 settings 页面"Global config settings"下确认 | ✅ COMPLETE (已添加两个键到 ~/.claude.json 表 showTurnDuration 之前) |
| 2 | HIGH | 不正确 Setting | `allow_remote_sessions` 在 Permission Keys 表中列为 managed-only 布尔值，但官方 permissions 页面说明："Access to Remote Control and web sessions is not controlled by a managed settings key." 标记为未验证或移除 | ✅ COMPLETE (重新添加未验证注释，附带官方文档引用和管理员 UI 链接) |
| 3 | MED | 版本更新 | 将报告版本徽章从 v2.1.80 更新到 v2.1.81 | ✅ COMPLETE (徽章、标题版本和标题文本已更新) |
| 4 | MED | 新 Setting | 添加 `showClearContextOnPlanAccept` — 在 v2.1.81 changelog 中确认。当 `true` 时，恢复计划接受时的"clear context"选项（默认隐藏）。尚未在官方 settings 页面 — 可能是 `~/.claude.json` 键 | ✅ COMPLETE (已添加到 Global Config Settings 表，附带 changelog 来源说明) |
| 5 | MED | Plugin 文档 | 在 Plugin Settings 章节记录 `source: 'settings'` 作为 marketplace 来源类型。官方 settings 页面将其列为 `extraKnownMarketplaces` 的 7 个来源类型之一 | ✅ COMPLETE (已添加全部 7 个来源类型列表和内联 marketplace 示例) |
| 6 | MED | 状态行字段 | 将 `rate_limits` 字段组添加到 Status Line Input Fields 表 — 包含 `five_hour.used_percentage`、`five_hour.resets_at`、`seven_day.used_percentage`、`seven_day.resets_at`。在 v2.1.80 中添加 | ✅ COMPLETE (已添加 4 个 rate_limits 字段到 Status Line Input Fields 表) |

---

## [2026-03-23 10:02 PM PKT] Claude Code v2.1.81

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失 Setting (~/.claude.json) | 将 `editorMode`（字符串，默认 `"normal"`，值：`"normal"` 或 `"vim"`）添加到 Global Config Settings 表。运行 `/vim` 时自动写入。已在官方 settings 页面确认 | ✅ COMPLETE (已添加到 Global Config Settings 表 autoInstallIdeExtension 之后) |
| 2 | HIGH | 文件 Scope 修复 | 将 `showClearContextOnPlanAccept` 从 Global Config Settings (~/.claude.json) 移动到 General Settings (settings.json)。官方文档现在将其列在主 Available settings 表中，而非 Global config 表中。移除过时的注释"not yet on official settings page" | ✅ COMPLETE (已移动到 General Settings 表 feedbackSurveyRate 之前，移除了过时注释) |
| 3 | MED | 描述变更 | 修复 `terminalProgressBarEnabled` 支持的终端从"Windows Terminal, iTerm2"到"ConEmu, Ghostty 1.2.0+, and iTerm2 3.6.6+"（按官方文档） | ✅ COMPLETE (终端列表已更新) |
| 4 | MED | 描述变更 | 在 `availableModels` 描述中添加"Config tool" — 官方文档说"via `/model`, `--model`, Config tool, or `ANTHROPIC_MODEL`"。报告当前省略了"Config tool" | ✅ COMPLETE (已添加"Config tool"到描述) |

---

## [2026-03-25 08:16 PM PKT] Claude Code v2.1.83

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新 Setting | 将 `autoMode` 添加到 Permissions 章节 — 对象，包含 `environment`、`allow`、`soft_deny` 数组，用于配置 auto mode 分类器。不从共享项目设置（`.claude/settings.json`）中读取。可在 user、local 和 managed settings 中使用。已在官方 settings + permissions 页面确认 | ✅ COMPLETE (已添加到 Permission Keys 表，包含完整描述、scope 限制和 `claude auto-mode defaults` 说明) |
| 2 | HIGH | 新 Setting | 将 `disableAutoMode` 添加到 Permissions 章节 — 字符串，设置为 `"disable"` 以阻止 auto mode 激活。从 Shift+Tab 循环中移除 `auto`。可在任何 settings 级别设置，在 managed settings 中最有用。已在官方 settings + permissions 页面确认 | ✅ COMPLETE (已添加到 Permission Keys 表 `autoMode` 之后) |
| 3 | HIGH | 新权限模式 | 将 `auto` 添加到 Permission Modes 表 — 后台分类器替代手动提示。研究预览版。需要 Team 计划 + Sonnet/Opus 4.6。已在官方 permission-modes 页面确认 | ✅ COMPLETE (已添加到 Permission Modes 表，包含分类器详情和回退行为) |
| 4 | HIGH | 新 Setting | 将 `sandbox.failIfUnavailable` 添加到 Sandbox Settings 表 — 布尔值，默认 `false`，当 sandbox 启用但无法启动时以错误退出而非不使用 sandbox 运行。已在 v2.1.83 changelog 确认 | ✅ COMPLETE (已添加到 Sandbox Settings 表 `sandbox.enabled` 之后) |
| 5 | HIGH | 新 Setting | 将 `disableDeepLinkRegistration` 添加到 General Settings 表 — 布尔值，阻止 `claude-cli://` 协议处理器注册。已在 v2.1.83 changelog 确认 | ✅ COMPLETE (已添加到 General Settings 表 `feedbackSurveyRate` 之前) |
| 6 | HIGH | 缺失环境变量 | 将 `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB` 添加到 Common Environment Variables 表 — 设置为 `1` 以从子进程环境（Bash tool、hooks、MCP stdio servers）中剥离 Anthropic 和云提供商凭证。已在 v2.1.83 changelog 确认 | ✅ COMPLETE (已添加到环境变量表 `CLAUDE_CODE_SUBAGENT_MODEL` 之后) |
| 7 | HIGH | Settings 层级 | 将 `managed-settings.d/` drop-in 目录添加到 Managed Settings 章节 — 独立策略片段，与 `managed-settings.json` 并存，按字母顺序合并。已在 v2.1.83 changelog 确认 | ✅ COMPLETE (已作为 managed settings 传递方式下的项目符号添加) |
| 8 | HIGH | 链接损坏 | 修复 Sources 中的 `https://claudelog.com/configuration/` — 返回 403 Forbidden。移除或替换为有效的来源 | ✅ COMPLETE (已替换为经过验证有效的 `https://claudelog.com/claude-code-changelog/`) |
| 9 | MED | 版本徽章 | 将报告版本从 v2.1.81 更新到 v2.1.83 | ✅ COMPLETE (徽章和标题已在 Phase 2.6 中更新) |
| 10 | MED | 示例更新 | 在快速参考示例中添加 `autoMode` 以演示 auto mode 分类器配置 | ✅ COMPLETE (在 `permissions` 块之前添加了 `autoMode` 块，包含 `environment` 数组) |
| 11 | MED | 路径变更 | 修复 Windows registry 路径从 `Software\Anthropic\ClaudeCode` 到 `SOFTWARE\Policies\ClaudeCode`（HKLM 和 HKCU）。官方文档已更新使用 `Policies` 子键 | ✅ COMPLETE (已更新为 `HKLM\SOFTWARE\Policies\ClaudeCode` 和 `HKCU\SOFTWARE\Policies\ClaudeCode`，附带优先级说明) |
| 12 | LOW | 缺失别名 | 将 `opus[1m]` 添加到 Model Aliases 表 — Opus 4.6 带 1M 上下文，自 v2.1.75 起在 Max/Team/Enterprise 上默认可用 | ✅ COMPLETE (已添加到 Model Aliases 表 `sonnet[1m]` 之后) |

---

## [2026-03-26 01:04 PM PKT] Claude Code v2.1.84

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新 Setting | 将 `defaultShell` 添加到 General Settings — 字符串，默认 `"bash"`，接受 `"bash"` 或 `"powershell"`。在 Windows 上通过 PowerShell 路由交互式 `!` 命令。需要 `CLAUDE_CODE_USE_POWERSHELL_TOOL=1`。已在官方 settings 页面确认 | ✅ COMPLETE (已添加到 General Settings 表 teammateMode 之后) |
| 2 | HIGH | 新 Setting | 将 `allowedChannelPlugins` 添加到 MCP Settings — 数组，仅 managed。允许推送消息的 channel plugins 白名单。设置后替换默认的 Anthropic 白名单。需要 `channelsEnabled: true`。已在官方 settings 页面确认 | ✅ COMPLETE (已添加到 MCP Settings 表 channelsEnabled 之后) |
| 3 | HIGH | 新 Setting | 将 `useAutoModeDuringPlan` 添加到 Permission Keys — 布尔值，默认 `true`。计划模式在 auto mode 可用时使用 auto mode 语义。不从共享项目设置中读取。已在官方 settings 页面确认 | ✅ COMPLETE (已添加到 Permission Keys 表 disableAutoMode 之后) |
| 4 | HIGH | 缺失环境变量 | 添加 9 个 model 自定义环境变量：`ANTHROPIC_DEFAULT_{OPUS,SONNET,HAIKU}_MODEL_{NAME,DESCRIPTION,SUPPORTED_CAPABILITIES}` 用于在 Bedrock/Vertex/Foundry 上自定义 `/model` 选择器。已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (在每个基础 model 变量之后添加了 3 个变量：Haiku、Opus、Sonnet) |
| 5 | HIGH | 缺失环境变量 | 添加 `CLAUDE_CODE_DISABLE_NONSTREAMING_FALLBACK` — 在 streaming 失败时禁用非 streaming 回退。防止通过代理重复执行 tool。已在官方 /en/env-vars 页面确认（v2.1.83 添加，上次运行遗漏） | ✅ COMPLETE (已添加在 CLAUDE_CODE_DISABLE_FAST_MODE 之后) |
| 6 | HIGH | 缺失环境变量 | 添加 `CLAUDE_CODE_USE_POWERSHELL_TOOL` — 在 Windows 上启用 PowerShell tool（opt-in preview）。仅限原生 Windows，非 WSL。已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已添加在 CLAUDE_CODE_USE_FOUNDRY 之后) |
| 7 | HIGH | 链接损坏 | 修复 Sources 中的 `https://claudelog.com/claude-code-changelog/` — 返回 403 Forbidden。替换为官方 GitHub changelog URL | ✅ COMPLETE (已替换为 github.com/anthropics/claude-code/blob/main/CHANGELOG.md) |
| 8 | MED | Settings 层级 | 更新 managed 层优先级："file-based (`managed-settings.d/*.json` + `managed-settings.json`)"并添加"across tiers"限定符。按官方文档添加层内合并说明 | ✅ COMPLETE (已更新优先级描述为 file-based tier 和跨层限定符) |
| 9 | MED | Settings 层级 | 扩展 drop-in 目录合并语义：systemd 约定、标量覆盖、数组 concat+dedup、深度合并、隐藏文件排除、数字前缀技巧。按官方 settings 页面 | ✅ COMPLETE (已扩展完整的 systemd 约定详情和数字前缀技巧) |
| 10 | MED | 注释 | 按规则 1F 反向完整性检查，为 `disableDeepLinkRegistration` 添加"in changelog, not on official settings page"注释 | ✅ COMPLETE (已添加注释到描述) |
| 11 | MED | 示例更新 | 在快速参考示例中添加 `defaultShell` 以演示 PowerShell 配置 | ✅ COMPLETE (在示例中添加了"defaultShell": "bash") |

---

## [2026-03-27 06:32 PM PKT] Claude Code v2.1.85

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失环境变量 | 将 `CLAUDE_STREAM_IDLE_TIMEOUT_MS` 添加到 Common Environment Variables 表 — streaming 空闲看门狗关闭停滞连接的超时时间（毫秒，默认：90000）。已在官方 /en/env-vars 页面确认。v2.1.84 中添加但上次运行遗漏 | ✅ COMPLETE (已添加到环境变量表 CLAUDE_CODE_OTEL_HEADERS_HELPER_DEBOUNCE_MS 之后) |
| 2 | HIGH | 版本更新 | 将报告版本徽章从 v2.1.84 更新到 v2.1.85 | ✅ COMPLETE (徽章、标题版本和标题文本已在 Phase 2.6 中更新) |
| 3 | MED | 新环境变量 | 将 `OTEL_LOG_TOOL_DETAILS` 添加到环境变量表 — 控制 OpenTelemetry 事件中的 `tool_parameters`。仅 v2.1.85 changelog（尚未在官方 env-vars 页面）。添加 changelog 来源注释 | ✅ COMPLETE (已添加"in v2.1.85 changelog, not yet on official env-vars page"注释) |
| 4 | MED | 新环境变量（归属） | 决定 `CLAUDE_CODE_MCP_SERVER_NAME` 和 `CLAUDE_CODE_MCP_SERVER_URL` 的归属 — 传递给 MCP `headersHelper` 脚本的环境变量（v2.1.85 changelog）。可能属于 hooks 仓库而非 settings 报告 | ✅ COMPLETE (已添加到 settings 报告并附带 changelog 注释 — 这些可通过 `env` 键配置，不仅限于 hook) |

---

## [2026-03-28 06:10 PM PKT] Claude Code v2.1.86

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 文件 Scope | 将 `teammateMode` 从 General Settings (settings.json) 移动到 Global Config Settings (~/.claude.json)。官方 settings 页面将其列在"Global config settings"下 — 添加到 settings.json 会触发 schema 验证错误（规则 1H）。与 v2.1.78 `showTurnDuration` 修复模式相同 | ✅ COMPLETE (已从 General Settings 表移除，添加到 Global Config Settings 表 terminalProgressBarEnabled 之后，附带 agent-teams 文档链接) |
| 2 | HIGH | 类型 + 注释 | 修复 `disableDeepLinkRegistration`：将类型从 `boolean` 更改为 `string`（值：`"disable"`），更新描述以匹配官方文档，移除过时的"(in changelog, not on official settings page)"注释。现在已在官方 settings 页面确认（第 169 行） | ✅ COMPLETE (类型已更改为 string，描述已更新为匹配官方文档，changelog 注释已移除) |
| 3 | HIGH | 版本更新 | 将报告版本徽章从 v2.1.85 更新到 v2.1.86 | ✅ COMPLETE (徽章和标题已在 Phase 2.6 中更新) |

---

## [2026-03-31 07:02 PM PKT] Claude Code v2.1.88

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失环境变量 | 将 `CLAUDE_CODE_NO_FLICKER` 添加到 Common Environment Variables 表 — 启用无闪烁备用屏幕渲染（v2.1.88）。已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已添加在 CLAUDE_CODE_DISABLE_TERMINAL_TITLE 之后) |
| 2 | HIGH | 缺失环境变量 | 将 `CLAUDE_CODE_SCROLL_SPEED` 和 `CLAUDE_CODE_DISABLE_MOUSE` 添加到 Common Environment Variables 表 — 全屏 UI 控制。已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已添加在 CLAUDE_CODE_NO_FLICKER 之后) |
| 3 | HIGH | 版本更新 | 将报告版本徽章从 v2.1.86 更新到 v2.1.88 | ✅ COMPLETE (徽章、标题版本和标题文本已在 Phase 2.6 中更新) |
| 4 | HIGH | 链接损坏 | 修复 Sources 中的 `https://www.eesel.ai/blog/settings-json-claude-code` — 返回仅 CSS 内容，无可读博客文章 | ✅ COMPLETE (已从 Sources 章节移除损坏链接) |
| 5 | MED | Settings 层级 | 将 `managed-mcp.json` 添加到 file-based managed 传递方式 — 官方 settings 页面将其与 `managed-settings.json` 并列列出用于 MCP server 配置 | ✅ COMPLETE (已添加到 Settings Hierarchy 的 File 传递方式项目符号) |
| 6 | MED | Plugin 来源类型 | 将 `url`、`npm`、`file` marketplace 来源类型注释为"not in official docs — unverified"（仅 `github`、`git`、`directory`、`hostPattern`、`settings` 已确认） | ✅ COMPLETE (已为所有 3 个来源类型添加未验证注释) |
| 7 | LOW | 标题计数 | 更新标题从"60+ settings"以匹配添加后的实际表计数 | ❌ INVALID (计数准确 — 60+ settings 和 125 env vars，都在所述范围内) |

---

## [2026-04-01 12:32 PM PKT] Claude Code v2.1.89

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失 Setting | 将 `skipDangerousModePermissionPrompt` 添加到 Permission Keys 表 — 布尔值，跳过 bypass-mode 确认提示。在项目设置中被忽略。已在官方 settings 页面确认 | ✅ COMPLETE (已添加在 Permission Keys 表 disableBypassPermissionsMode 之后) |
| 2 | HIGH | 新 Setting | 将 `showThinkingSummaries` 添加到 General Settings — 布尔值，默认 `false`。Thinking summaries 不再默认生成；设置 `true` 恢复。v2.1.89 changelog — 尚未在官方 settings 页面 | ✅ COMPLETE (已添加在 feedbackSurveyRate 之前，附带 changelog 注释) |
| 3 | HIGH | 行为变更 | 更新 `cleanupPeriodDays` 描述 — v2.1.89 changelog 说 `0` 现在会被验证错误拒绝。矛盾：官方 settings 页面仍将 `0` 描述为有效。标记给用户 | ✅ COMPLETE (描述已更新添加 changelog 和 docs 页面之间的矛盾说明) |
| 4 | HIGH | 缺失环境变量 | 添加约 46 个在官方 /en/env-vars 页面确认的缺失环境变量：`ANTHROPIC_BEDROCK_BASE_URL`、`ANTHROPIC_VERTEX_BASE_URL`、`ANTHROPIC_BETAS`、`ANTHROPIC_VERTEX_PROJECT_ID`、`CLAUDE_CODE_DISABLE_THINKING`、`DISABLE_INTERLEAVED_THINKING`、`ENABLE_PROMPT_CACHING_1H_BEDROCK`、`DISABLE_AUTO_COMPACT`、`DISABLE_COMPACT`、`CLAUDE_CODE_DISABLE_FILE_CHECKPOINTING`、`CLAUDE_CODE_DISABLE_ATTACHMENTS`、`CLAUDE_CODE_DISABLE_CLAUDE_MDS`、`CLAUDE_CODE_GLOB_HIDDEN`、`CLAUDE_CODE_GLOB_NO_IGNORE`、`CLAUDE_CODE_GLOB_TIMEOUT_SECONDS`、`CLAUDE_CODE_DISABLE_OFFICIAL_MARKETPLACE_AUTOINSTALL`、`CLAUDE_CODE_SYNC_PLUGIN_INSTALL`、`CLAUDE_CODE_SYNC_PLUGIN_INSTALL_TIMEOUT_MS`、`CLAUDE_CODE_AUTO_CONNECT_IDE`、`CLAUDE_CODE_IDE_HOST_OVERRIDE`、`CLAUDE_CODE_IDE_SKIP_VALID_CHECK`、`CLAUDE_CODE_MAX_RETRIES`、`API_TIMEOUT_MS`、`CLAUDE_CODE_OTEL_FLUSH_TIMEOUT_MS`、`CLAUDE_CODE_OTEL_SHUTDOWN_TIMEOUT_MS`、`CLAUDE_ENABLE_STREAM_WATCHDOG`、`CLAUDE_CODE_ENABLE_FINE_GRAINED_TOOL_STREAMING`、`CLAUDE_CODE_DEBUG_LOGS_DIR`、`CLAUDE_CODE_DEBUG_LOG_LEVEL`、`CLAUDE_CODE_ACCESSIBILITY`、`CLAUDE_CODE_SYNTAX_HIGHLIGHT`、`CLAUDE_CODE_RESUME_INTERRUPTED_TURN`、`CLAUDE_CODE_MAX_TOOL_USE_CONCURRENCY`、`CLAUDE_CODE_DISABLE_LEGACY_MODEL_REMAP`、`FALLBACK_FOR_ALL_PRIMARY_MODELS`、`CLAUDE_CODE_GIT_BASH_PATH`、`CLAUDE_AUTO_BACKGROUND_TASKS`、`CLAUDE_AGENT_SDK_DISABLE_BUILTIN_AGENTS`、`CLAUDE_AGENT_SDK_MCP_NO_PREFIX`、`DISABLE_DOCTOR_COMMAND`、`DISABLE_LOGIN_COMMAND`、`DISABLE_LOGOUT_COMMAND`、`DISABLE_UPGRADE_COMMAND`、`DISABLE_EXTRA_USAGE_COMMAND`、`DISABLE_INSTALL_GITHUB_APP_COMMAND`、`CLAUDE_CODE_PLUGIN_CACHE_DIR`、`CLAUDE_CODE_SIMPLE` | ✅ COMPLETE (已添加全部 46 个环境变量到表中相关变量附近) |
| 5 | HIGH | 版本更新 | 将报告版本徽章从 v2.1.88 更新到 v2.1.89 | ✅ COMPLETE (徽章和标题已在 Phase 2.6 中更新) |
| 6 | MED | 新环境变量 | 将 `MCP_CONNECTION_NONBLOCKING` 添加到环境变量表 — 在 `-p` 模式设置为 `true` 以跳过 MCP 连接等待。仅 v2.1.89 changelog，尚未在官方 /en/env-vars 页面 | ✅ COMPLETE (已在 CLAUDE_AGENT_SDK_MCP_NO_PREFIX 之后添加，附带 changelog 注释) |
| 7 | MED | 归属边界 | `CLAUDE_CODE_SIMPLE` 在 CLI startup flags 文件中为仅启动时使用，但官方 /en/env-vars 页面列为可配置。协调归属 | ✅ COMPLETE (已添加到 settings 报告环境变量表；更新了 CLI 文件以交叉引用 settings 报告) |
| 8 | MED | 示例更新 | 如果已添加 `showThinkingSummaries`，则更新快速参考示例 | ✅ COMPLETE (在示例中添加了 showThinkingSummaries: true) |

---

## [2026-04-02 09:24 PM PKT] Claude Code v2.1.90

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 类型 + 描述变更 | 修复 `forceLoginOrgUUID`：类型从 `string` 到 `string \| string[]`。扩展描述以包含数组行为（列出任何 org 被接受无需预选）、managed settings 强制执行（账户不在列出 org 中则登录失败）和空数组 fail-closed 行为 | ✅ COMPLETE (类型已更新为 string \| array，描述已扩展包含数组行为、managed 强制执行、fail-closed 语义，示例已更新) |
| 2 | HIGH | 缺失环境变量 | 将 `CLAUDE_CODE_OAUTH_TOKEN`、`CLAUDE_CODE_OAUTH_REFRESH_TOKEN`、`CLAUDE_CODE_OAUTH_SCOPES` 添加到 Common Environment Variables 表。全部已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已在 ANTHROPIC_AUTH_TOKEN 之后添加 3 个 OAuth 环境变量) |
| 3 | HIGH | 描述变更 + 注释 | 更新 `showThinkingSummaries`：移除"(in v2.1.89 changelog, not yet on official settings page)"注释 — 现在已在官方 settings 页面确认。更新描述以匹配官方："When unset or false (default in interactive mode), thinking blocks are redacted by the API and shown as a collapsed stub. Redaction only changes what you see, not what the model generates" | ✅ COMPLETE (注释已移除，描述已更新为匹配官方文档) |
| 4 | HIGH | Sandbox 跨合并 | 更新 `sandbox.filesystem.allowWrite` 描述添加"Also merged with paths from `Edit(...)` allow permission rules"。更新 `denyWrite` 添加"Also merged with paths from `Edit(...)` deny permission rules"。更新 `denyRead` 添加"Also merged with paths from `Read(...)` deny permission rules"。已在官方 settings 页面确认 | ✅ COMPLETE (跨合并行为已添加到所有 3 个 filesystem 条目) |
| 5 | HIGH | 描述变更 | 简化 `cleanupPeriodDays` 描述：移除矛盾说明，与官方文档对齐，现在说"minimum 1, Setting to 0 is rejected with a validation error"。旧行为不再在官方页面记录 | ✅ COMPLETE (矛盾说明已移除，描述已与官方文档对齐，添加了 --no-session-persistence 替代方案) |
| 6 | HIGH | 版本更新 | 将报告版本徽章从 v2.1.89 更新到 v2.1.90 | ✅ COMPLETE (徽章、标题版本和标题文本已更新) |
| 7 | MED | 新环境变量 | 将 `CLAUDE_CODE_PLUGIN_KEEP_MARKETPLACE_ON_FAILURE` 添加到环境变量表 — git pull 失败时保留 marketplace 缓存（v2.1.90 changelog，尚未在官方 /en/env-vars 页面） | ✅ COMPLETE (已在 CLAUDE_CODE_SYNC_PLUGIN_INSTALL_TIMEOUT_MS 之后添加，附带 changelog 注释) |
| 8 | MED | Hook 重定向计数 | 将重定向文本从"all 19 hook events"更新为"all 25 hook events"（按官方 hooks 页面计数） | ✅ COMPLETE (已在 hooks 重定向章节更新计数) |
| 9 | MED | 归属边界 | `CLAUDE_CODE_TMPDIR` 在官方 /en/env-vars 页面上列为可通过 `env` 键配置，但 CLI startup flags 报告列为仅启动时使用。协调归属 | ✅ COMPLETE (已添加到 settings 报告环境变量表；更新了 CLI flags 文件以交叉引用 settings 报告) |

---

## [2026-04-03 08:44 PM PKT] Claude Code v2.1.91

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新 Setting | 将 `disableSkillShellExecution` 添加到 General Settings 表 — 布尔值，禁用 skills、自定义 slash commands 和 plugin commands 中的内联 shell 执行。已在 v2.1.91 changelog 确认。尚未在官方 settings 页面或 JSON schema 中 | ✅ COMPLETE (已添加在 showThinkingSummaries 之后，附带 changelog 注释) |
| 2 | HIGH | 版本更新 | 将报告版本徽章从 v2.1.90 更新到 v2.1.91 | ✅ COMPLETE (徽章和标题已在 Phase 2.6 中更新) |

---

## [2026-04-04 10:48 PM PKT] Claude Code v2.1.92

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新 Setting | 将 `forceRemoteSettingsRefresh` 添加到 General Settings — 布尔值，仅 managed，阻塞 CLI 启动直到远程 managed settings 被新获取（fail-closed）。已在官方 settings 页面确认 | ✅ COMPLETE (已添加在 General Settings 表 feedbackSurveyRate 之前) |
| 2 | HIGH | 缺失环境变量 | 将 `CLAUDE_REMOTE_CONTROL_SESSION_NAME_PREFIX` 添加到 Common Environment Variables 表 — 自动生成的 Remote Control 会话名称的前缀，默认为机器主机名。已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已添加在 CLAUDE_CODE_ENABLE_TELEMETRY 之前) |
| 3 | MED | 描述变更 | 更新 `disableSkillShellExecution` — 移除"(in v2.1.91 changelog, not yet on official settings page)"注释。现在已在官方 settings 页面确认，描述已扩展 | ✅ COMPLETE (注释已移除，描述已按官方文档扩展) |
| 4 | MED | 描述变更 | 移除 marketplace 来源类型 `url`、`npm` 和 `file` 的"not in official docs — unverified"标签。官方 settings 页面现在记录了全部 8 个来源类型 | ✅ COMPLETE (未验证注释已移除 — 从 2026-03-31 重复出现，现已解决) |
| 5 | MED | 描述变更 | 丰富 `cleanupPeriodDays` — 添加"Also controls the age cutoff for automatic removal of orphaned subagent worktrees at startup"（按官方 settings 页面） | ✅ COMPLETE (worktree 清理详情已添加) |
| 6 | MED | 描述变更 | 丰富 `disableDeepLinkRegistration` — 添加通过 `%0A` 的多行提示支持（按官方 settings 页面） | ✅ COMPLETE (多行提示详情已添加) |
| 7 | MED | 描述变更 | 丰富 `includeGitInstructions` — 更新以包含 git status 快照和环境变量优先级（按官方 settings 页面） | ✅ COMPLETE (描述已扩展包含 git status 快照和 CLAUDE_CODE_DISABLE_GIT_INSTRUCTIONS 优先级) |
| 8 | MED | 描述变更 | 丰富 `language` — 添加"Also sets the voice dictation language"（按官方 settings 页面） | ✅ COMPLETE (语音听写详情已添加) |
| 9 | MED | 描述变更 | 丰富 `allowUnsandboxedCommands` — 添加企业策略详情（按官方 settings 页面） | ✅ COMPLETE (已扩展 fail-closed 行为和企业用例) |

---

## [2026-04-08 09:51 PM PKT] Claude Code v2.1.96

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 缺失环境变量 | 将 `CLAUDE_CODE_USE_MANTLE`、`ANTHROPIC_BEDROCK_MANTLE_BASE_URL`、`CLAUDE_CODE_SKIP_MANTLE_AUTH` 添加到 Common Environment Variables 表 — Bedrock Mantle 端点支持（v2.1.94）。全部已在官方 /en/env-vars 页面确认 | ✅ COMPLETE (已添加在相关云提供商变量附近) |
| 2 | HIGH | 默认值变更 | 更新 Effort Level 章节 — 默认值从 Medium 更改为 High（适用于 API-key、Bedrock/Vertex/Foundry、Team 和 Enterprise 用户）（v2.1.94）。更新表默认标记和历史说明 | ✅ COMPLETE (表已更新 High 为默认值，历史说明已扩展包含 v2.1.94 变更) |
| 3 | HIGH | 版本更新 | 将报告版本徽章从 v2.1.92 更新到 v2.1.96 | ✅ COMPLETE (徽章、标题版本和标题文本已在 Phase 2.6 中更新) |
| 4 | MED | 过时注释 | 从 `CLAUDE_CODE_PLUGIN_KEEP_MARKETPLACE_ON_FAILURE` 移除"(in v2.1.90 changelog, not yet on official env-vars page)" — 现在已在官方 /en/env-vars 页面确认。更新描述以匹配官方措辞 | ✅ COMPLETE (注释已移除，描述已按官方文档更新) |
| 5 | MED | 描述变更 | 更新 `CLAUDE_CODE_GLOB_HIDDEN` 描述以匹配官方："Set to `false` to exclude dotfiles from Glob results. Included by default. Does not affect `@` file autocomplete, `ls`, Grep, or Read" | ✅ COMPLETE (描述已按官方 env-vars 页面重写) |
| 6 | MED | 描述变更 | 更新 `CLAUDE_CODE_GLOB_NO_IGNORE` 描述以匹配官方："Set to `false` to make the Glob tool respect `.gitignore` patterns. By default, Glob returns all matching files including gitignored ones. Does not affect `@` file autocomplete" | ✅ COMPLETE (描述已按官方 env-vars 页面重写) |
| 7 | MED | 描述变更 | 更新 `editorMode` 描述 — 移除过时的 `/vim` 引用（v2.1.94 中已移除），将配置标签从"Key binding mode"更改为"Editor mode"（按官方文档） | ✅ COMPLETE (已移除 /vim 引用，配置标签已更新) |
