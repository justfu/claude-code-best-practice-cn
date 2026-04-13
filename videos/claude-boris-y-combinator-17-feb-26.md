# Claude Code 之父 Boris Cherny 深度访谈 — Y Combinator

Boris Cherny ([@bcherny](https://x.com/bcherny))，Claude Code 创始人，在 Y Combinator Light Cone 播客的采访文字记录，发布于 2026 年 2 月 17 日。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 视频详情

- **嘉宾：** Boris Cherny（Claude Code 创始人）
- **主持人：** Y Combinator（The Light Cone）
- **发布日期：** 2026 年 2 月 17 日
- **YouTube：** [在 YouTube 上观看](https://youtu.be/PQU9o_5rHC4)

---

## 文字记录

[`0:01`](https://youtu.be/PQU9o_5rHC4?t=1) 在 Anthropic，我们的思路是我们不为今天的模型构建，我们为六个月后的模型构建。这实际上至今仍是我对在 LLM 上构建的创始人的建议——想想模型今天还不擅长的领域是什么，因为它会变强的。Claude Code 的所有代码已经被反复重写了无数次。六个月前的 Claude Code 没有任何一个部分还保留着。你尝试一个东西，交给用户，跟用户交谈，学习，然后最终你可能会得到一个好点子。有时候不会。

[`0:36`](https://youtu.be/PQU9o_5rHC4?t=36) 也许一个月后，

[`0:38`](https://youtu.be/PQU9o_5rHC4?t=38) 一个月后就不需要 plan mode 了。欢迎来到另一期 Light Cone 节目，今天我们有一位非常特别的嘉宾——Claude Code 的创始工程师 Boris Cherny。Boris，感谢你的到来。

[`0:59`](https://youtu.be/PQU9o_5rHC4?t=59) 感谢邀请。

[`1:00`](https://youtu.be/PQU9o_5rHC4?t=60) 感谢你创造了一个让我连续三周失去睡眠的东西。

[`1:07`](https://youtu.be/PQU9o_5rHC4?t=67) 我对 Claude Code 非常上瘾，感觉像是火箭助推器。这对大家来说是不是也像这样持续了几个月？我觉得大概是在十一月底，我的很多朋友说有什么东西变了。

[`1:21`](https://youtu.be/PQU9o_5rHC4?t=81) 我记得我第一次创建 Claude Code 时就有这种感觉，当时我还不确定我是否发现了什么。我觉得我发现了，然后那段时间我睡不着。

[`1:28`](https://youtu.be/PQU9o_5rHC4?t=88) 是的。

[`1:29`](https://youtu.be/PQU9o_5rHC4?t=89) 那是连续三个月。

[`1:33`](https://youtu.be/PQU9o_5rHC4?t=93) 那是 2024 年 9 月。连续三个月，一天假都没休。周末也在工作。每天晚上都在工作。我就觉得，天哪，这会是一个大事。我还不知道它是否有用，因为它实际上还不能写代码。

[`1:48`](https://youtu.be/PQU9o_5rHC4?t=108) 回顾那些时刻到现在，最让人惊讶的是什么？

[`1:54`](https://youtu.be/PQU9o_5rHC4?t=114) 令人难以置信的是我们仍然在使用终端。终端本应是起点，我以为不会是终点。第二个令人惊讶的是它居然有用，因为一开始它不太会写代码。即使在二月份它大概只写了我 10% 的代码。我主要还是手写。所以我们的赌注得到了回报，它确实在我们预期会变强的领域变强了——这并不明显。在 Anthropic，我们的思路是我们不为今天的模型构建，我们为六个月后的模型构建。

[`2:39`](https://youtu.be/PQU9o_5rHC4?t=159) 回到最开始，你什么时候有了这个想法？是灵光一闪还是什么？

[`2:47`](https://youtu.be/PQU9o_5rHC4?t=167) 很有趣，它非常偶然。作为 Anthropic 的一员，编码的赌注已经持续了很长时间——通向安全 AGI 的路径是通过编码。你教模型如何写代码，然后教它如何使用工具，然后教它如何使用电脑。我加入的第一个团队叫 Anthropic Labs 团队，产生了三个产品：Claude Code、MCP 和桌面应用。

[`3:03`](https://youtu.be/PQU9o_5rHC4?t=183) 没有人让我构建一个 CLI。我们大概知道该构建某种编码产品了，但还没有人真正构建出利用这种能力的产品。所以我开始 hacking。第一步是理解如何使用 API。我就构建了一个小终端应用来用 API，就是一个聊天应用，因为当时大多数人用的就是聊天。然后 tool use 发布了，我就想试试。我给了它 bash 工具。然后我问它——我正在听什么音乐？它写了一段 AppleScript 来查询我的音乐播放器。这是用 Sonnet 3.5 做到的。这是我有生以来第一次感受到 AGI 的时刻。

[`4:25`](https://youtu.be/PQU9o_5rHC4?t=265) 你在终端里构建只是因为那是最快的方式？

[`4:29`](https://youtu.be/PQU9o_5rHC4?t=269) 是的，因为我不用构建 UI。

[`4:30`](https://youtu.be/PQU9o_5rHC4?t=270) 好的。

[`4:31`](https://youtu.be/PQU9o_5rHC4?t=271) 当时只有我一个人。IDE、Cursor、Windsurf 正在起飞，你有没有压力要把这做成插件或 IDE？没有压力，因为我们甚至不知道要构建什么。

[`5:24`](https://youtu.be/PQU9o_5rHC4?t=324) 天哪。

[`5:26`](https://youtu.be/PQU9o_5rHC4?t=326) 这是 Sonnet 3.5。

[`5:28`](https://youtu.be/PQU9o_5rHC4?t=328) 我没想到模型能做到这个。

[`5:34`](https://youtu.be/PQU9o_5rHC4?t=334) 我就觉得天哪，模型就是想要使用工具。它只想用工具。

[`5:39`](https://youtu.be/PQU9o_5rHC4?t=339) 这很有趣。Claude Code 在如此优雅简单的终端形态下运行得这么好，这其实是很反直觉的。终端已经存在很久了，但它似乎是一个很好的设计约束。

[`6:09`](https://youtu.be/PQU9o_5rHC4?t=369) 是的，这是个意外。第二天我给团队用，Robert 坐在我对面，已经在用 Claude Code 写代码了。我说你在干什么？这只是个原型啊。但它已经很有用了。Dario 在我们的发布评审会上问，内部使用量图表是垂直的，你们是不是在强制工程师使用？我说没有，我只是发了帖子，大家互相告诉对方的。

[`7:13`](https://youtu.be/PQU9o_5rHC4?t=433) 在 2024 年那个时期，工程师们怎么使用它的？他们在用这个发布代码吗？模型还不太擅长编码。我个人主要用它来自动化 git 操作。第一个用例实际上是写单元测试，因为风险较低。

[`7:51`](https://youtu.be/PQU9o_5rHC4?t=471) 我们看到人们开始为自己写 markdown 文件，然后让模型读取。这就是 CLAUDE.md 的来源。产品中对我来说最大的原则是 latent demand（潜在需求）。你构建一个可以被 hack 的产品，让人们以你没有预期的方式使用它，然后你看到他们怎么用，然后围绕这个构建产品。

[`8:50`](https://youtu.be/PQU9o_5rHC4?t=530) 你说你的 CLAUDE.md 其实很短？

[`9:03`](https://youtu.be/PQU9o_5rHC4?t=543) 我的 CLAUDE.md 只有两行。第一行是：每次提交 PR 时，启用 automerge。第二行是：每次提交 PR 时，发布到内部团队 Slack 频道。所有其他指令都在提交到代码库的 CLAUDE.md 中，我们整个团队每周贡献好几次。

[`9:52`](https://youtu.be/PQU9o_5rHC4?t=592) 你需要压缩 CLAUDE.md 吗？

[`10:03`](https://youtu.be/PQU9o_5rHC4?t=603) 我们的 CLAUDE.md 其实很短。如果你超限了，我的建议是删掉重新开始。

[`10:44`](https://youtu.be/PQU9o_5rHC4?t=644) 等等，真的吗？我本来以为你在终端构建这个，你一定是个死忠 Vim 党。

[`10:53`](https://youtu.be/PQU9o_5rHC4?t=653) 团队里确实有这样的人。Adam Wolf 就说永远不会从他的冷手中拿走 Vim。每个工程师喜欢用不同的开发工具，没有一种工具适合所有人。使用 Claude Code 不需要理解 Vim、TMUX 或 SSH，你只需打开工具，它会引导你。

[`11:30`](https://youtu.be/PQU9o_5rHC4?t=690) 你怎么决定终端输出的详细程度？每个用户都有自己的偏好。

[`11:47`](https://youtu.be/PQU9o_5rHC4?t=707) 你觉得现在太啰嗦了吗？

[`11:50`](https://youtu.be/PQU9o_5rHC4?t=710) 不，我喜欢详细输出。有时候它跑偏了我看一眼就能发现不对，然后 Escape 停止它。这通常是没正确使用 plan mode 的结果。

[`12:07`](https://youtu.be/PQU9o_5rHC4?t=727) 这件事我们经常改。六个月前我试着在内部隐藏 bash 输出，但一天后所有人都反对。他们想看输出。最近我们隐藏了文件读取和搜索的输出。六个月前我们做不到这个，因为模型会读错东西。现在几乎每次都是对的。我们添加了 verbose mode，按 Control+O 可以看完整输出。

[`14:10`](https://youtu.be/PQU9o_5rHC4?t=850) 有些人认为任何时候需要真人看代码就是不好的。

[`14:30`](https://youtu.be/PQU9o_5rHC4?t=870) 是的，是的。

[`14:31`](https://youtu.be/PQU9o_5rHC4?t=871) 这很有趣。

[`14:32`](https://youtu.be/PQU9o_5rHC4?t=872) Dan Chipper 谈了很多——当看到模型犯错时，尝试把它写进 CLAUDE.md 或 skill 中使其可复用。但其实 agent 能做什么，随着每个模型都在变化。

[`15:45`](https://youtu.be/PQU9o_5rHC4?t=945) 对技术创始人有什么建议来最大化利用最新模型发布？我觉得对你自己来说就是初学者心态和谦虚。作为工程师，我们学会了有很强的意见，高级工程师也因此受到奖励。但很多东西不再相关了。我认为最大的技能是能科学思考和从第一性原理思考的人。

[`16:40`](https://youtu.be/PQU9o_5rHC4?t=1000) 你招聘时怎么筛选这个？我有时会问"什么时候你错了"这个问题。这其实是个很好的行为面试问题。你能看到人们是否能事后认识到自己的错误，是否能承担错误的责任，并从中学习。

[`17:34`](https://youtu.be/PQU9o_5rHC4?t=1054) 你会根据 Claude Code 的使用记录来招聘吗？我们正在这样做。你可以上传你用 Claude Code 编码功能的文字记录。你能看出一个人怎么思考，是否查看日志，能否纠正跑偏的 agent，是否使用 plan mode。

[`18:31`](https://youtu.be/PQU9o_5rHC4?t=1111) 技能维度是什么？系统思维、测试、用户行为、产品感、自动化。我最喜欢的 CLAUDE.md 指令是：对于每个 plan，判断它是否过度工程、不足工程或完美工程，以及为什么。

[`18:54`](https://youtu.be/PQU9o_5rHC4?t=1134) 我觉得我们团队最有效的工程师分为两类：极端专家和极端通才。Jared 是前者的例子，他理解 dev tools 和 JavaScript 运行时系统比任何人都好。Daisy 是后者的例子——她为 Claude Code 提交了一个 PR，不是直接添加功能，而是先给 Claude Code 一个工具让它能测试任意工具并验证，然后让 Claude 自己写工具来实现。

[`20:42`](https://youtu.be/PQU9o_5rHC4?t=1242) 有种有趣的现象——有远见的创始人有产品的清晰愿景，能做 50 倍的工作，但他们雇佣的工程师没有那个愿景，只能做 5 倍。

[`21:52`](https://youtu.be/PQU9o_5rHC4?t=1312) 我们刚发布了 Claude Teams。你也可以自己构建方式来做这件事。

[`21:59`](https://youtu.be/PQU9o_5rHC4?t=1319) Claude Teams 的愿景是什么？

[`22:01`](https://youtu.be/PQU9o_5rHC4?t=1321) 协作。有一个叫 uncorrelated context windows 的想法——多个 agent 有各自独立的上下文窗口，不被彼此污染。如果你往问题上扔更多上下文，这是一种测试时计算的形式。Plugins 功能完全由一个 swarm 在一个周末构建的，跑了几天，基本没有人类干预。

[`22:54`](https://youtu.be/PQU9o_5rHC4?t=1374) 怎么设置的？一个工程师给 Claude 一个 spec，让它用 Linear 看板，Claude 在上面创建了一堆 ticket，然后生成一堆 agent，agent 开始自动领取任务。

[`23:21`](https://youtu.be/PQU9o_5rHC4?t=1401) 独立的 agent，没有大 spec 的上下文。

[`23:25`](https://youtu.be/PQU9o_5rHC4?t=1405) 对。大多数 agent 实际上是由 Claude 通过 sub agent 的形式启动的——sub agent 就是一个递归的 Claude Code，我们叫它 mama Claude。

[`23:45`](https://youtu.be/PQU9o_5rHC4?t=1425) 我的 Claude Insights 告诉我应该更多地在调试时使用多个 sub agent 并行。我把这个加到了 CLAUDE.md 里：下次你尝试修复 bug 时，让一个 agent 看日志，一个看代码路径。

[`24:11`](https://youtu.be/PQU9o_5rHC4?t=1451) 对于棘手的 bug，我在 plan mode 中修复，它会用 agent 搜索一切。如果测试看起来有点难，我会根据任务难度调整 sub agent 的数量——如果很难，就用 3 个、5 个甚至 10 个并行研究。

[`24:33`](https://youtu.be/PQU9o_5rHC4?t=1473) 那为什么不把这个放进 CLAUDE.md？

[`24:44`](https://youtu.be/PQU9o_5rHC4?t=1484) 这是按情况来的。CLAUDE.md 是个快捷方式——如果你发现自己反复说同样的话，就放进去。否则你直接告诉 Claude 就好。

[`24:56`](https://youtu.be/PQU9o_5rHC4?t=1496) 你是否在想也许六个月后你就不需要这样显式地 prompt 了？模型自己就能搞定？

[`25:05`](https://youtu.be/PQU9o_5rHC4?t=1505) 也许一个月后。

[`25:07`](https://youtu.be/PQU9o_5rHC4?t=1507) 一个月后就不需要 plan mode 了。

[`25:07`](https://youtu.be/PQU9o_5rHC4?t=1507) 天哪。

[`25:09`](https://youtu.be/PQU9o_5rHC4?t=1509) 我觉得 plan mode 的寿命有限。

[`25:11`](https://youtu.be/PQU9o_5rHC4?t=1511) 有趣。

[`25:12`](https://youtu.be/PQU9o_5rHC4?t=1512) 这是给大家的信息。没有 plan mode 的世界是什么样的？Claude Code 现在可以自己进入 plan mode 了。plan mode 其实就是在 prompt 中加一句话：请不要写代码。

[`25:47`](https://youtu.be/PQU9o_5rHC4?t=1547) 所以 Claude Code 的大部分功能开发跟 YC 说的"跟用户交流然后实现"是一样的。

[`25:59`](https://youtu.be/PQU9o_5rHC4?t=1559) 是的。plan mode 的来源是——我们看到用户对 Claude 说"来想个主意，做计划，但先不要写代码"。周日晚十点我写出来，当晚就发布了。

[`26:49`](https://youtu.be/PQU9o_5rHC4?t=1609) 我 80% 的会话从 plan mode 开始。用 Opus 4.5，计划一旦确定，它几乎每次都能正确执行。以前你计划前后都要照看，现在只需在计划前照看。也许下一步你完全不需要照看了。

[`27:53`](https://youtu.be/PQU9o_5rHC4?t=1673) 下一步是 Claude 直接跟你的用户交流。完全绕过你。

[`27:59`](https://youtu.be/PQU9o_5rHC4?t=1679) 我们的 Claude 之间确实在互相交流。它们在 Slack 上跟我们的用户交流。我的 Claude 偶尔还会发推文，但我通常删掉——语气不太对。

[`28:25`](https://youtu.be/PQU9o_5rHC4?t=1705) 一个常见模式是我让 Claude 构建东西，它看到代码库中某个人修改过什么，就在 Slack 上给那个人发消息问个澄清问题，得到答案后继续。

[`28:40`](https://youtu.be/PQU9o_5rHC4?t=1720) 给创始人什么建议？什么原则会持续，什么会改变？Latent demand 仍然是最重要的原则——人们只会做他们已经在做的事，你不可能让他们做新事。你要让他们已经在做的事变得更容易。为模型想要做的事情考虑如何让它更容易做。

[`29:45`](https://youtu.be/PQU9o_5rHC4?t=1785) Plan mode 就是 latent demand 的例子——人们已经在用 Claude 聊天窗口来制定 spec，plan mode 只是把它放到了 Claude Code 里。

[`30:19`](https://youtu.be/PQU9o_5rHC4?t=1819) 对终端的前景怎么看？一年前我会说终端只有三个月的寿命。但实际上我们一直在尝试不同形态——web、桌面应用、iOS 和 Android 应用、Slack、GitHub、VS Code、JetBrains。

[`30:58`](https://youtu.be/PQU9o_5rHC4?t=1858) 对 DevTool 创始人的建议？应该为工程师构建还是为 agent 构建？想想模型想要做什么，然后让这件事更容易做。

[`31:54`](https://youtu.be/PQU9o_5rHC4?t=1914) 十多年前你是重度用户还写了一本 TypeScript 的书。TypeScript 的类型系统有一些非常独特的决定——任何东西都可以是 literal type，条件类型——连 Haskell 都没有这么极端。Joe Pamer 和 Anders 的团队构建这个类型系统不是来自学术，而是来自观察 JavaScript 程序员如何写代码。

[`34:42`](https://youtu.be/PQU9o_5rHC4?t=2082) 15 年后，Haskell 的代码库没多少，但 TypeScript 到处都是，因为它更实用。

[`34:47`](https://youtu.be/PQU9o_5rHC4?t=2087) 终端其实是最好看的终端应用之一，用 React Terminal 写的。

[`34:58`](https://youtu.be/PQU9o_5rHC4?t=2098) 我也做前端。喜悦感（delight）非常重要。在 YC 你们也常谈论这个——构建人们爱的东西。终端设计的约束很多——80x100 字符、256 色、一种字体大小、没有鼠标交互。_terminal spinner_ 就迭代了大概 50 到 100 次，其中 80% 没发布。

[`37:14`](https://youtu.be/PQU9o_5rHC4?t=2234) 以前用 Origami 或 Framer 也许做三个原型要两周。用 Claude Code 可以做 20 个原型，选最好的，可能几个小时就完成了。

[`37:38`](https://youtu.be/PQU9o_5rHC4?t=2258) Boris 你还有什么建议？两条建议：不要为今天的模型构建，为六个月后的模型构建。模型总是通用的更好的。永远不要打赌模型做不——我们办公室挂着一幅"苦涩的教训"的副本。不要做 scaffolding（脚手架）——你可以花工程时间扩展 10-20% 的能力，或者等几个月让模型自己做。

[`39:18`](https://youtu.be/PQU9o_5rHC4?t=2358) 你多久重写一次代码？Claude Code 的所有代码一直在被反复重写。工具每几周增删一次。六个月前的代码已经不存在了。当前代码库大概 80% 不超过几个月。

[`40:02`](https://youtu.be/PQU9o_5rHC4?t=2400) Steve Yegge 发帖说在 Anthropic 工作太棒了——Anthropic 工程师的生产力是 Google 工程师巅峰时期的 1000 倍。对我们内部来说，自从 Claude Code 发布以来，每位工程师的生产力增长了 150%。这跟我在 Meta 负责代码质量时的体验完全不同——当时 2% 的生产力提升就需要几百人一年的工作。

[`41:36`](https://youtu.be/PQU9o_5rHC4?t=2496) 是什么让你来到 Anthropic？我住在日本乡下，每天早上读 Hacker News，全是 AI 的新闻。用了早期产品后被震撼了。跟 Ben Mann 聊天后被折服了。两个原因：一是它作为研究实验室运营，产品很次要，模型才是最重要的。二是使命感。我在午餐时间听到的对话都是关于 AI 安全的。

[`43:40`](https://youtu.be/PQU9o_5rHC4?t=2620) 今年会发生什么？Dario 预测 Anthropic 90% 的代码由 Claude 写。对我来说，自 Opus 4.5 以来是 100%。我卸载了 IDE，不再手写任何代码。每天 20 个 PR。软件工程师这个头衔会消失，变成 builder、产品经理或其他。每个职能都在写代码——PM、设计师、EM、财务人员。这是保守估计。上界更令人害怕——如果达到 ASL4（模型递归自我改进），我们需要确保安全。

[`46:23`](https://youtu.be/PQU9o_5rHC4?t=2783) 大家假期发现了 Claude Code，之后就疯了。你内部什么感觉？整个十二月我在旅行，每天都在写代码。Claude Code 内部增长一直是指数级的。Mercury 的数据显示 70% 的初创公司选择 Claude 作为模型。4% 的所有公共 commit 由 Claude Code 生成。NASA 用它来为火星探测器绘制航线。

[`48:12`](https://youtu.be/PQU9o_5rHC4?t=2892) Claude Code 和 Co-work 的关系？这又是一个 latent demand 的例子——有人在用 Claude Code 监控番茄植物，有人在用它从损坏的硬盘中恢复婚礼照片。设计师、财务团队、数据科学团队都在用。Co-work 就是一个带有 GUI 的桌面应用包装，底层是同一个 agent。

[`49:54`](https://youtu.be/PQU9o_5rHC4?t=2994) Boris 谢谢你创造了一个让我失去睡眠的东西，但也让我重新感受到了创造者和创始人模式的兴奋。

[`49:59`](https://youtu.be/PQU9o_5rHC4?t=2999) 谢谢邀请。记得报 bug。

---

## 来源

- [Inside Claude Code With Its Creator Boris Cherny — Y Combinator — YouTube](https://youtu.be/PQU9o_5rHC4)
- [Y Combinator](https://www.ycombinator.com/)
