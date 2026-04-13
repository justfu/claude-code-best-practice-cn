# Claude Code 的秘密：来自构建它的工程师 — Every

Claude Code 工程师 Cat 和 Boris 在 Every 播客的采访文字记录，发布于 2025 年 10 月 29 日。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 视频详情

- **嘉宾：** Cat 和 Boris（Claude Code 工程师，Anthropic）
- **主持人：** Every
- **发布日期：** 2025 年 10 月 29 日
- **YouTube：** [在 YouTube 上观看](https://youtu.be/IDSAMqip6ms)

---

## 文字记录

[`0:02`](https://youtu.be/IDSAMqip6ms?t=2) 让 Claude Code 如此好用的关键是它能访问工程师在终端做的一切。你能做的它都能做。没有中间层。

[`0:10`](https://youtu.be/IDSAMqip6ms?t=10) Anthropic 内部越来越多的人在大量使用——每月花费超过 1000 美元。我们看到这种 power user 行为。这其实是 YC 教的东西——如果你能解决自己的问题，你很可能也在解决别人的问题。产品中有一个很老的叫 latent demand 的理念——你以一种可 hack 的方式构建产品，人们可以以非预期的方式滥用它，然后你围绕这个需求构建。

[`1:29`](https://youtu.be/IDSAMqip6ms?t=89) Cat 和 Boris，非常感谢你们。

[`1:32`](https://youtu.be/IDSAMqip6ms?t=92) 谢谢邀请。你们是 Claude Code 的创造者。我真心热爱 Claude Code。

[`1:42`](https://youtu.be/IDSAMqip6ms?t=102) 第一次使用时——大概是 Sonnet 3.7 出来的时候——我觉得这是完全新的范式。最大的不同是你们直接去掉了文本编辑器，只跟终端对话。那跟我谈谈这个决策过程。

[`2:36`](https://youtu.be/IDSAMqip6ms?t=156) 这完全不是故意的。我们偶然走到了这一步。当时 Anthropic 有一个叫 Clyde 的前身项目——很重的 Python 东西，启动要一分钟。我加入 Anthropic 后想提交第一个 PR，手写了一个。Adam Wolf（我的导师）拒绝了 PR，说你手写的？用 Clyde 啊。我花了半天学会怎么用，但它一次性就生成了一个能用的 PR。这是我在 Anthropic 的第一个 AGI 时刻。

[`4:02`](https://youtu.be/IDSAMqip6ms?t=242) 后来我在用 API 做原型，最简单的方式是在终端构建应用。我做了一个聊天应用，然后开始给模型工具。最大的启示是——模型就是想要使用工具。我给了它 bash，它就开始用 bash 写 AppleScript 来自动化东西。我从来没见过这样的东西——之前我只用过有行内自动补全的 IDE。

[`5:03`](https://youtu.be/IDSAMqip6ms?t=303) 对 Cat 来说，那个神奇时刻大概是 Sonnet 4 / Opus 4 出来的时候。

[`5:17`](https://youtu.be/IDSAMqip6ms?t=317) 谈谈 tool moment——Claude Code 很擅长写 bash。很多人的第一直觉是给 agent 各种自定义 wrapper（find file tool、open file tool），但 Claude Code 直接用 bash，而且很擅长。现在 Claude Code 有一打左右的工具，每周都在增删。最近我们删掉了 OS tool，因为我们用 bash 的权限系统来强制执行了同样的限制。工具越少越好——对 Claude 的上下文来说。

[`7:01`](https://youtu.be/IDSAMqip6ms?t=421) 你们怎么分工？Boris 设定技术方向，是很多功能的产品愿景者。Cat 负责定价和打包、功能上线流程（从原型到 ant fooding 到用户沟通）。大部分功能是 bottom up 的——to-do list 是 Sid 做的，hooks 是 Dixon，plugins 是 Daisy。

[`8:08`](https://youtu.be/IDSAMqip6ms?t=488) 什么是 ant fooding？dog fooding 的 Anthropic 版本——我们的内部员工叫 ant。70-80% 的技术人员每天使用 Claude Code。反馈渠道每 5 分钟一条。你能在构建产品的同时使用它——这就是它的 ergonomics 如此合理的原因。

[`9:23`](https://youtu.be/IDSAMqip6ms?t=563) 举个例子——bash mode（!前缀）是 Boris 随口跟 Claude 说的，Claude 就做了。

[`10:24`](https://youtu.be/IDSAMqip6ms?t=624) 这个超级有用——我不用打开新 tab 了。而且 Claude Code 也能看到完整输出。这其实是 dual use 的理念——为人类和模型同时设计。比如 /commit slash command——人类和 Claude 都能用。

[`11:49`](https://youtu.be/IDSAMqip6ms?t=709) Claude Code 作为 terminal UI 的关键——它有终端的一切访问权限。这让 dual use 变得自然。

[`13:07`](https://youtu.be/IDSAMqip6ms?t=787) 为构建 agent 的人的建议——从解决自己的问题开始。Claude Code 是本地开始的，合理。现在也有 web 版可以在 VM 中运行。

[`14:07`](https://youtu.be/IDSAMqip6ms?t=847) 你们的 slash commands？/commit、/code-review、/feature-dev（Sid 创建的——先问要构建什么，制定规范，详细计划，做 to-do list，逐步构建）。

[`15:51`](https://youtu.be/IDSAMqip6ms?t=951) 怎么做好计划？一个不直觉的步骤是——即使你不知道确切要构建什么，就让 Claude 先做一遍。看看它犯什么错，清掉重来。这些学习帮助写更好的计划。这以前代价太高，但有了 Claude Code 就不贵了。

[`17:07`](https://youtu.be/IDSAMqip6ms?t=1027) 几种模式：prototyping mode（先让 Claude 做，看它犯什么错）；一次性任务（直接让 Claude 做，Shift+Tab 自动接受）；复杂的 feature development（plan mode 先对齐）。

[`18:21`](https://youtu.be/IDSAMqip6ms?t=1101) 构建不会被模型取代的东西？我们构建大多数能提升能力的东西，即使三个月后要删掉。plan mode 可能寿命有限——Claude 现在可以自己进入 plan mode 了。

[`20:20`](https://youtu.be/We7BZVKbCVw?t=1220) 模型和 harness 的紧密集成——研究人员自己也用，能直接看到什么有效。不容易的任务才能区分模型能力。我们对标的是最强大的模型。

[`21:55`](https://youtu.be/IDSAMqip6ms?t=1315) sub agent 的使用？planner sub agent、code review sub agent（CI 用 slash command，同步用 sub agent 因为 fork 上下文）。大规模迁移——spawn 10 个 sub agent。内部 /coder 用多个 sub agent 做不同检查，然后 spawn 更多排除误报。对手处理器模式——一个 agent 代表我，一个代表公司做报销辩论。

[`28:02`](https://youtu.be/IDSAMqip6ms?t=1682) memory 怎么做？有些人给每个任务写日记，然后有 agent 来综合记忆。从大量日志中综合比一次性提取更可靠。随着模型变聪明，它也会自然地做——比如 Sonnet 4.5 卡住时会自发用 bash 查看 git 历史。

[`31:15`](https://youtu.be/IDSAMqip6ms?t=1875) compound engineering（复合工程）——每个功能把学到的经验写回 prompt 和 slash command，让下一个功能更容易。我们在考虑让 Claude Code 自动做这个。

[`32:53`](https://youtu.be/IDSAMqip6ms?t=1973) 可扩展性——Boris 把自己放在"普通工程师"类别里。如果 Boris 能用的功能，其他平均水平的工程师也能用。所有系统部分都可扩展——status line、slash commands、hooks。Plugins 是让普通用户更方便地安装这些。

[`34:38`](https://youtu.be/IDSAMqip6ms?t=2078) Latent demand——你构建一个可以被 hack 的产品，看人们怎么滥用它，然后围绕那个需求构建。Facebook Dating 来自 60% 的 profile 浏览者是异性非好友的观察。Marketplace 来自 40% 的群组帖子是买卖。

[`36:41`](https://youtu.be/IDSAMqip6ms?t=2201) Agent SDK 的重新定位——从 Claude Code SDK 到 Claude Agent SDK，因为很多用例不是编码。健康助手、财务分析师、法律助手。核心是——只要 agent loop 能长时间运行，能访问互联网和代码，基本上什么都能构建。

[`40:41`](https://youtu.be/IDSAMqip6ms?t=2441) 向量搜索 vs agentic search？我们最初用向量嵌入，但维护困难（需要持续重新索引、本地变更问题、安全风险）。我们发现 agentic search 能达到相同准确率，部署更简洁。如果想要语义搜索，可以通过 MCP tool 接入。

[`42:09`](https://youtu.be/IDSAMqip6ms?t=2529) 最好的 MCP？Puppeteer、Playwright、Sentry、Asana。power user 技巧——让 Claude 在 plan mode 中主动问你问题（而不是默认不问）。settings.json 检入代码库来预批准命令和屏蔽命令。stop hook——如果测试不通过就返回"keep going"。

[`45:09`](https://youtu.be/IDSAMqip6ms?t=2709) CLI 是最终形态吗？不是。我们在实验多种形态——CLI、IDE 扩展（VS Code GUI）、@claude on GitHub、web、mobile。趋势是更长的自主运行时间——现在双位数小时，下个模型可能到天。

[`47:48`](https://youtu.be/IDSAMqip6ms?t=2868) 终端对非技术人员来说很可怕。VS Code GUI 扩展是第一步。web 版的 GUI 也更友好。Claude Code 本身专注于为最好的工程师构建最好的产品，同时也让别人能 hack 它来做其他事。

[`50:11`](https://youtu.be/IDSAMqip6ms?t=3011) 如果代码太冗长，直接告诉 Claude 简化它，效果很好。

[`51:28`](https://youtu.be/IDSAMqip6ms?t=3089) 为什么不把这个自动做成 slash command？影响太少的对话，不想矫枉过正。

[`52:50`](https://youtu.be/IDSAMqip6ms?t=3170) prompt engineering 曾经是一份工作，现在不是了。更多这类微技能会随模型变强而消失。构建产品需要谦逊——我们也不知道下一步是什么。

[`54:06`](https://youtu.be/IDSAMqip6ms?t=3246) 构建消费级应用的时代——我用 Agent SDK 做了一个购物顾问 assistant，帮我看沙发选项和评论。还有邮件回复 agent。

[`55:26`](https://youtu.be/IDSAMqip6ms?t=3326) 人们正在从文档转向 demo。你想要人们兴奋，展示 15 秒它能做什么就好。

[`56:53`](https://youtu.be/IDSAMqip6ms?t=3413) Plan mode 做了三次——做出来、扔掉、重建、再扔掉、再重建。To-do list 也做了三四个原型，然后 Boris 又做了 20 个。几乎所有发布的功能背后都有至少几个原型。

[`57:02`](https://youtu.be/IDSAMqip6ms?t=3422) 怎么保持从原型中学到的东西？一部分是 style guide（我们的 CLAUDE.md），另一部分是 product sense——模型还不完全理解"用最简单的方式解决问题然后删掉其他一切"。

[`59:12`](https://youtu.be/IDSAMqip6ms?t=3553) thinking mode 的演变——有人问能不能让模型思考，有人说直接用自然语言告诉它"请思考"就行了。后来人们不小心触发（说"don't think"反而触发了思考），所以做了 UX 改进来高亮 thinking。用 Tab 来 toggle，unship 了一些 thinking 触发词（保留了 ultra think 因为情怀）。

[`1:01:02`](https://youtu.be/IDSAMqip6ms?t=3662) 删除代码？我最喜欢看到红色 diff。原则是——unship 一个功能的同时必须 ship 一个更好的。Anthropic 自一月以来规模翻倍，但每位工程师的生产力增长了约 70%（以 PR 衡量）。

[`1:03:37`](https://youtu.be/IDSAMqip6ms?t=3817) 怎么在对话式 UI 中做到直觉化？用问号看提示、工作中显示提示、侧边更新日志、通知新模型。关键原则是不要新增用户体验——所有东西应该直觉到直接上手就能用。另一个原则是渐进式披露——Control+O 看完整 transcript，但只在相关时才提示你看。还有一个新原则——model 教你使用产品。比如看到模型调用 slash command，你也会知道你可以这样做。

[`1:05:39`](https://youtu.be/IDSAMqip6ms?t=3939) CLI 风潮？模仿是最好的赞美。我们专注于解决我们和客户的问题。我个人不太用其他工具。

[`1:08:14`](https://youtu.be/IDSAMqip6ms?t=4094) Unshipping（下线功能）很难。Facebook 在这方面做得不好。Instagram 更有原则——使用率不到 50% 就删除。但确实有社交成本——没人想告诉同事要下线他们的功能。

---

## 来源

- [The Secrets of Claude Code From the Engineers Who Built It — Every — YouTube](https://youtu.be/IDSAMqip6ms)
- [Every](https://every.to/)
