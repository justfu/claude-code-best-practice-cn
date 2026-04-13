# Commands 报告 — 变更历史

## 状态说明

| 状态 | 含义 |
|------|------|
| ✅ `COMPLETE (原因)` | 操作已执行并成功解决 |
| ❌ `INVALID (原因)` | 发现不正确、不适用或为有意为之 |
| ✋ `ON HOLD (原因)` | 操作已推迟 — 等待外部依赖或用户决定 |

---

## [2026-03-13 04:23 PM PKT] Claude Code v2.1.74

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新字段 | 添加 `name` 到 frontmatter 表 — skill 的显示名称 | ❌ INVALID (仅限 skill 的字段，不适用于 commands frontmatter) |
| 2 | HIGH | 新字段 | 添加 `disable-model-invocation` 到 frontmatter 表 — 防止自动加载 | ❌ INVALID (仅限 skill 的字段，不适用于 commands frontmatter) |
| 3 | HIGH | 新字段 | 添加 `user-invocable` 到 frontmatter 表 — 从 `/` 菜单中隐藏 | ❌ INVALID (仅限 skill 的字段，不适用于 commands frontmatter) |
| 4 | HIGH | 新字段 | 添加 `context` 到 frontmatter 表 — fork 以在 subagent 上下文中运行 | ❌ INVALID (仅限 skill 的字段，不适用于 commands frontmatter) |
| 5 | HIGH | 新字段 | 添加 `agent` 到 frontmatter 表 — context: fork 的 subagent 类型 | ❌ INVALID (仅限 skill 的字段，不适用于 commands frontmatter) |
| 6 | HIGH | 新字段 | 添加 `hooks` 到 frontmatter 表 — 限定于 skill 的生命周期 hooks | ❌ INVALID (仅限 skill 的字段，不适用于 commands frontmatter) |
| 7 | HIGH | 新命令 | 添加 `/btw <question>` — 快速提问而不添加到对话中 | ✅ COMPLETE (添加为 Session 标签中的 #53) |
| 8 | HIGH | 新命令 | 添加 `/hooks` — 管理工具事件的 hook 配置 | ✅ COMPLETE (添加为 Extensions 标签中的 #30) |
| 9 | HIGH | 新命令 | 添加 `/insights` — 生成会话分析报告 | ✅ COMPLETE (添加为 Context 标签中的 #17) |
| 10 | HIGH | 新命令 | 添加 `/plugin` — 管理 Claude Code 插件 | ✅ COMPLETE (添加为 Extensions 标签中的 #33) |
| 11 | HIGH | 新命令 | 添加 `/skills` — 列出可用 skills | ✅ COMPLETE (添加为 Extensions 标签中的 #35) |
| 12 | HIGH | 新命令 | 添加 `/upgrade` — 打开升级页面切换计划层级 | ✅ COMPLETE (添加为 Auth 标签中的 #3) |
| 13 | HIGH | 移除命令 | 移除 `/output-style` — v2.1.73 中已弃用，请使用 `/config` | ✅ COMPLETE (从 Config 标签中移除) |
| 14 | HIGH | 移除命令 | 移除 `/bug` 行 — 现在列为 `/feedback` 下的别名 | ✅ COMPLETE (移除该行，在 /feedback 描述中添加"Alias: /bug") |
| 15 | HIGH | 描述变更 | 更新 `/passes` — 从审核通过改为推荐分享 | ✅ COMPLETE (更新描述，保留在 Model 标签中) |
| 16 | HIGH | 描述变更 | 更新 `/review` — 已弃用，被 `code-review` marketplace 插件替代 | ✅ COMPLETE (更新 Project 标签中的描述) |
| 17 | MED | 描述变更 | 更新 `/stickers` — 从 UI 贴纸包更改为订购实物贴纸 | ✅ COMPLETE (更新 Config 标签中的描述) |

---

## [2026-03-15 12:50 PM PKT] Claude Code v2.1.76

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新命令 | 添加 `/color [color\|default]` 到 Config 标签 — 设置当前会话的提示栏颜色 | ✅ COMPLETE (添加为 Config 标签中的 #4) |
| 2 | HIGH | 新命令 | 添加 `/effort [low\|medium\|high\|max\|auto]` 到 Model 标签 — 设置 model effort 级别 | ✅ COMPLETE (添加为 Model 标签中的 #38) |
| 3 | MED | 描述变更 | 更新 `/status` — 改为"打开 Settings 界面（Status 标签）"而非"显示简洁的会话状态摘要" | ✅ COMPLETE (更新 Context 标签中 #20 的描述) |
| 4 | MED | 描述变更 | 更新 `/desktop` — 改为"在 Claude Code Desktop 应用中继续当前会话。仅限 macOS 和 Windows。" | ✅ COMPLETE (更新 Remote 标签中 #49 的描述) |
| 5 | LOW | 参数变更 | 更新 `/init` — 官方文档移除了 `[prompt]` 参数提示 | ✅ COMPLETE (移除 Project 标签中 #45 的 [prompt] 提示) |

---

## [2026-03-17 12:45 PM PKT] Claude Code v2.1.77

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新别名 | 在 `/fork` 条目中添加 `Alias: /branch`（v2.1.77 将 fork 重命名为 branch） | ✅ COMPLETE (在 Session 标签中 #59 的 /fork 处添加了"Alias: /branch") |
| 2 | HIGH | 新别名组 | 为 8 个命令添加别名：`/clear`（+/reset、/new）、`/config`（+/settings）、`/desktop`（+/app）、`/exit`（+/quit）、`/rewind`（+/checkpoint）、`/resume`（+/continue）、`/remote-control`（+/rc）、`/mobile`（+/ios、/android） | ✅ COMPLETE (在所有 8 个命令描述中添加了别名标记) |
| 3 | MED | 描述变更 | 更新 `/diff` — "打开交互式 diff 查看器，显示未提交的更改和每轮 diff" | ✅ COMPLETE (更新 Project 标签中 #44 的描述) |
| 4 | MED | 描述变更 | 更新 `/memory` — "编辑 CLAUDE.md 记忆文件，启用或禁用自动记忆，查看自动记忆条目" | ✅ COMPLETE (更新 Memory 标签中 #37 的描述) |
| 5 | MED | 描述变更 | 更新 `/copy` — "将最后的助手回复复制到剪贴板。显示代码块的交互式选择器" | ✅ COMPLETE (更新 Export 标签中 #27 的描述) |
| 6 | MED | 描述变更 | 更新 `/mobile` — "显示二维码以下载 Claude 移动应用" | ✅ COMPLETE (更新 Remote 标签中 #52 的描述和别名) |
| 7 | MED | 描述变更 | 更新 `/remote-control` — "使此会话可从 claude.ai 远程控制" | ✅ COMPLETE (更新 Remote 标签中 #53 的描述和别名) |
| 8 | LOW | Frontmatter 范围 | 6 个仅限 skill 的字段仍不在报告中（有意的范围限定） | ❌ INVALID (仅限 skill 的字段 — 与 v2.1.74 运行的判断相同) |

---

## [2026-03-18 11:38 PM PKT] Claude Code v2.1.78

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新命令 | 添加 `/voice` 到 Config 标签 — 切换按住说话语音听写 | ✅ COMPLETE (添加为 Config 标签中的 #15) |
| 2 | HIGH | 别名反转 | 将 `/fork` → `/branch` 互换为主名称，`/fork` 作为别名 | ✅ COMPLETE (在 Session 标签中 #56 处互换为 `/branch`，按字母顺序重新排列) |
| 3 | MED | 新别名 | 为 `/permissions` 添加 `/allowed-tools` 别名 | ✅ COMPLETE (在 Config 标签中 #7 处添加别名) |
| 4 | MED | 新参数 | 为 `/copy` 添加 `[N]` 参数语法 | ✅ COMPLETE (更新 Export 标签中 #28 为 `/copy [N]`) |
| 5 | LOW | Frontmatter 范围 | 6 个仅限 skill 的字段不在报告中（有意的范围限定） | ❌ INVALID (仅限 skill 的字段 — 与 v2.1.74 和 v2.1.77 运行的判断相同) |

---

## [2026-03-19 11:54 AM PKT] Claude Code v2.1.79

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | LOW | Frontmatter 范围 | 6 个仅限 skill 的字段不在报告中（有意的范围限定） | ❌ INVALID (仅限 skill 的字段 — 与 v2.1.74、v2.1.77 和 v2.1.78 运行的判断相同) |

---

## [2026-03-20 08:33 AM PKT] Claude Code v2.1.80

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | MED | 新字段 | 将 `effort` 添加到 frontmatter 表 — 命令调用时覆盖 model effort 级别（v2.1.80） | ✅ COMPLETE (添加为第 5 个字段，然后在完整字段集添加后重新定位到第 8 个) |
| 2 | HIGH | QA 修正 | 添加 6 个缺失的字段（`name`、`disable-model-invocation`、`user-invocable`、`context`、`agent`、`hooks`）— 官方文档说明 commands 支持"与 skills 相同的 frontmatter"；之前的 INVALID 判断（v2.1.74–v2.1.79）是错误的 | ✅ COMPLETE (添加了全部 6 个字段，计数更新 5 → 11，字段顺序与官方文档匹配) |
| 3 | HIGH | 跨报告修复 | 将 `effort` 添加到 skills 报告（`claude-skills.md`）— 该字段在那里也缺失 | ✅ COMPLETE (添加为 skills 报告中的第 8 个字段，计数更新 10 → 11) |

---

## [2026-03-21 09:08 PM PKT] Claude Code v2.1.81

无优先操作项 — 报告与官方文档完全同步（11 个 frontmatter 字段，63 个内置命令）。

---

## [2026-03-23 09:48 PM PKT] Claude Code v2.1.81

无优先操作项 — 报告与官方文档完全同步（11 个 frontmatter 字段，63 个内置命令）。

---

## [2026-03-25 08:07 PM PKT] Claude Code v2.1.83

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新命令 | 添加 `/schedule [description]` 到 Remote 标签 — 创建、更新、列出或运行 Cloud 定时任务 | ✅ COMPLETE (添加为 Remote 标签中的 #56，计数更新 63 → 64) |

---

## [2026-03-26 01:01 PM PKT] Claude Code v2.1.84

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新字段 | 添加 `shell` 到 frontmatter 表 — `!command` 块的 shell（`bash` 或 `powershell`） | ✅ COMPLETE (添加为第 12 个字段（在 `hooks` 之前），计数更新 11 → 12) |
| 2 | LOW | 参数变更 | 为 `/fast` 命令添加 `[on\|off]` 参数提示 | ✅ COMPLETE (更新 Model 标签中 #40 的 `/fast` 为 `/fast [on\|off]`) |

---

## [2026-03-27 06:25 PM PKT] Claude Code v2.1.85

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新字段 | 添加 `paths` 到 frontmatter 表 — 限制 skill 激活条件的 glob 模式 | ✅ COMPLETE (添加为 `user-invocable` 之后的第 6 个字段，计数更新 12 → 13) |

---

## [2026-03-28 06:05 PM PKT] Claude Code v2.1.86

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | MED | 参数变更 | 更新 `/add-dir` — 按官方文档添加 `<path>` 必需参数提示 | ✅ COMPLETE (更新 Project 标签中 #44) |
| 2 | MED | 参数变更 | 更新 `/branch` — 按官方文档添加 `[name]` 可选参数提示 | ✅ COMPLETE (更新 Session 标签中 #57) |
| 3 | MED | 参数变更 | 更新 `/model` — 按官方文档添加 `[model]` 可选参数提示 | ✅ COMPLETE (更新 Model 标签中 #41) |
| 4 | MED | 参数变更 | 更新 `/plan` — 按官方文档添加 `[description]` 可选参数提示 | ✅ COMPLETE (更新 Model 标签中 #43) |
| 5 | MED | 参数变更 | 更新 `/pr-comments` — 按官方文档添加 `[PR]` 可选参数提示 | ✅ COMPLETE (更新 Project 标签中 #47) |
| 6 | MED | 参数变更 | 更新 `/passes` — 移除 `[number]` 参数提示（官方文档中没有） | ✅ COMPLETE (更新 Model 标签中 #42) |
| 7 | MED | 参数变更 | 更新 `/rename` — 按官方文档从 `<name>`（必需）更改为 `[name]`（可选） | ✅ COMPLETE (更新 Session 标签中 #62) |
| 8 | LOW | 参数变更 | 更新 `/compact` — 按官方文档将参数标签从 `[prompt]` 更改为 `[instructions]` | ✅ COMPLETE (更新 Session 标签中 #60) |
| 9 | LOW | 参数变更 | 更新 `/feedback` — 按官方文档将参数标签从 `[description]` 更改为 `[report]` | ✅ COMPLETE (更新 Debug 标签中 #24) |

---

## [2026-03-31 06:55 PM PKT] Claude Code v2.1.88

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | MED | 描述同步 | 同步所有 43 个命令描述以匹配官方文档 — 行为澄清（`/vim` 切换、`/sandbox` 切换、`/hooks` 查看）、扩展细节（`/effort` 持久性、`/copy` SSH 写入、`/model` effort 箭头）以及 Auth、Config、Context、Debug、Export、Extensions、Model、Project、Remote 和 Session 标签间的措辞对齐 | ✅ COMPLETE (所有 64 个描述现在与 code.claude.com/docs/en/commands 官方文档匹配) |

---

## [2026-04-01 12:26 PM PKT] Claude Code v2.1.89

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | LOW | 描述变更 | 更新 `/init` — 官方文档现在使用 `CLAUDE_CODE_NEW_INIT=1` 而非 `=true` | ✅ COMPLETE (将环境变量值从 `=true` 更新为 `=1` 以匹配官方文档) |

---

## [2026-04-02 09:14 PM PKT] Claude Code v2.1.90

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | MED | 描述变更 | 更新 `/permissions` — 官方文档扩展了描述，包括 scope 规则的交互式对话框、目录管理和自动模式拒绝审查 | ✅ COMPLETE (更新描述以匹配官方文档) |
| 2 | MED | 新别名 | 按官方文档为 `/tasks` 命令添加 `/bashes` 别名 | ✅ COMPLETE (在 Debug 标签中 #27 的 /tasks 处添加"Alias: /bashes") |

---

## [2026-04-03 08:34 PM PKT] Claude Code v2.1.91

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新命令 | 添加 `/powerup` 到 Config 标签 — 通过带有动画演示的快速交互式课程发现 Claude Code 功能 | ✅ COMPLETE (添加为 Debug 标签中的 #26 — 在 v2.1.92 运行中解决) |

---

## [2026-04-04 10:40 PM PKT] Claude Code v2.1.92

| # | 优先级 | 类型 | 操作 | 状态 |
|---|--------|------|------|------|
| 1 | HIGH | 新命令 | 添加 `/powerup` 到 Debug 标签 — 通过带有动画演示的快速交互式课程发现 Claude Code 功能 | ✅ COMPLETE (添加为 Debug 标签中的 #26，从 v2.1.91 重复出现) |
| 2 | HIGH | 新命令 | 添加 `/setup-bedrock` 到 Auth 标签 — 通过交互式向导配置 Amazon Bedrock 认证、区域和 model 固定 | ✅ COMPLETE (添加为 Auth 标签中的 #3) |
| 3 | HIGH | 新命令 | 添加 `/ultraplan <prompt>` 到 Model 标签 — 在 ultraplan 会话中起草计划，在浏览器中审查，然后远程执行或发回 | ✅ COMPLETE (添加为 Model 标签中的 #45) |
| 4 | HIGH | 移除命令 | 从 Config 标签移除 `/vim` — v2.1.92 中已移除（max-version: 2.1.91），请使用 `/config` Editor 模式替代 | ✅ COMPLETE (从 Config 标签中移除) |
| 5 | HIGH | 移除命令 | 从 Project 标签移除 `/pr-comments [PR]` — v2.1.91 中已移除（max-version: 2.1.90），请直接询问 Claude | ✅ COMPLETE (从 Project 标签中移除) |
| 6 | MED | 描述变更 | 更新 `/release-notes` — 现为"在交互式版本选择器中查看 changelog。选择特定版本查看其发布说明，或选择显示所有版本。" | ✅ COMPLETE (更新 Debug 标签中 #27 的描述) |

---

## [2026-04-08 09:35 PM PKT] Claude Code v2.1.96

无优先操作项 — 报告与官方文档完全同步（13 个 frontmatter 字段，65 个内置命令）。
