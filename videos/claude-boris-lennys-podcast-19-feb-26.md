# Claude Code 负责人：编码问题解决之后会发生什么 — Lenny's Podcast

Boris Cherny ([@bcherny](https://x.com/bcherny))，Claude Code 创始人，在 Lenny's Podcast 的采访文字记录，发布于 2026 年 2 月 19 日。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 视频详情

- **嘉宾：** Boris Cherny（Claude Code 创始人）
- **主持人：** Lenny Rachitsky（Lenny's Podcast）
- **发布日期：** 2026 年 2 月 19 日
- **YouTube：** [在 YouTube 上观看](https://youtu.be/We7BZVKbCVw)

---

## 文字记录

[`0:02`](https://youtu.be/We7BZVKbCVw?t=2) 我的代码 100% 由 Claude Code 编写。从十一月以来我没有手动编辑过任何一行。每天我发布 10、20、30 个 PR。我们录制播客的同时我有五个 agent 在运行。

[`0:13`](https://youtu.be/We7BZVKbCVw?t=13) 你想念写代码吗？

[`0:15`](https://youtu.be/We7BZVKbCVw?t=15) 我从来没有像今天这样享受编码，因为我不需要处理所有琐碎的细节。每位工程师的生产力提高了 200%。

[`0:22`](https://youtu.be/We7BZVKbCVw?t=22) 总是有这个问题——我应该学编程吗？一两年后这就不重要了。编码基本上已经被解决了。我设想一个每个人都能编程的世界。任何人随时都可以构建软件。软件编写方式的下一个大转变是什么？

[`0:36`](https://youtu.be/We7BZVKbCVw?t=36) 也许在一个月后就不需要 plan mode 了。

[`0:38`](https://youtu.be/We7BZVKbCVw?t=38) Claude Code 的构建方式是一种 command-agent-skill 的架构。我们从用户反馈中驱动功能开发。

[`0:57`](https://youtu.be/We7BZVKbCVw?t=57) 你是怎么来到 Anthropic 的？我在日本乡下读 Hacker News，全是 AI 的新闻。第一次用 ChatGPT 时被震撼了。跟 Ben Mann 聊天后被说服了。两个原因——一是研究实验室的属性，产品不重要，模型才重要；二是使命感——午餐时间听到的都是 AI 安全话题。

[`2:02`](https://youtu.be/We7BZVKbCVw?t=122) Claude Code 是怎么诞生的？完全是偶然。当时没有 UI，只有终端，因为最快。然后 tool use 发布了——我给了它 bash 工具，问它我正在听什么音乐，它写了 AppleScript 来查询音乐播放器。这是我的第一个 AGI 时刻。

[`3:03`](https://youtu.be/We7BZVKbCVw?t=183) 你怎么看待 CLI vs IDE？我认为 model 也是用户。终端 UI 的关键洞察是——Claude Code 能访问工程师在终端做的一切。没有中间层。所有东西都是 dual use（双用途）的——slash command 可以被模型调用也可以被人类调用。

[`4:02`](https://youtu.be/We7BZVKbCVw?t=242) 为非编码用户构建？Co-work 来源于 latent demand。有人在用 Claude Code 监控番茄植物，有人用它恢复婚礼照片，设计师和财务团队都在用。Co-work 就是一个带 GUI 的桌面应用包装，底层是同一个 agent。

[`5:17`](https://youtu.be/We7BZVKbCVw?t=317) 你们用什么 slash command？/commit——告诉 Claude 确切地怎么做 commit，预批准 git commit/push/gh 等命令，不需要权限确认。/feature-dev——先问我要什么，制定规范，详细计划，做 to-do list，逐步构建。/code-review——Claude 做所有代码审查的第一步。

[`6:11`](https://youtu.be/We7BZVKbCVw?t=371) 怎么做计划？有几种模式。一是 prototyping mode——先让 Claude 做一遍，看看它犯什么错，然后清掉重来。这帮助你更好地理解要构建什么。二是一次性任务——直接让 Claude 做，Shift+Tab 自动接受，去做别的事。三是复杂的 feature development——Shift+Tab 进入 plan mode，先对齐计划，然后执行。

[`7:01`](https://youtu.be/We7BZVKbCVw?t=421) 你们怎么分工？Boris 设定技术方向，是很多功能的产品愿景者。Cat 负责定价和打包、功能上线流程、沟通。但 ideas 来自所有人——to-do list 是 Sid 做的，hooks 是 Dixon 做的，plugins 是 Daisy 做的。

[`8:08`](https://youtu.be/We7BZVKbCVw?t=488) 什么是 ant fooding？因为我们叫 Anth Ant，所以是 dog fooding（吃自己的狗粮）的变体。70-80% 的技术人员每天使用 Claude Code。每次我们考虑新功能，都先推给内部用户。反馈渠道每 5 分钟一条帖子。

[`9:38`](https://youtu.be/We7BZVKbCVw?t=578) 比如感叹号 bash mode——我有时候要在两个终端间切换很烦，就让 Claude 做了一个 ! 前缀直接运行 bash 命令的功能。

[`10:24`](https://youtu.be/We7BZVKbCVw?t=624) 这个超级有用。而且 Claude Code 也能看到完整输出。

[`10:46`](https://youtu.be/We7BZVKbCVw?t=646) 工具设计的关键：为工程师设计的工具也要让 model 能用。因为我们想分享逻辑——比如 /commit，人类和 Claude 都能用。

[`11:32`](https://youtu.be/We7BZVKbCVw?t=692) 惊喜的是，为人类设计的优雅工具对模型也工作得很好。如果你觉得合理，模型通常也觉得合理。

[`12:14`](https://youtu.be/We7BZVKbCVw?t=734) 关于可扩展性——从解决自己的问题开始（YC 的建议）。然后构建核心 agent loop，让团队和外部用户都能使用。

[`13:07`](https://youtu.be/We7BZVKbCVw?t=787) memory 怎么做？有些人给每个任务让 Claude 写日记——做了什么、尝试了什么、为什么不工作。然后有 agent 来综合这些记忆。但一次性从单个 transcript 中提取记忆很难——你说"让按钮变粉色"，不希望它以后让所有按钮都变粉色。从大量日志中综合记忆才是正道。

[`15:27`](https://youtu.be/We7BZVKbCVw?t=927) compound engineering（复合工程）——在我们的团队，每个功能都会把学到的经验写回 prompt、sub agent、slash command 中，让下一个功能更容易构建。

[`17:04`](https://youtu.be/We7BZVKbCVw?t=1024) 我们在考虑让 Claude Code 自动做这件事。新来的经理 Fiona 第一天就成功提交了 PR，她说她忘了怎么写代码但 Claude Code 让她重新上手了，而且不需要了解上下文因为所有知识都在 memory 中。

[`18:21`](https://youtu.be/We7BZVKbCVw?t=1101) 怎么构建一个不会很快被模型取代的 agent harness？我们构建大多数能提升 Claude Code 能力的东西，即使三个月后要删掉。如果我们不这样做就会被别人超越。

[`20:20`](https://youtu.be/We7BZVKbCVw?t=1220) 我们定位 Claude Code 为高端产品，北极星是用最强大的模型（现在是 Sonnet 4.5）做到最好。

[`20:29`](https://youtu.be/We7BZVKbCVw?t=1229) 关于模型和 harness 的关系——研究人员自己也用 Claude Code，所以他们能看到什么有效什么无效。不容易的任务才能区分模型能力。

[`21:55`](https://youtu.be/We7BZVKbCVw?t=1315) sub agent 的使用？我有 planner sub agent、code review sub agent（CI 中用 slash command，同步使用时用 sub agent 因为可以 fork 上下文窗口）。大规模迁移——spawn 10 个 sub agent 并行处理。内部的 /coder slash command 用多个 sub agent 检查 CLAUDE.md 合规、git 历史、明显 bug，然后 spawn 更多 sub agent 排除误报。

[`25:02`](https://youtu.be/We7BZVKbCVw?t=1502) 一个非技术的使用案例——报销。我用一个 agent 代表我，一个 agent 代表公司，它们"辩论"来确定正确的报销金额。这种对手处理器（adversarial processor）模式很有趣。

[`26:19`](https://youtu.be/We7BZVKbCVw?t=1579) sub agent 的真正价值是不相关的上下文窗口。

[`27:10`](https://youtu.be/We7BZVKbCVw?t=1630) 也可以连接版本控制系统——Claude Code 可以直接查询 GitHub，找到过去类似功能的实现方式。

[`29:56`](https://youtu.be/We7BZVKbCVw?t=1796) 关于 CLI 是最终形态吗？终端是起点不是终点。我们也在尝试 web、桌面应用、iOS/Android、Slack、GitHub、VS Code、JetBrains 等不同形态。

[`31:15`](https://youtu.be/We7BZVKbCVw?t=1875) 一位 Meta 时代的同事说 Claude Code 能 write 100% 的代码——这是真的。对 Anthropic 内部来说，生产力增长了 150%。

[`34:42`](https://youtu.be/We7BZVKbCVw?t=2082) coding 是否已经解决了？对我来说已经解决了。对其他人来说很快也会。软件工程师的头衔会消失。我们团队每个人都在写代码——PM、设计师、EM、财务。

[`36:19`](https://youtu.be/We7BZVKbCVw?t=2176) 推荐的产品？Co-work—— legitimatley 改变了我生活的东西。Chrome 集成非常好，自动帮交了罚款、取消订阅。也推荐 Acquired 播客——从 Nintendo 那期开始。

[`1:16:11`](https://youtu.be/We7BZVKbCVw?t=4571) Claude Code 之所以能持续增长是因为用户。这么多人使用它，热爱它，告诉我们什么不行什么想要。你们就是它不断改进的唯一原因。

[`1:24:16`](https://youtu.be/We7BZVKbCVw?t=5056) 最喜欢的人生格言？运用常识。我看到的大多数失败都是因为人们没有运用常识——盲目遵循流程而不思考，或者在做不好的产品。

[`1:25:08`](https://youtu.be/We7BZVKbCVw?t=5108) 你最近活跃在 Twitter 上，为什么？十二月我在欧洲旅行，每天都在写代码，有一天写烦了就打开 Twitter，看到人们在讨论 Claude Code 的 bug，就开始回复和修复。报 bug 的人对我们修复反馈的速度感到惊讶。

---

## 来源

- [Head of Claude Code: What Happens After Coding Is Solved — Lenny's Podcast — YouTube](https://youtu.be/We7BZVKbCVw)
- [Lenny's Podcast](https://www.lennyspodcast.com/)
