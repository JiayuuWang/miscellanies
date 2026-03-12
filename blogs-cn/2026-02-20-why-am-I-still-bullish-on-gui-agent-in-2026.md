# 2026年，我为什么继续看好 GUI-Agent？

如果你关注 AI 领域在过去一年的发展，会发现一个有趣的现象：GUI-Agent 在 2025 年迎来了一波井喷式爆发。从学术界的 Benchmark 刷榜，到工业界的巨头布局，"能操作电脑的 AI"成了当下最热门的话题之一。

但有意思的是，进入 2026 年以来，学术界开始出现一种声音：**"GUI-Agent 已经不适合继续做了"**。理由无外乎：赛道太卷、已经发展了比较长的时间、paper 越来越难中。而工业界方面，各大洋巨头确实都推出了自己的 GUI 产品，但引起的反响尚不如其他方向的AI产品；中国的"豆包手机"虽然一度引爆流量，却也很快归于平静。

那么，GUI-Agent 是不是真的"不行"了？

我个人的看法是：**我仍然长期看好 GUI-Agent，而且比以往任何时候都看好。**

借今天这篇文章，我想聊聊这个话题。

## 写在前面

CLI(Command Line Interface)表示命令行界面，GUI(Graphical User Interface)表示图形用户界面，他们代表了计算机发展中的两大交互界面，也代表了人机沟通方式的演变。前者通过键入精确的文本命令来操作，虽学习门槛高，但高效且资源占用低，是早期计算机及专业技术人员的基石；后者则通过直观的窗口、图标和鼠标点击来实现交互，极大地降低了使用门槛，让计算机得以普及至大众。简而言之，**CLI是“念咒语”式的专业工具，而GUI是“按遥控器”式的日常桥梁**，两者至今仍相辅相成。

GUI Agent 是一种能够像人类一样理解和操作图形用户界面的智能体。它通过模拟视觉识别（看懂屏幕上的图标、按钮）和物理交互（控制鼠标移动、点击、键盘输入）来完成复杂任务，本质上是在“观看”屏幕并“动手操作”。

与之相比，通过 CLI 操控电脑的 Agent 走的是另一条路径（目前的主流）：它依赖的是结构化的文本命令和标准化的程序接口，通过生成精确的指令字符串（比如shell 命令）来直接调用计算机的功能。

两者的核心区别在于交互方式与适应能力。CLI Agent 的操作速度快、精度高，但受限于系统必须预装相应的命令行工具，且输出格式固定；而 GUI Agent 则拥有极强的通用性，因为它模拟的是人类的使用方式，理论上可以操作任何有视觉界面的软件（包括那些根本没有 CLI 接口的旧系统或第三方应用），无需底层代码的适配，但其执行效率较低，且更依赖视觉模型的准确性。等会我们还会讨论这个话题。

## 2025 年：GUI-Agent 井喷的一年

在展开我的观点之前，让我们先回顾一下 2025 年发生了什么。

### 学术界：Benchmark 百花齐放

2025 年，GUI-Agent 相关的学术研究可以用"爆发"来形容，这一年出现了大量高质量的 Benchmark 和研究成果[1]：

- **OSWorld**：首个在真实 Ubuntu、Windows、macOS 环境中评估多模态 Agent 的 Benchmark，涵盖 369 个真实任务。人类表现能达到 72.36%，而当时最好的模型只有 12.24%[2]

- **AndroidWorld**：在真实的 Android 模拟器上构建和评估自主 Agent 的环境

- **WorldGUI**：2026 年新发布的 Benchmark，关注动态环境下的 Agent 适应能力[3]

- **ScreenSpot-Pro**：专门针对高分辨率专业软件（如 Photoshop、Premiere Pro）的 GUI  grounding 基准，目前最佳模型只有 18.9% 的准确率[4]

- **FineState-Bench**：专注于细粒度状态控制的 Benchmark，顶级模型在细粒度交互上的准确率仅有 32.8%[5]

这些 Benchmark 有一个共同特点：**它们都很难**。即便是最先进的多模态大模型，在这些任务上的表现与人类仍有巨大差距。但正是这种差距，意味着这个领域还有巨大的上升空间。

### 工业界：巨头纷纷入局

2025 年，工业界的动作同样令人目不暇接：

- **OpenAI Operator**：2025 年 1 月发布，能在浏览器中自主执行复杂任务，在复杂 JavaScript 网站上达到 87% 的成功率，WebArena 上 58%，OSWorld 上 38%[1]

