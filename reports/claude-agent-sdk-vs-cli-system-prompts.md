# Claude Agent SDK vs Claude CLI：系统提示和输出一致性

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

![SDK vs CLI 系统提示图](../assets/sdk-vs-cli-diagram.svg)

---

## 摘要

当通过 **Claude Agent SDK** 与 **Claude CLI (Claude Code)** 发送相同消息（例如"挪威的首都是什么？"）时，伴随这些消息的系统提示根本不同。CLI 使用**模块化系统提示架构**（约 269 个基础 token，加上根据功能条件加载的额外上下文），而 SDK 默认使用最小化提示。**两者之间无法保证输出一致**，即使配置匹配也是如此，因为缺少 seed 参数以及 Claude 架构中固有的非确定性。

---

## 1. 系统提示对比

### Claude CLI (Claude Code)

Claude CLI 使用**模块化系统提示架构**，约 269 token 的基础提示，附带条件加载的额外上下文：

| 组件 | 描述 | 加载方式 |
|-----------|-------------|---------|
| **基础系统提示** | 核心指令和行为 | 始终加载（~269 token） |
| **工具指令** | 18+ 个内置工具（Write、Read、Edit、Bash、TodoWrite 等） | 始终加载 |
| **编码指南** | 代码风格、格式规则、安全实践 | 始终加载 |
| **安全规则** | 拒绝规则、注入防御、伤害预防 | 始终加载 |
| **响应风格** | 语调、详细程度、解释深度、表情符号使用 | 始终加载 |
| **环境上下文** | 工作目录、git 状态、平台信息 | 始终加载 |
| **项目上下文** | CLAUDE.md 内容、设置、钩子配置 | 条件加载 |
| **Subagent 提示** | Plan 模式、Explore agent、Task agent | 条件加载 |
| **安全审查** | 扩展安全指令（~2,610 token） | 条件加载 |

**关键特征：**
- **模块化架构**，有 110+ 个系统提示字符串条件加载
- 基础提示适中（~269 token），总量根据激活的功能而变化
- 包含广泛的安全和注入防御层
- 自动加载工作目录中的 CLAUDE.md 文件
- 交互模式中会话持久化的上下文

### Claude Agent SDK

Agent SDK 默认使用**最小化系统提示**，包含：

| 组件 | 描述 | Token 影响 |
|-----------|-------------|--------------|
| **基本工具指令** | 仅显式提供的工具 | 最小化 |
| **基本安全** | 最小安全指令 | 最小化 |

**关键特征：**
- 默认没有编码指南或风格偏好
- 除非显式配置，否则没有项目上下文
- 没有广泛的工具描述
- 需要显式配置才能匹配 CLI 行为

---

## 2. 每个接口发送的内容

### 示例："挪威的首都是什么？"

#### 通过 Claude CLI

```
System Prompt: [模块化，约 269+ 基础 token]
├── 基础系统提示（~269 token）
├── 工具指令（Write、Read、Edit、Bash、Grep、Glob 等）
├── Git 安全协议
├── 代码参考指南
├── 专业客观性指令
├── 安全和注入防御规则
├── 环境上下文（操作系统、目录、日期）
├── CLAUDE.md 内容（如果存在）[条件加载]
├── MCP 工具描述（如果配置）[条件加载]
├── Plan/Explore 模式提示 [条件加载]
└── 会话/对话上下文

User Message: "挪威的首都是什么？"
```

#### 通过 Agent SDK（默认）

```
System Prompt: [最小化]
├── 基本工具指令（如果提供了工具）
└── 基本操作上下文

User Message: "挪威的首都是什么？"
```

#### 通过 Agent SDK（使用 `claude_code` 预设）

```typescript
const response = await query({
  prompt: "挪威的首都是什么？",
  options: {
    systemPrompt: {
      type: "preset",
      preset: "claude_code"
    }
  }
});
```

```
System Prompt: [模块化，匹配 CLI]
├── 完整的 Claude Code 系统提示
├── 工具指令
├── 编码指南
└── 安全规则

// 注意：仍然不包含 CLAUDE.md，除非配置了 settingSources
```

---

## 3. 自定义方法

### Claude CLI 自定义

