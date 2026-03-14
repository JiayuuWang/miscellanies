# 2026年，我为什么继续看好 GUI-Agent？
*封面来源：Li et al., "ScreenSpot-Pro: GUI Grounding for Professional High-Resolution Computer Use", 2025*

如果你关注 AI 领域在过去一年的发展，会发现一个有趣的现象：GUI-Agent 在 2025 年迎来了一波井喷式爆发。从学术界的 Benchmark 刷榜，到工业界的巨头布局，"能操作电脑的 AI"成了当下最热门的话题之一。

[![Claude | Computer use for automating operations ](/images/claude-cua-demo.png)](https://www.youtube.com/watch?v=ODaHJzOyVCQ)
*图片来源：[Claude | Computer use for automating operations](https://www.youtube.com/watch?v=ODaHJzOyVCQ)*

但有意思的是，进入 2026 年以来，学术界开始出现一种声音：**"GUI-Agent 已经不适合继续做了"**。理由无外乎：赛道太卷、已经发展了比较长的时间、paper 越来越难中。而工业界方面，大厂亲自下台，确实都推出了自己的 GUI 产品，但引起的反响尚不如其他方向的AI产品；中国的"豆包手机"虽然一度引爆流量，却也很快归于平静。

那么，GUI-Agent 是不是真的"不行"了？

我个人的看法是：**我仍然长期看好 GUI-Agent，而且比以往任何时候都看好。**

借今天这篇文章，我想聊聊这个话题。

## 写在前面

CLI(Command Line Interface)表示命令行界面，GUI(Graphical User Interface)表示图形用户界面，他们代表了计算机发展中的两大交互界面，也代表了人机沟通方式的演变。前者通过键入精确的文本命令来操作，虽学习门槛高，但高效且资源占用低，是早期计算机及专业技术人员的基石；后者则通过直观的窗口、图标和鼠标点击来实现交互，极大地降低了使用门槛，让计算机得以普及至大众。简而言之，**CLI是“念咒语”式的专业工具，而GUI是“按遥控器”式的日常桥梁**，两者至今仍相辅相成。

[![Centralized Bash history with timestamps ](/images/cli.png)](https://www.youtube.com/watch?v=ODaHJzOyVCQ)
*图片来源：[Centralized Bash history with timestamps](https://www.unixtutorial.org/centralized-bash-history-with-timestamps/)*

GUI Agent 是一种能够像人类一样理解和操作图形用户界面的智能体。它通过模拟视觉识别（看懂屏幕上的图标、按钮）和物理交互（控制鼠标移动、点击、键盘输入）来完成复杂任务，本质上是在“观看”屏幕并“动手操作”。

与之相比，通过 CLI 操控电脑的 Agent 走的是另一条路径（目前的主流）：它依赖的是结构化的文本命令和标准化的程序接口，通过生成精确的指令字符串（比如shell 命令）来直接调用计算机的功能。

两者的核心区别在于交互方式与适应能力。CLI Agent 的操作速度快、精度高，但受限于系统必须预装相应的命令行工具，且输出格式固定；而 GUI Agent 则拥有极强的通用性，因为它模拟的是人类的使用方式，理论上可以操作任何有视觉界面的软件（包括那些根本没有 CLI 接口的旧系统或第三方应用），无需底层代码的适配，但其执行效率较低，且更依赖视觉模型的准确性。等会我们还会讨论这个话题。

## 2025 年：GUI-Agent 井喷的一年

在展开我的观点之前，让我们先回顾一下 2025 年发生了什么。

### 学术界：Benchmark 百花齐放

2025 年，GUI-Agent 相关的学术研究可以用"爆发"来形容，这一年出现了大量高质量的 Benchmark 和研究成果[1]：

- **OSWorld**：首个在真实 Ubuntu、Windows、macOS 环境中评估多模态 GUI-Agent 的 Benchmark，涵盖 369 个真实桌面任务，覆盖文件管理、办公软件、开发工具等多个场景。人类表现能达到 72.36%，而当时最好的模型只有 12.24%[2]，清楚地暴露出现有模型在 GUI grounding 和多应用协同上的巨大鸿沟。

- **AndroidWorld**：一个在真实 Android 模拟器上构建的动态基准环境，提供 116 个端到端任务、覆盖 20 个真实 App（通讯录、日历、浏览器、记账应用等）。它专门用来评估移动端 GUI-Agent 在真实设备上的操作稳定性和泛化能力，比如在分辨率变化、语言切换、系统设置不同的情况下，Agent 是否还能完成任务。

- **WorldGUI**：2026 年新发布的 Benchmark，在 Windows 桌面环境中构造了大量"从任意初始状态出发"的任务[3]。它刻意让目标软件未打开、窗口被遮挡、界面处于非默认页签等，重点考察 GUI-Agent 在动态环境中的恢复、重规划和纠错能力，而不是在理想静态界面里的"happy path"。

- **ScreenSpot-Pro**：专门针对高分辨率专业软件（如 Photoshop、Premiere Pro）的 GUI grounding 基准，包含 23 个应用、跨越 5 个行业和 3 个操作系统[4]。早期 GUI grounding 模型在这个数据集上的最佳成绩只有 18.9%[4]，之后通过视觉搜索和区域裁剪等方法，准确率被提升到 40%+，最新的 RegionFocus 方法已经把 ScreenSpot-Pro 的准确率提升到 61.6%[9]，但距离实用仍然有明显差距。

- **FineState-Bench**：专注于细粒度状态控制的 Benchmark，覆盖桌面、Web 和移动端[5]。它要求 GUI-Agent 完成诸如精确拖动滑块、选择特定颜色、只高亮某一句话等操作。实验结果显示，即便是目前最先进的 GUI-Agent，在这种精细交互上的综合准确率也只有 32.8%[5]。

这些 Benchmark 有一个共同特点：**它们都很难**。即便是最先进的多模态大模型，在这些任务上的表现与人类仍有巨大差距。但正是这种差距，意味着这个领域还有巨大的上升空间。

### 工业界：巨头纷纷入局

2025 年，工业界的动作同样令人目不暇接：

- **OpenAI Operator**：2025 年 1 月发布，能在浏览器中自主执行复杂任务，在复杂 JavaScript 网站上达到 87% 的成功率，WebArena 上 58%，OSWorld 上 38%[1]

[![Introducing Operator ](/images/openai-operator.png)](https://www.youtube.com/watch?v=ODaHJzOyVCQ)
*图片来源：[Introducing Operator](https://openai.com/zh-Hans-CN/index/introducing-operator/)*

- **Anthropic Claude Computer Use**：**2024 年 10 月**率先推出，是首个提供自主桌面控制的前沿 AI 模型。通过截屏捕获、视觉分析、动作规划、虚拟鼠标键盘执行的循环来工作[6]

- **Google Project Mariner**：2025 年 5 月向 Google AI Ultra 用户推出，基于 Gemini 2.0，在 ScreenSpot 上得分 84.0%，WebVoyager 上 83.5%[1]

- **微软 Fara-7B**：微软研究院推出的 PC 自动化模型

- **豆包手机助手**：2025 年 12 月，字节跳动推出的系统级 AI Agent，能够跨 App 执行复杂任务，一度在淘宝上被炒到近五千元[7]

开源社区也不甘示弱：

- **Mobile-Agent-v3** 和 **GUI-Owl**：在开源模型中实现了 SOTA 表现，AndroidWorld 达到 73.3%，OSWorld 达到 37.7%[8]

- **Browser Use**：开源的浏览器自动化框架，支持用 API key 调用各种模型（虽然主要应用在非 GUI 任务中，但其贡献巨大，也促进了人们对 GUI 场景的探索）

## 唱衰声中的反思

不可否认，2026 年的学术界确实出现了对 GUI-Agent 的反思。有人在 Twitter 上说"GUI-Agent 太卷了，不适合发 paper"，也确实有一些研究者开始转向其他方向。

工业界方面，一些人产生了疑问：**GUI-Agent 到底能不能落地，是不是已经到头了？**

## 为什么我仍然看好 GUI-Agent？

让我说说我的理由。

### 1. GUI 可以真正模拟人机交互，突破 CLI 的天然限制

这是我看好 GUI-Agent 最核心的原因。

CLI（命令行界面）和 API 方式有一个根本性的局限：**一旦一个系统既没有结构化接口、也无法通过 DOM/HTTP 注入脚本，只有"看屏幕+动鼠标"这一条路，传统 CLI 就很难施展拳脚**。例如很多安全敏感场景，只允许通过远程桌面或本地客户端 GUI 访问，而不会暴露任何可编程接口。

举个例子：不少大型企业把最核心的财务系统部署在内网虚拟机里，员工必须先通过 Windows 远程桌面登录，再在远程桌面里打开一款十几年前的厚客户端软件，完成报销审批、合同导出等操作——没有公开 API，也不能在页面里直接注入脚本，你甚至拿不到 DOM 结构。这种情况下，CLI 或浏览器自动化几乎无从下手，但 GUI 方法直接在远程桌面里"看屏幕→移动鼠标→点击菜单→填写表单→导出报表"，像真人一样完成整个流程。

这就是 GUI-Agent 最本质的优势：**它能做任何人类能对电脑做的事情**。鼠标点击、键盘输入、拖拽滑动、下拉选择……这些对 GUI-Agent 来说都是基本动作空间。

用更专业的话说，GUI-Agent 是**通用的计算机操作接口**。它不依赖任何特定的 API，而是直接与图形界面交互。这意味着：

- **它可以操作任何软件**：无论是 Word、Excel、Photoshop，还是某个你刚下载的冷门工具(这点也很关键，它意味着Agent维护方无需手动扩展以适应新的软件和网站)
- **它可以适应任何网站**：即使是没有 API 的个人博客、论坛，也能轻松搞定
- **它可以跨应用工作**：不同应用，甚至不同os的 UI 设计都高度相仿，这使得GUI-Agent在跨应用场景下表现出高度的通用性和灵活性

正如 Anthropic 在介绍 Computer Use 时所说："We are teaching Claude general computer skills—enabling it to use the same interfaces, applications, and workflows that humans use every day."（我们正在教会 Claude 通用的计算机技能——让它能够使用与人类相同的界面、应用程序和工作流程。）[6]

### 2. 在某些领域，GUI-Agent 能提供更好的体验

GUI-Agent 不仅仅是"更通用"，在某些特定场景下，它能提供明显更好的用户体验。

**跨 App 的视觉链路任务**：比如你需要这样一个操作链："从邮箱里打开一份 50 页的 PDF 投资报告，把其中所有被红色高亮的指标抄到本地 Excel 模板里生成图表，然后把图表截图发到企业微信里的『投资决策』群。"这里不仅涉及浏览器、PDF 阅读器、Excel、即时通讯软件之间的跳转，还有"识别红色高亮内容"和"确认图表效果是否看起来合理"这种强视觉判断。用 CLI 写脚本几乎不现实，而 GUI-Agent 可以像人一样一边看一边操作。

**高度视觉化的创意/设计工作流**：在 Figma、Photoshop、Premiere 这类工具里，很多指令是模糊的，比如"让这一页版式更紧凑一点""把人物再提亮一点但不要过曝"。这些目标很难抽象成稳定的 API 调用，但 GUI-Agent 可以通过多轮截屏和局部对比，在界面上直接拖拽、对齐、微调参数，让结果逐步逼近人类主观的"好看"。

**需要视觉确认的场景**：有时候，我们需要"看到"才能确认操作是否正确。比如 AI 帮你在后台管理系统里批量更新了一批配置，我们往往希望它能"看到页面上所有字段都变成了绿色对勾"或者"确认页面右上角出现了『发布成功』的 Toast"才认为任务完成。GUI-Agent 可以直接截屏比对这些视觉信号，而不仅仅依赖返回的 HTTP 状态码。

**非结构化内容的处理**：当你需要 AI 帮你从扫描版合同、手写单据或者一张照片中提取信息，并分别填写到浏览器里的表单、桌面 ERP 系统和本地 Excel 时，GUI-Agent 可以直接完成"看图→理解→跨应用填表"的整个链路，而不需要每个系统都提供结构化接口。

更重要的是，以上这些只是我看到的和能想象出来的应用场景，还有更多未知的场景需要大家去**发现**和**定义**。
### 3. 当前利好 GUI-Agent 发展的因素

除了上述核心优势外外部环境也发生了不少积极变化：

**模型的视觉 grounding 能力逐渐增强**

在 ScreenSpot-Pro 这个高难度 Benchmark 上，早期通用多模态模型的最佳成绩只有 18.9%[4]；随后一系列视觉搜索与区域裁剪方法将准确率提升到了 40%+，其中 RegionFocus 在 Qwen2.5-VL-72B 上已经把 ScreenSpot-Pro 的准确率提升到 61.6%[9]。2026 年发布的 UI-Venus 1.5 则进一步将这一数字推高到了 69.6%[12]。虽然还没达到人类水平，但在如此复杂的专业软件场景里，这样的进步已经非常惊人——ScreenSpot-Pro 专门针对高分辨率专业软件设计，包含 23 个应用、跨越 5 个行业和 3 个操作系统，连人类都经常感到棘手。

[![Li et al., "ScreenSpot-Pro: GUI Grounding for Professional High-Resolution Computer Use", 2025 ](/images/srceenshot-pro-task.png)](https://arxiv.org/html/2504.07981v1#bib)
*图为该数据集中的一个任务示例，人类都很难立刻找到正确的按钮！
图片来源：[Li et al., "ScreenSpot-Pro: GUI Grounding for Professional High-Resolution Computer Use", 2025](https://arxiv.org/html/2504.07981v1#bib)*

更值得注意的是，UI-TARS、Qwen3.5 等开源模型也在快速追赶。GUI-Owl-7B 能在 AndroidWorld 上达到 66.4% 的准确率，Mobile-Agent-v3 将这个数字提升到了 73.3%[8]，而 UI-Venus 1.5 在同一基准上的最新成绩已经达到 77.6%[12]。

**模型的 Agent 能力飞速增长**

2025 年是 Agent 能力爆发的一年。OpenAI 的 o1/o3 系列、Anthropic 的 Claude 4 Sonnet、Google 的 Gemini 2.5，都展示了惊人的推理和规划能力。这些能力对于 GUI-Agent 来说至关重要——毕竟，操作电脑不仅仅是"看到"就够了，还需要"想到怎么做"。

**学术研究提供了丰富的 insight**

过去一年，学术界对 GUI-Agent 的研究产生了大量有价值的 insight：

- WorldGUI 揭示了 Agent 在非默认初始状态下的脆弱性[3]
- FineState-Bench 发现顶级模型的细粒度交互准确率仅有 32.8%[5]
- 各种研究探讨了 VLM 在数字 Agent 任务中的行为逻辑，包括截图分辨率、轨迹历史的影响[2]

这些研究让我们更清楚地知道问题在哪里，也指明了前进的方向。

**GUI-Agent 不是孤立的领域**

这一点非常重要：GUI-Agent 的发展是建立在 LLM、Inference、Data 等多个领域进步之上的。这意味着什么？

**当 LLM 变得更强，GUI-Agent 会自动受益**。当多模态模型变得更擅长"看图"，GUI-Agent 的感知能力会同步提升。当推理算法变得更高效，GUI-Agent 的响应速度也会水涨船高。

**甚至当 GUI-Agent 操作的对象(比如app)变强，它的能力也随之变强**

换句话说，GUI-Agent 是一个"站在巨人肩膀上"的领域。底层技术的每一次进步，都会自动惠及 GUI-Agent。这种"顺风车"特性，让它的长期发展前景更加乐观。

## 挑战与机遇

当然，GUI-Agent 面临的挑战也不容忽视：

**稳定性问题**：目前的 GUI-Agent 在复杂任务上仍有较高的失败率。根据 WorldGUI 的研究，即使是最先进的模型，在非默认初始状态下的性能也会大幅下降[3]。

**细粒度控制**：FineState-Bench 的研究表明，当前模型在精确选择颜色值、高亮特定句子等细粒度操作上表现很差[5]。

**推理成本**：GUI-Agent 需要反复截屏、分析、决策，token 消耗远高于纯文本交互。这在大规模应用时是一个实际问题。

**安全风险**：如果 GUI-Agent 日益成熟，安全问题可能会是最值得关注的问题。让模型控制电脑本身就有安全风险，更不用说通过 GUI 了。Anthropic 在 Computer Use 中采取了多层安全措施，包括 ASL-3 分类器、沙盒环境、实时监控等[10]。

但我更愿意把这些挑战理解为**机遇**。每一个未解决的问题，都是一个潜在的研究方向，也是一个潜在的产品机会。

## 我的尝试：Auto-Cursor

2025 年末，我发起了一个 Demo 级的项目：
[Auto-Cursor](https://github.com/JiayuuWang/Auto-Cursor)。

[![Auto-Cursor ](/images/auto-cursor.png)](https://github.com/JiayuuWang/Auto-Cursor)
*图片来源：[Auto-Cursor: A GUI Agent for Cursor IDE](https://github.com/JiayuuWang/Auto-Cursor)*

这个项目的动机很简单：拓展 GUI 方法的使用场景，通过 GUI 操作 Cursor IDE。

Auto-Cursor 的形式：**让 AI 能够自主操作 Cursor**，从而实现自动化编程。你只需要告诉它一个目标（比如"把这个页面的 CSS 改成暗色主题"），它就会自己分析代码、自己通过操作 Cursor 的 UI 进行修改和测试。

它命中了上面说的 GUI 方法的优势中的第一条：突破 API 的限制。需要注意的是，Cursor 向用户开放了大量的接口权限，如获取用户和用户组的行为等等，但不允许通过脚本进行应用内的操作。

当然，这只是一个 Demo 级的小项目，还有很多不完善的地方。但它展示了 GUI-Agent 在不同领域的潜力。

## 总结

以发 paper 的角度，GUI-Agent 或许不再是增长最快的方向了。但从长远来看，它有无限潜力。

我不太愿意说 GUI-Agent 是"通往 AGI 的道路"，因为 AGI 这个词已经被用得太泛了，很难定义。但我相信，GUI-Agent 未来会成为一个强有力的工作方式，会重塑多个行业。

就像当年 CLI 取代批处理、GUI 取代 CLI 一样，AI 操作界面可能成为人机交互的下一个范式转变。而 GUI-Agent，正是这个转变的先锋。

---

**参考来源：**

[1] Zylos Research - Computer Use and GUI Agents in 2026: State of the Art (https://zylos.ai/research/2026-02-08-computer-use-gui-agents)

[2] OSWorld - Benchmarking Multimodal Agents for Open-Ended Tasks in Real Computer Environments (https://os-world.github.io/)

[3] WorldGUI - An Interactive Benchmark for Desktop GUI Automation (https://arxiv.org/html/2502.08047v4)

[4] ScreenSpot-Pro: GUI Grounding for Professional High-Resolution Computer Use (https://arxiv.org/html/2504.07981v1)

[5] FineState-Bench: A Comprehensive Benchmark for Fine-Grained State Control in GUI Agents (https://arxiv.org/html/2508.09241v1)

[6] Anthropic Computer Use API Documentation (https://www.digitalapplied.com/blog/anthropic-computer-use-api-guide)

[7] 机器之心 - 「豆包手机」为何能靠超级Agent火遍全网 (https://news.qq.com/rain/a/20251210A056UI00)

[8] Mobile-Agent-v3: Fundamental Agents for GUI Automation (https://arxiv.org/abs/2508.15144)

[9] RegionFocus: Visual Test-time Scaling for GUI Agent Grounding (https://arxiv.org/html/2505.00684v2)

[10] Bosio Digital - The Agent Arms Race (https://bosio.digital/articles/agent-arms-race-openai-anthropic-google)

[11] Awesome Agents - Cursor Launches Always-On AI Coding Agents (https://awesomeagents.ai/news/cursor-automations-agentic-coding-agents/)

[12] UI-Venus-1.5 Technical Report & GitHub (https://github.com/inclusionAI/UI-Venus)