- **Anthropic Claude Computer Use**：**2024 年 10 月**率先推出，是首个提供自主桌面控制的前沿 AI 模型。通过截屏捕获、视觉分析、动作规划、虚拟鼠标键盘执行的循环来工作[6]

- **Google Project Mariner**：2025 年 5 月向 Google AI Ultra 用户推出，基于 Gemini 2.0，在 ScreenSpot 上得分 84.0%，WebVoyager 上 83.5%[1]

- **微软 Fara-7B**：微软研究院推出的 PC 自动化模型

- **豆包手机助手**：2025 年 12 月，字节跳动推出的系统级 AI Agent，能够跨 App 执行复杂任务，一度在淘宝上被炒到近五千元[7]

开源社区也不甘示弱：

- **Mobile-Agent-v3** 和 **GUI-Owl**：在开源模型中实现了 SOTA 表现，AndroidWorld 达到 73.3%，OSWorld 达到 37.7%[8]

- **Browser Use**：开源的浏览器自动化框架，支持用 API key 调用各种模型

## 唱衰声中的反思

不可否认，2026 年的学术界确实出现了对 GUI-Agent 的反思。有人在 Twitter 上说"GUI-Agent 太卷了，不适合发 paper"，也确实有一些研究者开始转向其他方向。

工业界方面，一些人产生了疑问：**GUI-Agent 到底能不能落地，是不是已经到头了？**

## 为什么我仍然看好 GUI-Agent？

让我说说我的理由。

### 1. GUI 可以真正模拟人机交互，突破 CLI 的天然限制

这是我看好 GUI-Agent 最核心的原因。

CLI（命令行界面）和 API 方式有一个根本性的局限：**它只能做 API 封装者允许你做的事**。如果你想调用某个服务的 API，但服务提供商没有提供相应的接口，那你就只能干瞪眼。

举个例子：你想让 AI 帮你订一张机票。如果对方只提供了网页预订入口（没有 API），CLI 方式的 AI 根本无从下手。但 GUI-Agent 不一样——它可以直接操作浏览器，像真人一样点击"搜索""预订""支付"按钮。

这就是 GUI-Agent 最本质的优势：**它能做任何人类能对电脑做的事情**。鼠标点击、键盘输入、拖拽滑动、下拉选择……这些对 GUI-Agent 来说都是基操。

用更专业的话说，GUI-Agent 是**通用的计算机操作接口**。它不依赖任何特定的 API，而是直接与图形界面交互。这意味着：

- **它可以操作任何软件**：无论是 Word、Excel、Photoshop，还是某个你刚下载的冷门工具
- **它可以适应任何网站**：即使是没有 API 的个人博客、论坛，也能轻松搞定
- **它可以跨应用工作**：在多个软件之间传递数据、协同工作

正如 Anthropic 在介绍 Computer Use 时所说："We are teaching Claude general computer skills—enabling it to use the same interfaces, applications, and workflows that humans use every day."（我们正在教会 Claude 通用的计算机技能——让它能够使用与人类相同的界面、应用程序和工作流程。）[6]

### 2. 在某些领域，GUI-Agent 能提供更好的体验

GUI-Agent 不仅仅是"更通用"，在某些特定场景下，它能提供明显更好的用户体验。

**跨 App 的复杂任务**：想象一下，你需要完成这样一个任务："帮我查一下北京到上海的机票，选最便宜的，国航的，下午3点以后的，然后截图发给微信上的张三。"这种跨多个应用的长链条任务，CLI 方式很难处理，但 GUI-Agent 可以优雅地完成。

**操作不可编程的软件**：很多企业内部系统、财务软件、政府网站，并没有提供 API 接口。对这些系统进行自动化改造，GUI-Agent 是为数不多的可行方案之一。

**需要视觉确认的场景**：有时候，我们需要"看到"才能确认操作是否正确。比如 AI 帮你填了一个表单，我们需要它"看"到提交成功的提示才算完成。GUI-Agent 可以直接截屏确认，一目了然。

**非结构化内容的处理**：当你需要 AI 帮你从一张图片中提取信息并填写到表单里时，GUI-Agent 可以直接"看图→操作"，一步到位。

### 3. 当前利好 GUI-Agent 发展的因素

除了上述核心优势外外部环境也发生了不少积极变化：

**模型的视觉 grounding 能力逐渐增强**

几年前的 AI，看图都费劲，更别说精确定位屏幕上的按钮了。但现在不一样了。

