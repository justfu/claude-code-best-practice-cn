创建一个 agent 团队来构建时间编排工作流，将当前迪拜时间
展示为可视化 SVG 卡片。该工作流遵循
Command → Agent → Skill 架构模式：

- 一个 command 编排流程并处理用户交互
- 一个 agent 使用预加载的 skill 获取迪拜实时时间
- 一个 skill 根据获取的数据创建可视化 SVG 时间卡片

**重要提示**：所有文件必须创建在 `agent-teams/.claude/` 目录内 ——
而不是仓库根目录的 `.claude/` 目录中。这样可以使 agent 团队的
输出保持自包含，并通过 `cd agent-teams && claude` 运行。
不要引用或复制现有的天气工作流 —— 从零开始构建所有内容。

分配以下团队成员：

1. **Command 架构师** — 设计并实现 `/time-orchestrator`
   command，位于 `agent-teams/.claude/commands/time-orchestrator.md`。该 command 应该：
   - 通过 Agent 工具（而非 bash）调用 time-agent 来获取
     迪拜（阿联酋，Asia/Dubai 时区，UTC+4）的当前时间
   - 通过 Skill 工具调用 time-svg-creator skill 来渲染
     基于获取的时间数据的 SVG 卡片
   - 使用 frontmatter 中的 model: haiku
   - 包含关键要求：顺序执行流程、正确的工具使用方式
     （用 Agent 工具调用 agent，用 Skill 工具调用 skill），以及输出摘要
   通过共享任务列表与其他团队成员协调，就组件之间传递的
   数据契约（{time, timezone, formatted}）达成一致。

2. **Agent 工程师** — 设计并实现 `time-agent`，位于
   `agent-teams/.claude/agents/time-agent.md`，以及其预加载的 `time-fetcher`
   skill，位于 `agent-teams/.claude/skills/time-fetcher/SKILL.md`。该 agent 应该：
   - 使用 Bash 执行 `TZ='Asia/Dubai' date '+%Y-%m-%d %H:%M:%S %Z'`
     获取迪拜（Asia/Dubai，UTC+4）的当前时间
   - 将时间值、时区名称和格式化字符串返回给 command
   - 使用 frontmatter：tools（Bash）、model: haiku、color: blue、maxTurns: 3
   - 通过 `skills:` 字段预加载 time-fetcher skill
   time-fetcher skill（`agent-teams/.claude/skills/time-fetcher/SKILL.md`）
   应包含获取迪拜时间的 bash 命令、预期输出格式，
   并设置 user-invocable: false，因为它是仅限 agent 使用的领域知识。
   将约定的数据契约发布到共享任务列表，以便 Command 架构师和
   Skill 设计师能够对齐接口。

3. **Skill 设计师** — 设计并实现 `time-svg-creator`
   skill，位于 `agent-teams/.claude/skills/time-svg-creator/SKILL.md`，并附带支持
   文件 `reference.md`（SVG 模板 + 输出模板）和 `examples.md`
   （示例输入/输出对）。该 skill 应该：
   - 从调用上下文中接收时间值、时区和格式化字符串
   - 为迪拜创建一个自包含的 SVG 时间卡片，显示当前时间
   - 将 SVG 写入 `agent-teams/output/dubai-time.svg`
   - 将 markdown 摘要写入 `agent-teams/output/output.md`
   - 使用提供的确切时间 —— 绝不重新获取
   - 将模板保存在 reference.md 中（带占位符的 SVG 标记、
     markdown 输出模板），将示例对保存在 examples.md 中
   同时创建 `agent-teams/output/` 目录用于存放输出文件。

所有三个团队成员都应在共享任务列表中创建任务来
协调数据契约：agent 返回 {time, timezone, formatted}，
command 通过上下文传递它，skill 消费它。
同时并行启动三者，因为各组件是相互独立的 ——
它们只需要对数据接口达成一致，无需等待彼此的实现。