| 方法 | 命令 | 效果 |
|--------|---------|--------|
| **追加到提示** | `claude -p "..." --append-system-prompt "..."` | 在保留默认值的同时添加指令 |
| **替换提示** | `claude -p "..." --system-prompt "..."` | 完全替换系统提示 |
| **项目上下文** | CLAUDE.md 文件 | 自动加载，持久化 |
| **输出样式** | `/output-style [名称]` | 应用预定义的响应样式 |

### Agent SDK 自定义

| 方法 | 配置 | 效果 |
|--------|---------------|--------|
| **自定义提示** | `systemPrompt: "..."` | 完全替换默认值（丢失工具） |
| **预设 + 追加** | `systemPrompt: { type: "preset", preset: "claude_code", append: "..." }` | 保留 CLI 功能 + 自定义指令 |
| **CLAUDE.md 加载** | `settingSources: ["project"]` | 加载项目级别指令 |
| **输出样式** | `settingSources: ["user"]` 或 `settingSources: ["project"]` | 加载已保存的输出样式 |

### 配置对比表

| 功能 | CLI 默认 | SDK 默认 | SDK 预设 |
|---------|-------------|-------------|-----------------|
| 工具指令 | ✅ 完整 | ❌ 最小化 | ✅ 完整 |
| 编码指南 | ✅ 有 | ❌ 无 | ✅ 有 |
| 安全规则 | ✅ 有 | ❌ 基础 | ✅ 有 |
| CLAUDE.md 自动加载 | ✅ 有 | ❌ 无 | ❌ 无* |
| 项目上下文 | ✅ 自动 | ❌ 无 | ❌ 无* |

*需要显式配置 `settingSources: ["project"]`

---

## 4. 输出一致性保证

### 关键发现：无确定性保证

**Claude Messages API 不提供用于可复现性的 seed 参数。** 这是一个根本的架构限制。

### 阻止完全相同输出的因素

| 因素 | 描述 | 可控？ |
|--------|-------------|---------------|
| **不同的系统提示** | CLI vs SDK 有不同的默认值 | ✅ 是（通过配置） |
| **浮点运算** | 并行硬件的怪异行为 | ❌ 否 |
| **MoE 路由** | 混合专家架构的变化 | ❌ 否 |
| **批处理/调度** | 云基础设施差异 | ❌ 否 |
| **数值精度** | 推理引擎变化 | ❌ 否 |
| **模型快照** | 版本更新/更改 | ❌ 否 |

### 温度和采样