根据最新的数据，在 ScreenSpot-Pro 这个高难度 Benchmark 上，最先进的模型已经能达到 48%-61% 的准确率[4][9]。虽然还没达到人类水平，但进步是惊人的——这个 Benchmark 专门针对高分辨率专业软件设计，包含 23 个应用、跨越 5 个行业和 3 个操作系统，连人类都经常感到棘手。

更值得注意的是，UI-TARS、Qwen2.5-VL 等开源模型也在快速追赶。GUI-Owl-7B 能在 AndroidWorld 上达到 66.4% 的准确率，Mobile-Agent-v3 更是将这个数字提升到了 73.3%[8]。

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

**当 LLM 变得更强，GUI-Agent 会自动受益**。当多模态模型变得更擅长"看图"，GUI-Agent 的感知能力会同步提升。当推理算法变得更高效，GUI-Agent 的规划能力也会水涨船高。

换句话说，GUI-Agent 是一个"站在巨人肩膀上"的领域。底层技术的每一次进步，都会自动惠及 GUI-Agent。这种"顺风车"特性，让它的长期发展前景更加乐观。

## 挑战与机遇

当然，GUI-Agent 面临的挑战也不容忽视：

**稳定性问题**：目前的 GUI-Agent 在复杂任务上仍有较高的失败率。根据 WorldGUI 的研究，即使是最先进的模型，在非默认初始状态下的性能也会大幅下降[3]。

**细粒度控制**：FineState-Bench 的研究表明，当前模型在精确选择颜色值、高亮特定句子等细粒度操作上表现很差[5]。

**推理成本**：GUI-Agent 需要反复截屏、分析、决策，token 消耗远高于纯文本交互。这在大规模应用时是一个实际问题。

**安全风险**：让 AI 控制电脑本身就有安全风险。Anthropic 在 Computer Use 中采取了多层安全措施，包括 ASL-3 分类器、沙盒环境、实时监控等[10]。

但我更愿意把这些挑战理解为**机遇**。每一个未解决的问题，都是一个潜在的研究方向，也是一个潜在的产品机会。

## 我的尝试：Auto-Cursor

说了这么多理论，也该聊聊实践了。

2025 年末，我发起了一个 Demo 级的项目：[Auto-Cursor](https://github.com/JiayuuWang/Auto-Cursor)。

这个项目的动机很简单：Cursor 是一款非常强大的 AI 编程工具，但它本质上还是一个"工具"——你需要手动告诉它要做什么。有没有办法让它更主动、更自动化？

Auto-Cursor 的想法是：**让 AI 能够自主操作 Cursor**，从而实现真正的自动化编程。你只需要告诉它一个目标（比如"把这个页面的 CSS 改成暗色主题"），它就会自己分析代码、自己修改、自己测试。

当然，这只是一个 Demo 级的小项目，还有很多不完善的地方。但它展示了 GUI-Agent 在软件工程领域的潜力。

## 未来展望

说了这么多，让我们来想象一下 GUI-Agent 会对各行各业产生什么影响。

**软件工程**：这是最直接的应用场景。想象一下，AI 不仅能帮你写代码，还能自己操作 IDE、自己运行测试、自己提交 PR。微软已经在这个方向上迈出了第一步——Copilot 和 Claude Code 都在向这个目标努力[10]。Cursor 最近推出的 Automations 功能，已经可以基于 GitHub PR、Slack 消息等触发自动化的代码审查和安全审计[11]

**UI/UX 设计**：AI 能否自己操作 Figma、Sketch 来完成设计稿？目前已经有团队在尝试用 GUI-Agent 自动化设计流程的某些环节。

**安全测试**：渗透测试、漏洞扫描……这些工作需要操作各种工具和界面。GUI-Agent 可以帮助自动化这些流程，甚至发现人类容易遗漏的问题。

**RPA（机器人流程自动化）**：传统 RPA 依赖预设的规则，一旦界面变化就可能失效。GUI-Agent 有更强的泛化能力，或许能让 RPA 变得更加智能和鲁棒。

**无障碍访问**：对于视障人士来说，GUI-Agent 或许能成为他们的"数字眼睛"，帮助他们操作电脑和手机。

## 总结

我知道，看完这篇文章，可能还是会有人说："你说得都对，但 GUI-Agent 真的能改变世界吗？"

我的回答是：**也许不会直接改变世界，但它会改变我们工作的方式。**

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
