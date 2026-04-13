# 理解大型 Monorepo 中 Claude Skills 的发现机制

在 Monorepo 中使用 Claude Code 时，理解 Skills 如何被发现和加载到上下文中，对于有效组织项目特定能力至关重要。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

## 与 CLAUDE.md 的重要区别

**Skills 不具有与 CLAUDE.md 文件相同的加载行为。** CLAUDE.md 文件沿目录树向上遍历（祖先加载），而 Skills 使用一种不同的发现机制，专注于项目内的嵌套目录。

## Skills 如何被发现

### 1. 标准 Skill 位置

Skills 根据作用域从固定位置加载：

| 位置 | 路径 | 适用范围 |
|----------|------|------------|
| 企业级 | 托管设置 | 组织中的所有用户 |
| 个人级 | `~/.claude/skills/<skill-name>/SKILL.md` | 你的所有项目 |
| 项目级 | `.claude/skills/<skill-name>/SKILL.md` | 仅此项目 |
| 插件级 | `<plugin>/skills/<skill-name>/SKILL.md` | 插件启用的地方 |

### 2. 嵌套目录的自动发现

当你在子目录中编辑文件时，Claude Code 会自动从嵌套的 `.claude/skills/` 目录中发现 Skills。例如，如果你正在编辑 `packages/frontend/` 中的文件，Claude Code 也会在 `packages/frontend/.claude/skills/` 中查找 Skills。

这支持每个包有自己的 Skills 的 Monorepo 设置。

## Monorepo 结构示例

考虑一个典型的包独立的 Monorepo：

```
/mymonorepo/
├── .claude/
│   └── skills/
│       └── shared-conventions/SKILL.md    # 项目级 Skill
├── packages/
│   ├── frontend/
│   │   ├── .claude/
│   │   │   └── skills/
│   │   │       └── react-patterns/SKILL.md  # 前端特定 Skill
│   │   └── src/
│   │       └── App.tsx
│   ├── backend/
│   │   ├── .claude/
│   │   │   └── skills/
│   │   │       └── api-design/SKILL.md      # 后端特定 Skill
│   │   └── src/
│   └── shared/
│       ├── .claude/
│       │   └── skills/
│       │       └── utils-patterns/SKILL.md  # 共享工具 Skill
│       └── src/
```

## 场景 1：刚在根目录启动 Claude（尚未编辑文件）

当你在 `/mymonorepo/` 运行 Claude Code 且尚未编辑任何文件时：

```bash
cd /mymonorepo
claude
# 刚启动 - 尚未编辑任何文件
```

| Skill | 在上下文中？ | 原因 |
|-------|-------------|--------|
| `shared-conventions` | **是** | 根 `.claude/skills/` 中的项目级 Skill |
| `react-patterns` | **否** | 未发现 - 尚未处理 `packages/frontend/` 中的文件 |
| `api-design` | **否** | 未发现 - 尚未处理 `packages/backend/` 中的文件 |
| `utils-patterns` | **否** | 未发现 - 尚未处理 `packages/shared/` 中的文件 |

## 场景 2：编辑了包中的文件之后

在让 Claude 编辑 `packages/frontend/src/App.tsx` 之后：

| Skill | 在上下文中？ | 原因 |
|-------|-------------|--------|
| `shared-conventions` | **是** | 根 `.claude/skills/` 中的项目级 Skill |
| `react-patterns` | **是** | 编辑 `packages/frontend/` 中的文件时发现 |
| `api-design` | **否** | 仍未发现 - 尚未处理 `packages/backend/` 中的文件 |
| `utils-patterns` | **否** | 仍未发现 - 尚未处理 `packages/shared/` 中的文件 |

**关键洞察**：嵌套 Skills 在你处理这些目录中的文件时**按需发现**。它们不会在会话启动时预加载。

## 关键行为：描述 vs 完整内容

Skill 描述会被加载到上下文中，以便 Claude 知道有哪些可用的，但**完整内容仅在调用时加载**。这是一个重要的优化：

- **描述**：始终在上下文中（在字符预算内）
- **完整内容**：在 Skill 被调用时按需加载

> 注意：预加载了 Skills 的 Subagent 工作方式不同 — 完整 Skill 内容在启动时注入。

## 优先级顺序（当 Skills 同名时）

当 Skills 在不同层级同名时，高优先级位置获胜：

| 优先级 | 位置 | 作用域 |
|----------|----------|-------|
| 1（最高） | 企业级 | 组织范围 |
| 2 | 个人级（`~/.claude/skills/`） | 你的所有项目 |
| 3（最低） | 项目级（`.claude/skills/`） | 仅此项目 |

插件 Skills 使用 `plugin-name:skill-name` 命名空间，因此不会与其他层级冲突。

## 为什么这种设计适合 Monorepo

- **包特定 Skills 保持隔离** — 在 `packages/frontend/` 工作的前端开发者获得前端特定 Skills，不会被后端 Skills 弄乱上下文。

- **自动发现减少配置** — 无需显式注册包级 Skills；在你处理这些目录中的文件时会自动发现。

- **上下文得到优化** — 最初只加载 Skill 描述，嵌套 Skills 按需发现。

- **团队可以维护自己的 Skills** — 每个包团队可以定义自己领域特定的 Skills，无需与其他团队协调。

## 字符预算注意事项

Skill 描述加载到上下文中，有字符预算限制（默认 15,000 字符）。在有许多包和 Skills 的大型 Monorepo 中，你可能会达到此限制。

- 运行 `/context` 检查关于被排除 Skills 的警告
- 设置 `SLASH_COMMAND_TOOL_CHAR_BUDGET` 环境变量来增加限制

## 最佳实践

1. **将共享工作流放在根 `.claude/skills/`** — 仓库范围的约定、提交工作流和共享模式。

2. **将包特定 Skills 放在包 `.claude/skills/`** — 框架特定模式、组件约定、该包独有的测试工具。

3. **对危险 Skills 使用 `disable-model-invocation: true`** — 部署或破坏性 Skills 应需要显式用户调用。

4. **保持 Skill 描述简洁** — 描述始终在上下文中（在字符预算内），冗长的描述浪费上下文空间。

5. **在 Skill 名称中使用命名空间** — 考虑用包名作为前缀（如 `frontend-review`、`backend-deploy`）以避免混淆。

## 对比：Skills vs CLAUDE.md 加载

| 行为 | CLAUDE.md | Skills |
|----------|-----------|--------|
| 祖先加载（沿目录树向上） | 是 | 否 |
| 嵌套/后代发现（沿目录树向下） | 是（懒加载） | 是（自动发现） |
| 全局位置 | `~/.claude/CLAUDE.md` | `~/.claude/skills/` |
| 项目位置 | `.claude/` 或仓库根目录 | `.claude/skills/` |
| 内容加载 | 完整内容 | 仅描述（调用时加载完整内容） |

---

## 来源

- [Claude Code 文档 - 用 Skills 扩展 Claude](https://code.claude.com/docs/en/skills)
- [Claude Code 文档 - 嵌套目录的自动发现](https://code.claude.com/docs/en/skills#automatic-discovery-from-nested-directories)
