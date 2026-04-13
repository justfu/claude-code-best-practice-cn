# 用 Boris Cherny 构建 Claude Code — The Pragmatic Engineer

Boris Cherny ([@bcherny](https://x.com/bcherny))，Claude Code 创始人，在 The Pragmatic Engineer 播客的采访文字记录，发布于 2026 年 3 月 4 日。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 视频详情

- **嘉宾：** Boris Cherny（Claude Code 创始人）
- **主持人：** Gergely Orosz（The Pragmatic Engineer）
- **发布日期：** 2026 年 3 月 4 日
- **YouTube：** [在 YouTube 上观看](https://youtu.be/julbw1JuAz0)

---

## 文字记录

[`0:01`](https://youtu.be/julbw1JuAz0?t=1) 你是 O'Reilly 第一本 TypeScript 书的作者。

[`0:04`](https://youtu.be/julbw1JuAz0?t=4) 是的，我在日本的一个小镇找到了那本书的日文翻译版，那是超酷的时刻。然后我发现自己完全不记得 TypeScript 了。现在 Claude Code 写了 Anthropic 大约 80% 的代码。我每天写大概 10-20 个 PR。Opus 4.5 和 Claude Code 写了每一个的 100%。我没有手动编辑任何一行。

[`0:22`](https://youtu.be/julbw1JuAz0?t=22) Andre Carpety 发帖说他从来没有像现在这样作为程序员感觉如此落后。

[`0:26`](https://youtu.be/julbw1JuAz0?t=26) 这确实是我很纠结的事情。模型进步得太快，旧模型上有效的方法在新模型上可能不行。我对这个时代的一个比喻是 15 世纪的印刷术——有一群懂写字的抄写员。

[`0:42`](https://youtu.be/julbw1JuAz0?t=42) 有些雇佣抄写员的国王自己都是文盲。

[`0:45`](https://youtu.be/julbw1JuAz0?t=45) 如果想想抄写员发生了什么——他们不再是抄写员了，但现在有了作家和作者这个类别。这些人存在是因为文学市场——当你加入一家顶级 AI 实验室，你的第一个 PR 被拒了，不是因为代码不好，而是因为你手写的。Boris Cherny 加入 Anthropic 时就经历了这个。Boris 是 Claude Code 的创始人和工程负责人。在加入 Anthropic 之前，他在 Meta 工作七年，负责 Instagram、Facebook、WhatsApp 和 Messenger 的代码质量。

[`2:14`](https://youtu.be/julbw1JuAz0?t=134) 你是怎么进入科技、软件工程和编码世界的？大概在我 13 岁的时候，我开始在 eBay 上卖旧的宝可梦卡。我发现可以在 eBay 上写 HTML。我看到别人的宝可梦卡列表有漂亮的颜色和字体。然后我发现了 blink 标签。如果加上 blink 标签，我的卡能卖 99 美分而不是 49 美分。第二件事是初中的 TI-83 图形计算器——我把数学考试的答案编程到计算器里。后来考试变难了，我得编程解题器而不是直接存答案。数学变得更高级，我得从 Basic 降到汇编语言让程序跑得更快。

[`3:28`](https://youtu.be/julbw1JuAz0?t=208) 你在高中就降到汇编了？大概是初中或高中吧。然后班上其他人开始发现我有解题器。我买了一根串口线分给他们。下一次数学考试全班都拿了 A。老师说怎么回事？后来她发现了——你蒙混过一次，下次不许了。

[`4:54`](https://youtu.be/julbw1JuAz0?t=294) 你怎么决定从一个创业公司到另一个？凭感觉。创业从来不是线性路径。你总是在 pivot。你得搞清楚市场想要什么，用户想要什么。在医疗软件公司 Agile Diagnosis，我们为医生做了可视化决策树软件。我骑摩托车去 UCSF 跟着医生观察，发现医生根本没有时间坐下来用电脑——5 分钟内要看完一个病人，走到电脑前，开机 3 分钟，打开 IE6 又 30 秒，登录我们的应用，5 分钟就没了。

[`8:31`](https://youtu.be/julbw1JuAz0?t=511) 我觉得不同类型的工程师有不同的方式。在团队里有人像 Jared Sumar，技术能力惊人。对我来说工程一直是个实用的事情。我一直是个通才——设计、工程、用户研究，什么都做。

[`11:39`](https://youtu.be/julbw1JuAz0?t=699) 在 Facebook 你工作了七年，四次晋升。Facebook Groups 是我第一个项目。当时这个社区连接的使命吸引了我。我以前是 Reddit 重度用户，因为我不认识其他写代码的人。在 Reddit 上找到志同道合的人是超令人兴奋的。后来我成为 Facebook Groups 的技术负责人，组织在成长，工作从构建变成了大量的文档撰写和协调。

之后我去了 Instagram。因为妻子拿到了日本奈良的工作邀请。12 小时时差。我加入了东京的 Instagram 小团队，跟 Will Bailey 一起。Instagram 的技术栈跟 Facebook 比简直是灾难——Python，类型检查器不工作，click to definition 不工作。所以我开始做 Dev Infra，推动从 Python 迁移到 Facebook 的 monolith，从 REST 迁移到 GraphQL。

[`17:17`](https://youtu.be/julbw1JuAz0?t=1037) Zuck 要求每个工程师 20% 的时间花在修复技术债务上。我们叫它"更好的工程"（Better Engineering）。我负责协调所有这些。代码质量对工程生产力有两位数百分比的贡献。

[`18:04`](https://youtu.be/julbw1JuAz0?t=1084) 你怎么衡量的？我们做因果分析和因果推断。比如 Meta 从远程办公回到办公室，部分就是基于这个数据驱动的决定。

[`19:55`](https://youtu.be/julbw1JuAz0?t=1195) 你加入 Anthropic 后第一个 PR 被 Adam Wolf 拒了。他是我入职导师。我手写了第一个 PR，因为我觉得就该这么写。Adam 说你不应该手写，用 Clyde。Clyde 是 Claude Code 的前身，很粗糙，是 Python 的，启动要 40 秒。但 prompt 得当的话它能帮你写代码。它一次性就生成了一个能用的 PR。这是我第一次在 Anthropic 的"wow"时刻。

[`23:56`](https://youtu.be/julbw1JuAz0?t=1436) 现在的理解方式是理解模型。工程师是早期采用者。当我们从对话式 AI 转向 agentic AI 时，工程师很快理解了。而非工程师对 AI 的理解还停留在聊天机器人。

[`26:01`](https://youtu.be/julbw1JuAz0?t=1561) 模型就是想要使用工具。当时人们对 AI 编码的心智模型是——你把模型放进一个盒子里，定义接口。这不是正确的方式。模型是它自己的东西——你给它工具、程序，让它运行，不要把它做成更大系统的组件。这其实是"苦涩的教训"的一个推论——让模型自己干。

[`27:14`](https://youtu.be/julbw1JuAz0?t=1634) 你先是给了它 bash，然后是文件系统，再是更多工具。是的，前三个月只有我一个人，后来团队才成长。我们是否应该把 Claude Code 保留在内部？因为它让我们的生产力大幅提高。最终决定是发布，以便在真实世界中研究安全性。事后看这完全是正确的决定。

[`28:53`](https://youtu.be/julbw1JuAz0?t=1733) 我们是研究实验室，是安全实验室。产品是附属的，产品存在是为了更好地服务研究和让模型更安全。

[`30:15`](https://youtu.be/PQU9o_5rHC4?t=1815) 现在每个技术员工每天都在用 Claude Code，几乎是 100%。非技术员工也越来越接近 100%。一半的销售团队都在用。Dario 问为什么增长这么快，是不是在强制使用？我说没有，我们提供工具，人们用脚投票。

[`31:09`](https://youtu.be/julbw1JuAz0?t=1869) 从什么时候开始 Claude Code 写了你所有的代码？使用 Opus 4.5 后瞬间切换的。我卸载了 IDE，因为不再需要了。我后来才意识到我一个月都没用过 IDE 了。

[`32:17`](https://youtu.be/julbw1JuAz0?t=1937) 说实话它写的代码比我好。我想保留一点自尊心，但可能是真的。

[`33:15`](https://youtu.be/julbw1JuAz0?t=1995) 谈谈你的开发工作流。没有一种正确的方式。我们有五个终端 tab，每个有独立的代码库 checkout。几乎每次都从 plan mode 开始（Shift+Tab 两次）。用完 tab 后溢出到桌面应用，它内置了 worktree 支持。iOS app 是另一个惊喜——每天早上醒来在手机上启动几个 agent。

[`37:14`](https://youtu.be/julbw1JuAz0?t=2234) 用 plan mode 进入后，给个 prompt，它开始 chugging 的时候去第二个 tab 启动第二个。然后再第三个、第四个。当第一个完成时回去看。这是高效的方式。

[`38:42`](https://youtu.be/julbw1JuAz0?t=2322) 你的 PR 数量惊人。每个 PR 的复杂度？有的几行，有的几千行，完全不同。以前在 Instagram 我是产出最高的工程师之一。现在每天 20-30 个 PR，但每个都完全不同——有些几千行，有些几百行，有些一行。没有代码迁移类的了，Claude 自己做那些。

[`40:27`](https://youtu.be/julbw1JuAz0?t=2427) 代码审查怎么办？以前我做最多产的代码审查者之一。每次我需要评论什么就记到电子表格里，当某个问题出现三到四次就写一个 lint 规则来自动化。Claude 其实非常擅长写 lint 规则。现在当同事提交 PR 时，我直接 @Claude 在他们的 PR 上写一个 lint 规则。我们还运行 Claude agent SDK 在 CI 中——每个 PR 都由 Claude Code 审查，能抓到大概 80% 的 bug。Claude 会自动修复一些，不确定的留给人类。始终有工程师做第二轮审查。

[`43:23`](https://youtu.be/julbw1JuAz0?t=2603) 是不是每个项目都应该这样？每个进入生产的东西工程师都会看一眼吗？对于个人 side project 你可以直接推到 main。对于企业产品——我们的主要客户群是企业，安全性和隐私非常重要。所以我们必须有人工审查。

[`44:06`](https://youtu.be/julbw1JuAz0?t=2646) LLM 是非确定性的。怎么处理？我们用 type checker、linter、运行 build。这些都是确定性步骤。还可以做 best-of-N，让它多次通过。我们的 lint 规则 100% 由 Claude 写。

[`45:14`](https://youtu.be/julbw1JuAz0?t=2714) 我以前在电子表格里记录问题，现在直接 @Claude 写 lint 规则。很管用。

[`1:24:00`](https://youtu.be/julbw1JuAz0?t=5040) 在那个小镇找到日文翻译版的书是很酷的时刻。然后我发现我不记得 TypeScript 了。TypeScript 的类型系统有一种美——条件类型、literal type，连 Haskell 都没有这么极端。

[`1:25:57`](https://youtu.be/julbw1JuAz0?t=5157) 我对当前时代的比喻是 15 世纪的印刷术。抄写员是一个很小的精英群体，被国王雇佣，国王自己可能都不识字。欧洲识字率不到 1%。印刷术出现后 30-50 年，印刷材料的成本降低了约 100 倍。50-100 年后数量增加了约 10000 倍。识字率达到约 70%，但这花了 200-300 年，因为学习读写很难。

[`1:28:13`](https://youtu.be/julbw1JuAz0?t=5293) 有些国王自己是文盲却雇佣抄写员——就像企业主知道想构建什么，但自己不能写代码。如果他们能直接表达和读写信件，就不需要中间人了。

[`1:29:44`](https://youtu.be/PQU9o_5rHC4?t=5384) 抄写员并没有消失，他们变成了作家和作者。市场扩大了。

[`1:30:13`](https://youtu.be/PQU9o_5rHC4?t=5413) 谁在你身边脱颖而出？这是我职业生涯中遇到过最强的一群人。有很棒的 prototyper，有擅长找 PMF 的人，还有跨学科的 hybrid——跨越产品和工程、设计和工程。

[`1:31:15`](https://youtu.be/PQU9o_5rHC4?t=5475) 哪个信念从去年到现在改变了？我不确定安全问题有多重要。我加入 Anthropic 是因为我读了很多科幻小说，知道这如果走偏会有多糟。但从内部看到过去一年出现的新风险后，我变得更加担忧了。现在这是对我来说最重要的事。

什么技能仍然有价值？仍然有价值的是方法论驱动和假设驱动——在产品设计中如此，在日常工程（如调试）中也是如此。好奇心和超越泳道做事情的能力也更有价值。下一个十亿美元的创业公司可能就是一个人有一个很酷的想法，他的大脑能跨越工程、产品和商业来思考。我认为这将是通才的一年。另一个被奖励的技能是注意力短暂——现在的工作是在多个 Claude 之间跳转，是 context switching 的能力。适应性也很重要——每个新模型出来都会改变，你需要好奇并适应。

[`1:35:25`](https://youtu.be/PQU9o_5rHC4?t=5725) 推荐什么书？刘慈欣——不只是《三体问题》，他的短篇小说更好。Charles Stross 的《Accelerondo》——基本上是未来 50 年的产品路线图。从起飞开始，AI 奇点，最后以一群龙虾意识环绕木星结束。技术方面推荐《Functional Programming in Scala》——即使语言选择不再那么重要，函数式编程的思维方式教你更好地编码和用类型思考。

[`1:36:45`](https://youtu.be/julbw1JuAz0?t=5805) Boris，太棒了。我一直回到你的印刷术比喻——中世纪的抄写员是一小群精英，被国王雇佣，国王自己可能是文盲。我们软件工程师可能处于类似的位置。但抄写员并没有消失，他们变成了作家和作者，整个书面作品市场扩大了。这给了我希望。

---

## 来源

- [Building Claude Code with Boris Cherny — The Pragmatic Engineer — YouTube](https://youtu.be/julbw1JuAz0)
- [The Pragmatic Engineer](https://newsletter.pragmaticengineer.com/)
