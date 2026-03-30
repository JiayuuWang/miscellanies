# 经历一场 vibe coding 面试后，我的所思所想
*封面来源：opensessions*

几天前，我参加了一场 vibe coding 面试考核，给了一份题单，每道题都是让你用 AI 工具端到端地实现一个完整的项目。这些题目选材多样且新颖，要求也不低，不仅要一一实现列举的各项功能，还要兼顾视觉呈现和用户体验。题目被附上不同的难度标签和建议时间，和力扣、牛客等刷题平台类似，但最大的不同，前者直接考察候选人使用 AI 工具的能力。我将在不透露隐私信息的情况下，分享一下我的开发过程和一些感受。

一句话总结：**vibe coding 应被当作一个严肃的话题看待，良好的 vibe coding 能力能大大增强开发者的竞争力。**

## 什么是 Vibe Coding？

这个词由 AI 研究员 Andrej Karpathy 在 2025 年 2 月首次提出[1]。他这样描述这种工作方式：**"完全顺着感觉来，拥抱指数级增长，甚至忘掉代码的存在。"** 在实践层面，vibe coding 意味着开发者不再逐行编写代码，而是用自然语言向 AI 描述想要的功能，让 AI 来生成、迭代和调试代码，开发者则专注于产品目标、视觉呈现和用户体验。

