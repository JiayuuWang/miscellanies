# Is It Possible That Future Software Is Just Pure Text?

*Cover image source: CLI-Anything*

A project called **CLI-Anything** has been making waves in both developer circles and the research community recently. It comes from Professor Chao Huang's group at the Hong Kong University of Science and Technology (HKUDS), and has been accumulating attention on GitHub rapidly — at the time of writing, it already has **29k** stars.

[![CLI-Anything Github Repository](/images/cli-anything-repo.png)](https://github.com/HKUDS/CLI-Anything)
*CLI-Anything
Image source: [CLI-Anything Github Repository](https://github.com/HKUDS/CLI-Anything)*

When you open the CLI-Anything repository (the core code lives at https://github.com/HKUDS/CLI-Anything/tree/main/cli-anything-plugin), you'll notice something unusual: **there's almost no code in this project — it's mostly `.md` files**, plain-text Markdown documents. These documents describe in natural language the SOPs for "CLI-ifying" a target application, as well as how to use various CLI tools and workflows. Your local coding agent (like Claude Code) then "reads and executes" them. In other words, the coding agent becomes the software's "runtime" and "driver."

That observation led me to a question: **Is it possible that future software is just a bunch of pure text?**

## What Does CLI-Anything Actually Do?

Let me briefly describe the project itself.

Traditional CLI tools — `ffmpeg`, `git`, `rsync` — each have their own parameter styles, their own documentation, and steep learning curves. Users typically spend a lot of time memorizing commands, reading man pages, or repeatedly Googling.

CLI-Anything takes a different approach. Instead of providing a new CLI tool, it provides a set of **natural-language "usage guides"**, which your local coding agent reads and executes. You simply tell the agent what you want to do, and it consults the `.md` files to automatically invoke the right CLI commands, compose the right parameters, and handle the output.

This is a forward-thinking and genuinely successful open-source project. But I won't spend too much time on the project itself here — I'm more interested in the broader pattern of software that CLI-Anything represents.

## A New Software Paradigm?

The software paradigm we're used to looks like this:

> **Humans write code → compiled to binary → machine executes**

[![Compile Process](/images/compile.png)](https://www.researchgate.net/figure/Java-source-code-is-first-compiled-to-bytecode-and-subsequently-interpreted-or-executed_fig1_318376879)
*Compile Process
Image source: [https://www.researchgate.net/](https://www.researchgate.net/figure/Java-source-code-is-first-compiled-to-bytecode-and-subsequently-interpreted-or-executed_fig1_318376879)*

What CLI-Anything represents is a different possibility:

> **Humans write natural language → coding agent understands and executes**

On the surface, the difference is just "a different middle layer." But the implications run much deeper.

In the traditional paradigm, the "content" of software is machine code or bytecode. It's designed for machines — humans find it hard or impossible to read. Software protection relies on making the underlying intent even harder for humans to recover.

In the new paradigm, the "content" of software is natural language. It's fundamentally written for humans, and can also be executed by an agent. This means: **for the first time, software can be simultaneously readable by both humans and machines.**

## How Far Could This Go?

Imagine a more extreme scenario.

You visit a software store and download a "word processor." After installation, your disk contains a few `.md` files (or perhaps the text is encrypted and unreadable to humans), describing in natural language what this software can do and how it works. Your local coding agent reads these files and acts as a "driver," generating and executing the appropriate operations in real time based on your natural-language instructions.

**No binary files, no executables — just text and an agent.**

This sounds absurd at first glance, but it actually touches on a fundamental question: **What is software, really?**

Software isn't the binary itself — binary is just one form of "translation." The core of software is **intent**: a set of logic describing what to do and how to do it. Binary translates that logic into a form machines can read; natural language expresses that logic in a form humans can read. If an agent is powerful enough to "understand" natural language and "execute" it, then the translation step into binary becomes unnecessary.

## Real Obstacles Worth Taking Seriously

There are, of course, many technical and non-technical problems that need honest treatment — we can't just talk about the vision.

**Reliability.** Agents don't understand natural language with 100% precision. The same text, interpreted by different agents or in different contexts, can yield different results. This is fundamentally unlike the determinism of binary execution. For domains that require precise control — financial transactions, surgical robotics — this level of uncertainty is currently unacceptable.

**Performance.** Every "run" requires the agent to understand the text and generate an execution plan, which is far slower than executing a binary directly. This is acceptable in many contexts, but not all.

**Security and intellectual property.** If software is just text, copying and distributing it becomes trivially easy. Today's IP protection logic is built on the premise that binaries make it difficult to reverse-engineer the original intent. Pure-text software would undermine that entirely. Encrypting the text is one approach (as in the "install encrypted text" scenario above), but that introduces new problems around key management.

**Standardization.** Today's CLI-Anything depends on a specific agent: Claude Code. Different agents may interpret the same text differently. If the "text as software" path is ever to be walked seriously, it will require some form of standardization around agent capabilities — or a mechanism that ensures consistent interpretation across different agents.

## But the Direction Is Real

Despite these obstacles, I believe the direction CLI-Anything points to is genuine, and it's already happening.

It's not the first project to do this. Similar projects and practices are multiplying, each validating the direction in its own way.

**Gstack**, an open-source framework released by Y Combinator CEO Garry Tan, gained rapid traction on GitHub[4]. Its core is likewise a set of Markdown files, each defining a "role skill" — CEO, Engineering Lead, QA Lead, Release Engineer — with corresponding responsibilities and behavioral guidelines, all written in natural language. When you trigger a slash command in Claude Code (like `/plan-ceo-review`, `/qa`, or `/ship`), the agent reads the corresponding Markdown file, "plays" that role, and carries out the work for that phase of the development lifecycle. The entire framework has almost no executable code, yet it can turn a local coding agent into a virtual development team.

[![gstack](/images/gstack.png)](https://x.com/garrytan/status/2038391669679362079)
*Image source: [https://x.com/garrytan/status/2038391669679362079](https://x.com/garrytan/status/2038391669679362079)*

**CLAUDE.md and PROJECT.md** are themselves expressions of this paradigm. You see these files in more and more GitHub repositories — they describe in natural language "what this project is, what tech stack it uses, what conventions to follow during development," and the coding agent reads and internalizes them at startup as the foundation for everything that follows. Anthropic's official support and promotion of CLAUDE.md is, in some sense, already incorporating "text as software configuration" into formal norms[2].

**CLI-Anything's own SKILL.md mechanism** is also worth noting. It introduces a SKILL.md file format that packages each CLI tool into an agent-discoverable, agent-installable "skill bundle" — agents can find and install new tools autonomously, without human intervention. This isn't just "text describing functionality" anymore; it's an ecosystem of tools that agents can extend on their own[5].

This bears a resemblance to the "declarative programming" philosophy of earlier decades — you describe *what* you want, not *how* to do it, and let the underlying system decide the execution details. The difference is that the "underlying system" is now a coding agent, and the "declaration language" is now natural language.

And as agent capabilities keep growing, this path will go deeper. CLI-Anything today is just "a natural-language guide for CLI tools." But the boundary won't stay there.

## What I'm Really Saying

I'm not predicting that binary code will disappear. The traditional software paradigm has its strengths and irreplaceable qualities, and for the foreseeable future both paradigms will coexist.

What I am saying is: **the definition of software is getting broader than it used to be.**

Once, "software" had to be executable machine code. Then interpreted languages made "software" into human-readable scripts. Now, agents make "software" out of natural language text. Each shift has lowered the barrier to expressing intent, and let more people participate in the act of creating software.

In the future, when you run an installer, what it may install is a bundle of structured text and a coding agent driver. The natural-language description becomes the software's moat.

[![How to make an installer to your program](/images/installer.jpg)](https://www.youtube.com/watch?v=CGqba0tb2NQ)
*Image source: [How to make an installer to your program](https://github.com/HKUDS/CLI-Anything)*

CLI-Anything is just a small sample, but it gave me a genuine sense that **agent-as-runtime "pure text software" isn't just a thought experiment — in some contexts, it's already working.**

Where it goes from here is well worth watching.

---

**References:**

[1] HKUDS/CLI-Anything GitHub Repository (https://github.com/HKUDS/CLI-Anything)

[2] Anthropic Claude Code Docs: CLAUDE.md and memory (https://docs.anthropic.com/en/docs/claude-code/memory)

[3] Declarative programming - Wikipedia (https://en.wikipedia.org/wiki/Declarative_programming)

[4] Gstack GitHub Repository (Garry Tan, Y Combinator CEO) (https://github.com/garrytan/gstack)

[5] CLI-Anything Docs: SKILL.md and the CLI-Hub ecosystem (https://github.com/HKUDS/CLI-Anything)
