# 构建 Claude Code 的经验：我们如何使用 Skills — Thariq

Thariq（[@trq212](https://x.com/trq212)）于 2026 年 3 月 17 日分享的关于 Anthropic 内部如何使用 skills 的全面指南。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 背景

Skills 已经成为 Claude Code 中使用最多的扩展点之一。它们灵活、易于制作且便于分发。但这种灵活性也让人很难知道什么是最佳实践。Thariq 分享了在 Anthropic 大量使用 skills 的经验教训——目前有数百个 skill 在活跃使用中。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/1.png" alt="Thariq 介绍推文" width="50%" /></a>

---

## 什么是 Skills？

一个常见的误解是 skills "只是 markdown 文件"，但最有趣的部分在于它们是**文件夹**，可以包含脚本、资源、数据等——agent 可以发现、探索和操作的内容。Skills 还有各种各样的配置选项，包括注册动态 hook。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/2.png" alt="什么是 Skills？" width="50%" /></a>

---

## Skills 的类型

在梳理了所有 skill 之后，团队发现它们聚集为 9 个反复出现的类别。最好的 skill 能够干净利落地归入其中一个；而令人困惑的那些则跨越了多个类别。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/3.png" alt="Skills 类型网格" width="50%" /></a>

---

### 1/ 库和 API 参考

解释如何正确使用库、CLI 或 SDK 的 skills。这些可以是内部库或 Claude Code 有时会遇到困难的常用库。它们通常包含一个参考代码片段文件夹以及编写脚本时要避免的常见陷阱列表。

**示例：** billing-lib、internal-platform-cli、frontend-design

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/4.png" alt="库和 API 参考" width="50%" /></a>

---

### 2/ 产品验证

描述如何测试或验证代码是否正常工作的 skills。这些通常与外部工具（如 Playwright、tmux 等）配合使用。验证 skills 对于确保 Claude 的输出正确性非常有用。可能值得让工程师花一周时间把验证 skills 做到极致。

**示例：** signup-flow-driver、checkout-verifier、tmux-cli-driver

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/5.png" alt="产品验证" width="50%" /></a>

---

### 3/ 数据获取与分析

连接到你的数据和监控栈的 skills。这些可能包括使用凭据获取数据的库、特定的仪表盘 ID 等，以及常见工作流的说明或获取数据的方式。

**示例：** funnel-query、cohort-compare、grafana

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/6.png" alt="数据获取与分析" width="50%" /></a>

---

### 4/ 业务流程与团队自动化

将重复性工作流自动化为一条命令的 skills。这些通常相当简单，但可能对其他 skills 或 MCP 有更复杂的依赖关系。将之前的结果保存在日志文件中可以帮助模型保持一致性并反思工作流的先前执行情况。

**示例：** standup-post、create-\<ticket-system\>-ticket、weekly-recap

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/7.png" alt="业务流程与团队自动化" width="50%" /></a>

---

### 5/ 代码脚手架与模板

为代码库中的特定功能生成框架样板代码的 skills。你可以将这些 skills 与可组合的脚本结合使用。当你的脚手架有无法纯代码覆盖的自然语言需求时，它们特别有用。

**示例：** new-\<framework\>-workflow、new-migration、create-app

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/8.png" alt="代码脚手架与模板" width="50%" /></a>

---

### 6/ 代码质量与审查

在组织内部执行代码质量标准并帮助审查代码的 skills。这些可以包含确定性脚本或工具以实现最大的健壮性。你可能希望将这些 skills 作为 hook 的一部分或在 GitHub Action 中自动运行。

**示例：** adversarial-review、code-style、testing-practices

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/10.png" alt="代码质量与审查" width="50%" /></a>

---

### 7/ CI/CD 与部署

帮助你在代码库中获取、推送和部署代码的 skills。这些 skills 可能引用其他 skills 来收集数据。

**示例：** babysit-pr、deploy-\<service\>、cherry-pick-prod

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/11.png" alt="CI/CD 与部署" width="50%" /></a>

---

### 8/ 运维手册

接收症状（如 Slack 线程、告警或错误特征），通过多工具调查进行排查，并生成结构化报告的 skills。

**示例：** \<service\>-debugging、oncall-runner、log-correlator

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/12.png" alt="运维手册" width="50%" /></a>

---

### 9/ 基础设施运维

执行日常维护和运维操作的 skills——其中一些涉及从护栏中受益的破坏性操作。这些使工程师更容易在关键操作中遵循最佳实践。

**示例：** \<resource\>-orphans、dependency-management、cost-investigation

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/13.png" alt="基础设施运维" width="50%" /></a>

---

## 创建 Skills 的技巧

编写高效 skills 的 9 个最佳实践，以及分发和衡量方面的指导。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/14.png" alt="创建 Skills 技巧网格" width="50%" /></a>

---

### 技巧 1：不要陈述显而易见的内容

Claude Code 对你的代码库了如指掌，Claude 也非常了解编码，包括许多默认偏好。如果你发布的 skill 主要是关于知识的，请尝试专注于将 Claude 推出其正常思维模式的信息。前端设计 skill 就是一个很好的例子——它是通过与客户迭代改进 Claude 的设计品味而构建的，避免经典模式如 Inter 字体和紫色渐变。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/15.png" alt="不要陈述显而易见的内容" width="50%" /></a>

---

### 技巧 2：构建陷阱（Gotchas）部分

任何 skill 中信息量最高的内容就是 Gotchas 部分。这些部分应该从 Claude 使用你的 skill 时遇到的常见失败点中积累而成。理想情况下，你应该随着时间推移更新你的 skill 以捕获这些陷阱。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/16.png" alt="构建 Gotchas 部分" width="50%" /></a>

---

### 技巧 3：使用文件系统和渐进式披露

Skill 是一个文件夹，而不仅仅是一个 markdown 文件。你应该将整个文件系统视为一种上下文工程和渐进式披露的形式。告诉 Claude 你的 skill 中有哪些文件，它会在适当的时候读取它们。最简单的形式是指向其他 markdown 文件——例如，将详细的函数签名和使用示例拆分到 `references/api.md` 中。你可以有引用文件夹、脚本、示例等的文件夹。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/17.png" alt="渐进式披露" width="50%" /></a>

---

### 技巧 4：避免过度约束 Claude

Claude 通常会尝试遵循你的指令，而且由于 skills 如此可复用，你会想要注意不要过于具体。给 Claude 所需的信息，但给它灵活性以适应情况。与其给出规定性的逐步指令，不如给出目标和约束。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/18.png" alt="避免过度约束 Claude" width="50%" /></a>

---

### 技巧 5：考虑设置流程

某些 skills 可能需要用户提供的上下文来进行设置。一个好的模式是将这些设置信息存储在 skill 目录中的 `config.json` 文件里。如果配置未设置，agent 可以向用户询问信息。你可以指示 Claude 使用 AskUserQuestion 工具进行结构化的多选题。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/19.png" alt="考虑设置流程" width="50%" /></a>

---

### 技巧 6：Description 字段是给模型看的

当 Claude Code 启动会话时，它会构建一个包含每个可用 skill 及其描述的列表。Claude 会扫描此列表来决定"是否有适合这个请求的 skill？"这意味着 description 字段不是摘要——它是对**何时触发**此 skill 的描述。请为模型而写。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/20.png" alt="Description = 触发器" width="50%" /></a>

---

### 技巧 7：记忆与数据存储

某些 skills 可以通过在内部存储数据来包含一种记忆形式。你可以将数据存储在简单如仅追加的文本日志文件或 JSON 文件中，也可以存储在复杂如 SQLite 数据库中。存储在 skill 目录中的数据在升级 skill 时可能会被删除，因此请使用 `${CLAUDE_PLUGIN_DATA}` 作为每个 plugin 的稳定文件夹来存储数据。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/21.png" alt="记忆与数据存储" width="50%" /></a>

---

### 技巧 8：存储脚本与生成代码

你能给 Claude 最强大的工具之一就是代码。给 Claude 脚本和库可以让 Claude 把轮次花在组合上——决定下一步做什么，而不是重建样板代码。Claude 然后可以动态生成脚本来组合这些功能以进行更高级的分析。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/22.png" alt="存储脚本与生成代码" width="50%" /></a>

---

### 技巧 9：按需 Hook

Skills 可以包含仅在调用 skill 时激活的 hook，并在会话持续期间有效。将此用于你不想一直运行但有时非常有用的更加有主见的 hook。

**示例：**
- `/careful` — 通过 PreToolUse 匹配器在 Bash 上阻止 rm -rf、DROP TABLE、force-push、kubectl delete
- `/freeze` — 阻止不在特定目录中的任何 Edit/Write

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/23.png" alt="按需 Hook" width="50%" /></a>

---

## 分发 Skills

与团队分享 skills 的两种方式：
- **提交到你的仓库**（在 `.claude/skills` 下）——最适合在相对较少的仓库中工作的小型团队
- **制作 plugin** 并建立一个 Claude Code Plugin marketplace，用户可以在其中上传和安装 plugin

每个被提交的 skill 也会略微增加模型的上下文。随着规模扩大，内部 plugin marketplace 允许你分发 skills 并让你的团队决定安装哪些。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/24.png" alt="分发 Skills" width="50%" /></a>

---

## 管理 Marketplace

没有一个集中化的团队来决定哪些 skills 进入 marketplace。相反，尝试有机地发现最有用的 skills。上传到 GitHub 的 sandbox 文件夹中，并通过 Slack 或其他论坛指向它。一旦某个 skill 获得了关注（这由 skill 所有者决定），他们可以提交 PR 将其移入 marketplace。发布前的策划对于避免重复的 skills 很重要。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/25.png" alt="管理 Marketplace" width="50%" /></a>

---

## 组合 Skills

你可能想要有相互依赖的 skills。例如，一个上传文件的文件上传 skill，和一个生成 CSV 并上传它的 CSV 生成 skill。这种依赖管理尚未内置于 marketplace 或 skills 中，但你可以通过名称引用其他 skills，如果它们已安装，模型将调用它们。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/26.png" alt="组合 Skills" width="50%" /></a>

---

## 衡量 Skills

要了解一个 skill 的使用情况，可以使用 PreToolUse hook 让你记录公司内的 skill 使用情况。这意味着你可以找到流行的 skills 或与预期相比触发率不足的 skills。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/27.png" alt="衡量 Skills" width="50%" /></a>

---

## 总结

Skills 对于 agent 来说是极其强大和灵活的工具，但它仍处于早期阶段，我们都在摸索如何最好地使用它们。与其把它看作一份权威指南，不如把它看作是我们看到的行之有效的有用技巧集锦。理解 skills 的最好方式就是开始上手、实验，看看什么对你有效。我们的大部分 skill 最初只有几行代码和一个 gotcha，随着 Claude 遇到新的边缘情况，人们不断添加内容而变得更好。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-17-mar-26/28.png" alt="总结" width="50%" /></a>

---

## 来源

- [Thariq (@trq212) 在 X 上 — 2026 年 3 月 17 日](https://x.com/trq212/status/2033949937936085378)
- [Skilljar — Agent Skills 课程](https://code.claude.com/docs/en/skills)
- [Skill Creator](https://code.claude.com/docs/en/skills)