[![Vibe Coding](/images/vibecodingtweet.png)](https://x.com/karpathy/status/1886192184808149383)
*Andrej Karpathy 原帖
图片来源：[Vibe Coding](https://x.com/karpathy/status/1886192184808149383)*

可以把它理解为一种"指挥者而非演奏者"的编程方式。

随着这种工作方式的兴起，招聘市场也开始出现变化：越来越多的公司（尤其是初创公司）开始在技术面试中加入"vibe coding 环节"，直接考察候选人使用 AI 工具高效交付产品的能力[2]。我参加的这场考核，正是这一趋势的体现。

## 我的开发过程

### 第一步：用端到端应用生成工具快速搭建雏形

拿到题目后，我没有直接开始写代码，而是先把题目信息消化、加工，整理成结构清晰的需求描述，再丢给 **Replit**（https://replit.com）这类端到端的应用生成工具。

Replit 是一个集 IDE、运行环境、部署平台于一体的在线开发平台。它的核心是 **Replit Agent**——一个能够根据自然语言提示，自主规划、编写、测试、调试并部署全栈应用的 AI Agent[3]。你告诉它"帮我做一个支持多用户登录的任务管理应用"，它就能端到端地给你一个可以跑起来的产品。

[![Replit](/images/replit.png)](https://replit.com/)
*Replit 官网
图片来源：[Vibe Coding](https://replit.com/)*

类似的工具还有：

**Bolt.new（by StackBlitz）**：以"代码优先"为理念，在浏览器内提供完整的 IDE 体验，框架灵活性极高，适合希望保留代码控制权的开发者。

**Lovable**：专注于 SaaS MVP 的构建，与 Supabase 深度集成，有可视化编辑模式，适合想要快速上线 SaaS 产品的创业者。

**v0（by Vercel）**：专注于 UI 组件生成，擅长输出高质量的前端设计，与 Next.js 生态深度集成，适合前端开发者和设计师。

**Base44**：极简配置，以最少决策实现最快上线，适合完全不懂技术的创始人[4]。

这类工具共同的优点是**速度快、门槛低、整合完善**——你不需要配置环境，不需要操心托管和部署，专注于产品逻辑即可。但它们也有明显的缺点：**平台锁定**是最大的问题。Replit 生成的代码天然适配 Replit 默认的配置和集成（比如它的 PostgreSQL 数据库、自带的 Auth 系统），一旦想迁移到其他环境，就需要做不少重构工作——这正是我在第二步遇到的麻烦。

### 第二步：迁移到 Claude Code 进行精细调整

有了雏形之后，我把代码迁移到了本地，使用 **Claude Code** 进行更细化的调整和功能打磨。

这个迁移过程并不顺利。Replit 生成的代码里有很多对其平台环境的隐式依赖——环境变量的注入方式、数据库连接的配置路径、部署钩子等等，都需要一一适配本地环境。这段时间花了不少精力，也让我深刻体会到：**选择工具链的时候要提前考虑"出口"**，频繁的代码迁移会消耗大量时间。

### 第三步：在 Claude Code 中反复测试和调试

迁移完成后，进入了密集的测试-调试-迭代循环...
## 我的工具配置

我在这次考核中的工具配置非常简洁：

**Replit**：Core 用户，默认配置，用于快速生成应用雏形。

**Claude Code**：配置总体也很简洁，有几个值得分享的细节：
- **关键命令需要人类确认**：对于执行文件删除、推送代码、修改配置等高风险操作，我配置为必须手动确认，避免 AI 在我不知情的情况下做出不可逆的操作；
- **自建 PROJECT.md**：里面是完全未改动的题目要求原文，用于让 Claude Code 在开发过程中随时对照，防止"目标漂移"；
- **两个终端，两个 Claude Code 实例**：一个专门负责构建和 debug，另一个专门负责功能测试，两者的对话历史相互隔离（注意：本地持久化的 .md 文件和系统提示词还是共享的），这样可以避免上下文污染，保持各自思路的清晰。

## 主流 AI 编程工具横向对比

借这个机会，我来梳理一下目前主流的 AI 编程工具格局，按呈现形式分为三类：

### 类型一：端到端应用生成工具

代表：**Replit**、**Bolt.new**、**Lovable**、**v0**、**Base44**

核心定位是**从自然语言到可部署应用的全链路生成**。适合快速原型、MVP 验证、非技术人员建站。优点是速度极快、几乎零配置；缺点是平台锁定风险高，生成代码的架构质量参差不齐，复杂项目容易遇到"维护墙"。

### 类型二：AI IDE

代表：**Cursor**、**Trae（字节跳动出品）**、**Windsurf（前身为 Codeium）**

这类工具是在传统 IDE（通常基于 VS Code）的基础上深度集成 AI 能力，让开发者在熟悉的开发环境中享受 AI 辅助[5]。

- **Cursor**：面向专业开发者的"重型武器"，代码库索引深度高，支持多模型切换（Claude、GPT、Gemini 等），Composer 功能可以跨文件批量编辑。
- **Windsurf**：界面流畅，上手门槛低，免费套餐慷慨，以"协作式 AI"为卖点，擅长 React/Next.js 等现代 Web 框架。
- **Trae**：字节跳动出品，强调自主 Agent 工作流，适合需要 AI 自主完成整个功能模块的团队。

### 类型三：CLI 型 Agent

代表：**Claude Code**、**OpenCode**、**Aider**

这类工具在终端中运行，是真正的"代码库级别"AI——它们理解整个项目的上下文，而不局限于单个文件[6]。优点是上下文理解深度高、与 Git 工作流天然契合、适合复杂项目的精细打磨；缺点是学习曲线相对陡峭，对命令行不熟悉的用户上手有难度。

## 核心思考

### 避免频繁的代码迁移

这次经历给我最深的教训之一：**工具的选择应该在项目开始前就确定好，并尽量一贯到底**。

从 Replit 生成的代码迁移到本地 Claude Code 环境，表面上看只是换了个开发工具，实际上背后涉及大量的"去平台化"工作：环境变量管理方式的迁移、数据库驱动的切换、认证系统的重写……每一项都要花时间，而这些时间本可以用在功能开发上。

一个更好的工作流应该是：**在开始之前，就决定好你的最终运行环境和代码仓库位置，然后选择与之兼容性最好的生成工具**。如果最终代码要落在 GitHub 并部署到 Vercel，那么 Lovable（原生支持 GitHub 同步）或 Bolt.new 可能比 Replit 更合适；如果不在乎平台锁定，只追求速度，Replit 和 Base44 是最快的选择。

### Vibe Coding 是一项严肃的技能

我认为一个值得强调的观点是：**vibe coding 不等于"随便玩玩"，它是一项需要认真对待的专业能力**。

能把 AI 工具用得好的人，绝不只是会打字，背后需要：

**清晰的需求分解能力**：AI 无法处理模糊的需求。你必须能把一个"帮我做一个类似 Notion 的应用"拆解成清晰、可操作的功能列表和优先级排序，否则 AI 生成的东西会朝着错误方向越走越偏。

**系统性的架构判断力**：AI 生成的代码往往能跑，但不一定好维护、可扩展或安全。你需要有足够的技术判断力，识别出哪些生成代码是"危险的捷径"，哪些是合理的实现。

**高效的上下文管理**：无论是 PROJECT.md、CLAUDE.md，还是对多个 Agent 实例的任务分工，本质上都是在**管理 AI 的认知边界**。上下文管理做得好，AI 就像一个了解全局的靠谱同事；做得差，AI 就是一个不断走弯路的迷路者。

**迭代测试的节奏感**：Vibe coding 的精髓不是"一次生成、一键完成"，而是**快速迭代、持续验证**。你要能快速判断每一次生成的结果是否符合预期，发现问题后及时修正方向，而不是等到项目末期才发现整体架构跑偏了。

正如一位资深工程师所说：**"Vibe coding 降低了写代码的门槛，但提高了'会用 AI'的门槛。"** 工程判断力、需求分析能力、系统架构素养——这些东西 AI 替代不了，反而因为 AI 的存在变得更加关键[7]。Anthropic的核心技术总管 Boris Cherny 在一次博客里提到："现在 Vide coding 能力最强的人恰恰是公司里最会写代码的人。"

## 其他知名开发者的感受

这场 vibe coding 浪潮，也引发了行业内不少讨论，我摘录了几个我认为比较有代表性的声音。

**Andrej Karpathy（vibe coding 概念的提出者）**——乐观的实验派

Karpathy 在 X 上分享了他的实验：用 vibe coding 一晚上做出了一个完整的小游戏，代码他几乎没看过，但游戏就是能跑。他的原话是：**"我只是看到东西、说出东西、运行东西、复制粘贴东西，然后它大部分都能工作。"** 他的结论是，AI 让"表达想法"的成本骤降，创意的瓶颈不再是"会不会写代码"，而是"有没有想法"[1]。

值得注意的是，Karpathy 本人后来也对这个词的"语义漂移"有所警惕——他最初谈的是适合"随手扔掉的周末项目"的玩法，但这个词被越来越多的人用来描述任何形式的 AI 辅助编程，这并不是他的本意。

**Peter Steinberger（PSPDFKit 创始人，OpenClaw 作者）**——资深开发者的切身体验

Steinberger 是 iOS 社区的知名开发者，也是 OpenClaw 的作者。他对 vibe coding 的态度颇为复杂。

他在博客 *Just One More Prompt*（2025 年 8 月）中，把自己称为"Claudoholic"，坦言 AI 编程的即时满足感会产生一种类似成瘾的吸引力，容易陷入"虚假的生产力幻觉"[9]。他更在公开场合反对把 vibe coding 当作一个贬义词，认为它只是一种被误解的技能——就像吉他，需要练习、直觉和技术理解才能弹好，随便拨几下弦出来的只是噪音。

他的工作流同样很有参考价值：他现在会直接发布未完全阅读的 AI 生成代码，但这是建立在他多年工程管理经验带来的"直觉判断力"的基础上的——这套直觉让他知道什么时候可以信任 AI，什么时候需要自己介入。

**Simon Willison（Datasette 作者，知名开源开发者）**——概念的捍卫者

Willison 在他的博客 simonwillison.net 上多次为 vibe coding 的"原始定义"发声。他认为这个词被滥用了：真正的 vibe coding 是一种**刻意忘掉代码存在**的开发方式，有其独特价值；而把"使用 AI 工具辅助专业开发"也叫做 vibe coding，是对这个概念的稀释[10]。

他后来提出了一个新词——**"vibe engineering"**（后来更倾向于用"agentic engineering"）——来描述那种用多个 AI Agent 构建和维护生产级软件的复杂工作。在他看来，这才是真正费脑、费劲、要求极高工程素养的事情，远不是"随便振动一下"就能完成的[10]。

**Boris Cherny（Claude Code 产品负责人，Anthropic）**——来自工具制造者的视角

Cherny 在多次采访中透露，他自 2025 年 11 月起就再没有手写过代码，完全依靠 Claude Code，每天能推出 10 到 30 个 PR[11]。他的观点是"写代码这件事，对大多数场景来说基本上已经被'解决'了"，下一个真正的挑战在于**想法、优先级判断和发现用户的潜在需求**。

他也提到，他自己的配置"出乎意料地朴素"——一个 CLAUDE.md 文件、让 AI 像初级工程师一样被对待、允许它从错误中学习而不是每次都帮它修正。这和我在考核中的配置思路高度吻合。


---

**参考来源：**

[1] Andrej Karpathy 关于 vibe coding 的原始推文与讨论 (https://x.com/karpathy)

[2] Wikipedia - Vibe Coding (https://en.wikipedia.org/wiki/Vibe_coding)

[3] Replit AI Agent 官方文档 (https://replit.com)

[4] vitara.ai - AI Web App Builder Comparison 2026 (https://vitara.ai)

[5] nxcode.io - Cursor vs Windsurf vs Trae Comparison 2026 (https://nxcode.io)

[6] Claude Code 官方文档 (https://docs.anthropic.com/en/docs/claude-code/overview)

[7] tanium.com - What is Vibe Coding and What Does It Mean for Security (https://www.tanium.com/blog/what-is-vibe-coding/)

[8] redhat.com - What is Vibe Coding? (https://www.redhat.com/en/topics/ai/what-is-vibe-coding)

[9] steipete.me - Just One More Prompt (https://steipete.me)

[10] simonwillison.net - Vibe Coding is Not the Same as AI-Assisted Development (https://simonwillison.net)

[11] lennysnewsletter.com - Boris Cherny on the Future of Software Engineering (https://www.lennysnewsletter.com)