即使使用 `temperature=0.0`（贪婪解码）：
- 完全确定性**无法保证**
- 由于基础设施因素，仍可能出现微小变化
- 已知 bug：[Claude CLI 对相同输入产生非确定性输出](https://github.com/anthropics/claude-code/issues/3370)

---

## 5. 实现最大一致性

要在 SDK 和 CLI 之间获得**尽可能接近**的相同输出：

### Agent SDK 配置

```typescript
import Anthropic from "@anthropic-ai/sdk";

const client = new Anthropic();

// 选项 1：使用 claude_code 预设
const response = await client.messages.create({
  model: "claude-sonnet-4-20250514",
  max_tokens: 1024,
  // 尽可能匹配 CLI 系统提示
  system: "你的精确系统提示匹配 CLI",
  messages: [
    { role: "user", content: "挪威的首都是什么？" }
  ],
  // 使用贪婪解码以获得最大一致性
  temperature: 0
});

// 选项 2：使用 Agent SDK query 函数
import { query } from "@anthropic-ai/agent-sdk";

for await (const message of query({
  prompt: "挪威的首都是什么？",
  options: {
    systemPrompt: {
      type: "preset",
      preset: "claude_code"
    },
    temperature: 0,
    model: "claude-sonnet-4-20250514",
    // 像 CLI 一样加载项目上下文
    settingSources: ["project"]
  }
})) {
  // 处理响应
}
```

### CLI 配置

```bash
# 尽可能匹配 SDK 配置
claude -p "挪威的首都是什么？" \
  --model claude-sonnet-4-20250514 \
  --temperature 0
```

### 仍然无法保证

即使配置完美匹配：
- 不同运行之间输出可能不同
- SDK 和 CLI 之间输出可能不同
- 不存在 seed 参数来强制可复现性

---

## 6. 实际影响

### 何时使用哪个接口

| 用例 | 推荐接口 | 原因 |
|----------|----------------------|--------|
| 交互式开发 | Claude CLI | 完整工具套件、项目上下文 |
| 编程集成 | Agent SDK | 细粒度控制、嵌入 |
| 一致的 API 响应 | Agent SDK + 自定义提示 | 更好地控制系统提示 |
| 批量处理 | Agent SDK | 更适合自动化流水线 |
| 一次性任务 | Claude CLI | 更快的设置、即时上下文 |

### 设计建议

1. **不要依赖逐位可复现性**
   - 构建对微小输出变化鲁棒的应用
   - 使用结构化输出和验证

2. **对于需要一致性的生产流水线：**
   - 尽可能缓存结果
   - 使用带有 JSON schema 验证的结构化输出
   - 结合确定性逻辑和验证
   - 考虑使用多次生成和共识机制

3. **在 SDK 中匹配 CLI 行为：**
   ```typescript
   systemPrompt: {
     type: "preset",
     preset: "claude_code",
     append: "你的额外指令"
   },
   settingSources: ["project", "user"]
   ```

---

## 7. 系统提示 Token 影响

| 配置 | 架构 | 说明 |
|---------------|-------------|-------|
| SDK（最小化） | 最小化默认 | 仅基本工具指令 |
| SDK（claude_code 预设） | 模块化（~269+ 基础） | 匹配 CLI，根据功能变化 |
| CLI（默认） | 模块化（~269+ 基础） | 额外上下文条件加载 |
| CLI（带 MCP 工具） | 模块化 + MCP | MCP 工具描述增加大量 token |

**注意：** Claude Code 使用模块化架构，有 110+ 个系统提示字符串。基础提示约 269 token，各个组件根据激活的功能从 18 到 2,610 token 不等。

**含义：** SDK 的最小化默认值给你更多实际任务的上下文空间，但代价是失去 Claude Code 的完整功能。

---

## 8. 总结表

| 方面 | Claude CLI | Agent SDK（默认） | Agent SDK（预设） |
|--------|------------|--------------------|--------------------|
| **系统提示** | 模块化（~269+ 基础） | 最小化 | 模块化（匹配 CLI） |
| **包含工具** | 18+ 内置 | 仅如果提供 | 18+ 内置 |
| **CLAUDE.md 自动加载** | 是 | 否 | 否（需要配置） |
| **编码指南** | 是 | 否 | 是 |
| **安全规则** | 完整 | 基础 | 完整 |
| **温度控制** | 是 | 是 | 是 |
| **确定性保证** | 否 | 否 | 否 |
| **输出一致？** | 不适用 | 否（vs CLI） | 更接近，但仍否 |

---

## 9. 结论

**问：SDK vs CLI 中相同消息伴随什么系统提示？**

CLI 使用**模块化系统提示架构**，约 269 token 基础提示和 110+ 个条件加载组件（工具指令、编码指南、安全规则、项目上下文）。SDK 使用**最小化默认值**，仅包含基本工具指令，但可以使用 `claude_code` 预设配置为匹配 CLI 行为。

**问：是否有输出一致的保证？**

**没有。** 即使系统提示匹配、输入相同且 `temperature=0`，也无法保证输出一致，原因包括：
- Claude API 中缺少 seed 参数
- 浮点运算变化
- 基础设施级别的非确定性
- 模型架构（混合专家）路由变化

**建议：** 设计对输出变化鲁棒的系统，而不是依赖确定性行为。对于一致性关键的应用，使用结构化输出、缓存和验证层。

---

## 来源

- [修改系统提示 - Agent SDK](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/sdk#modifying-system-prompts)
- [Claude Code CLI 参考](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/cli)
- [Claude Code Headless 模式](https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/headless)
- [Claude Code 最佳实践 - Anthropic 工程](https://www.anthropic.com/engineering/claude-code-best-practices)
- [Claude Messages API 参考](https://docs.anthropic.com/en/api/messages)
- [GitHub Issue #3370: 非确定性输出](https://github.com/anthropics/claude-code/issues/3370)
- [Claude Code 系统提示仓库](https://github.com/Piebald-AI/claude-code-system-prompts) - 模块化提示架构分析
- [为什么 LLM 的确定性输出几乎不可能](https://unstract.com/blog/understanding-why-deterministic-output-from-llms-is-nearly-impossible/)

---

*本报告由 Claude Code 使用 Opus 4.5 模型于 2026 年 2 月 3 日生成。*
