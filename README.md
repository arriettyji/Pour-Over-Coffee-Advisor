# Pour-over Coffee Advisor

[中文](#中文) | [English](#english)

## 中文

Pour-over Coffee Advisor 是一个面向 AI Agent 的通用手冲与过滤咖啡分析 Skill。它可以为具体咖啡设计完整起始方案，根据冲煮过程和感官结果诊断问题，在器材或条件变化后迁移配方，并比较不同冲煮路线。建议会结合当前咖啡、烘焙与样品状态、滤杯—滤纸系统、磨豆机、用水、粉量、冲煮过程、感官反馈和用户本次目标形成。

它不是固定配方合集，也不把某位实践者的方法当成唯一答案。项目使用固定理论知识、实践案例、运行时对象研究和结构化分析推理，为每个案例独立构造能够直接执行、说明依据并接受下一杯验证的建议。

> 本项目仍在持续测试和更新。不同模型、搜索能力、上下文长度及工具权限会影响对象研究、推理完整度和最终输出。

### 能做什么

| 任务 | Skill 的工作 |
|---|---|
| 第一次冲煮 | 研究当前咖啡和冲煮系统，设计粉量、比例、研磨、水温、注水、流量、水位、扰动与结束条件共同组成的完整起始方案 |
| 已有结果诊断 | 分析参数、过程、流动和感官模式，比较主要机制与替代解释，并生成完整下一轮方案 |
| 器材与条件迁移 | 在滤杯、滤纸、磨豆机、刀盘、水、粉量或其他条件变化后重新选择系统并重构配方 |
| 配方分析 | 解释已有配方的结构、适用条件、协同关系、潜在限制与调整空间 |
| 方案比较 | 在当前咖啡、器材与目标下比较不同滤杯—滤纸系统、配方架构或杯型方向 |
| 连续迭代 | 将下一杯同时作为改善方案与验证判断的实验，并根据新结果更新后续路线 |

Skill 可以从自然语言、咖啡包装照片、产品名称、烘焙日期、器材信息、现有配方、冲煮过程、TDS/EY 和感官反馈中提取信息。当现有信息足以建立合理方案时，它会直接完成分析；只有某个缺口足以改变整体路线时，才集中提出高价值问题。

### 一次完整回答通常包含什么

完整方案不会只给出若干孤立数值，而会根据案例复杂度组织以下内容：

1. **当前对象研究与分析**：确认咖啡、烘焙商、生豆背景、产季、样品状态、器材与用水，并说明资料缺口和可迁移经验。
2. **技术判断与路线选择**：区分饮用浓度、平均萃取、均匀性、粉床流动、热状态、感官结构和个人目标，再决定精修、重构、换系统或并行探索。
3. **完整执行方案**：使用方案摘要表和注水时间轴表列出粉量、水量、比例、研磨、水温、滤杯、精确滤纸、每段注水、流量、水位、动作、预计总时和结束条件。
4. **参数协同与证据**：解释粉量、器材、滤纸、研磨、热、注水和时间如何相互作用，并区分稳定知识、实践观察、对象事实与当前推断。
5. **观察重点与后续判断**：说明下一杯最值得记录的流动和感官信息，以及不同结果将怎样更新当前解释。

简单案例可以紧凑，复杂诊断可以充分展开。输出结构约束需要覆盖的决定，而不是要求每次回答使用完全相同的目录或长度。

### 为什么器材、粉量和时间需要共同分析

项目把滤杯、滤纸、粉量、研磨、注水与水位视为一个完整冲煮系统。滤杯身份、滤纸形状与尺寸、实际成形方式、纸张产品线和有效粉床几何分别确认；资料更丰富或品牌更知名的器材不会因此自动获得更高适配度。

粉量会影响有效床深、粉床阻力、热容量、总水量、液柱、注水动作的相对强度和操作误差，因此必须传播到滤杯选择、研磨、润湿、注水、水位、热管理、预计总时和结束条件。用户指定粉量时，Skill 会把它作为确定输入传播到整个方案，而不是只在表格中更换粉量数字。

预计总时是条件化预测，不是由一个通用公式或固定器材时间表产生。方案需要逐段考虑注水期间同步排液、段末水位、段间排液和下一段起始状态，并将精确滤纸、滤杯出口、粉量/床深、研磨/细粉、液柱、温度、排气和扰动共同纳入判断。时间窗口同时配合可观察的结束条件使用。

### 工作方式

项目采用三个核心层与两个辅助层：

| 层 | 主要作用 | 位置 |
|---|---|---|
| 固定理论知识 | 提供生产与生豆、烘焙、冲煮和感官的稳定机制、方法与证据边界 | `references/theory/` |
| 运行时对象研究 | 针对当前咖啡、烘焙商、生产背景、产季、器材、滤纸和水确认身份与最新信息 | `references/runtime-research/` |
| 结构化分析推理 | 将输入、研究、理论、实践资料和感官结果组织成诊断、路线与完整方案 | `references/reasoning/` |
| 实践观点与案例 | 保存现实方法、长期观察、比赛方案、器材经验、争议与可检验假设 | `references/practice/` |
| 私人上下文规范 | 管理无档案、会话级资料和持久私人档案的边界与优先级 | `references/personal-profile.md` |

对象研究在完整配方回答中始终作为独立部分出现。当前产品页面即使资料完整，也不会替代对烘焙商、生豆生产背景、产区与产季、可迁移经验和器材系统的并列研究。

### 证据如何使用

关键决定使用以下证据类型：

| 类型 | 含义 |
|---|---|
| 稳定知识 | 同行评议研究、学术或技术专著、标准、研究报告及方法充分资料 |
| 实践观察 | 实践者直接报告的操作、过程或感官结果 |
| 实践解释 | 实践者对观察提出的机制解释 |
| 对象事实 | 当前咖啡、生产、烘焙、样品、器材、水和用户提供状态的可核实信息 |
| 当前推断 | Agent 综合全部资料后针对当前案例形成、仍可由下一杯检验的判断 |

特定咖啡、器材或比赛方案不会自动升级为普遍规律。跨对象经验需要说明共享条件、关键差异、能够支持的窄结论和迁移等级；同一杯冲煮记录只能直接证明该次完整配置及其结果，不能单独证明某个参数的独立作用。

### 固定资料覆盖

当前固定知识库采用“底层逐项研究记录 + 跨来源决策卡”的两层结构：

- 7 部研究型或技术型必读资料形成 203 条逐项研究记录；
- 24 项主动补充的同行评议研究、标准或方法充分资料形成 86 条研究记录；
- 稳定理论底层现有 289 条研究记录，并综合为 49 张跨来源决策卡；
- 2 部偏通识或实践的必读资料另形成 42 条来源研究记录；
- 实践层包含 268 篇文章或视频的独立研究记录、51 个比赛方案的完整案例与逐案迁移分析，以及 26 张跨文章或案例的主题综合卡。

这些数字表示已经整理的研究记录和运行时检索入口，不代表某个主题只有相应数量的结论。完整覆盖、资料性质、主要证据缺口和第一版能力边界见 [`references/research-status.md`](references/research-status.md)。公开包只包含结构化研究成果、短篇综合与来源定位，不包含建设阶段使用的原始电子书、论文附件或用户私人资料。

### 私人档案与会话上下文

Skill 在没有个人档案时也可以直接运行。用户可以只提供当前咖啡和本次条件，Agent 会在资料足以形成方案时完成分析。

在同一对话中，Skill 可以继续使用已经确认的器材、耗材、默认操作和偏好，同时为不同咖啡、不同冲煮尝试和单次追问保持独立作用域。上一支咖啡的器材选择、剩余量、配方要求或单次结果不会自动成为所有咖啡的全局限制。

需要跨对话持续使用时，用户可以另行维护唯一的 `private-coffee-profile.md`。私人档案可以保存器材规范身份、滤纸接口、用水、稳定默认值和明确偏好，但不会包含在本公共项目中。当前请求和当前会话中最新确认的信息始终优先于私人档案。

### 获取与安装

项目主页为 [github.com/arriettyji/Pour-Over-Coffee-Advisor](https://github.com/arriettyji/Pour-Over-Coffee-Advisor)。可以在 GitHub 的 **Code** 菜单中选择 **Download ZIP**，也可以使用 Git 克隆完整仓库：

```bash
git clone https://github.com/arriettyji/Pour-Over-Coffee-Advisor.git
```

解压或克隆后，按照所使用 AI Agent 的 Skill 安装方式导入包含 `SKILL.md` 的整个项目目录。请保留 `references/`、`agents/`、`assets/` 和 `evals/` 的相对目录结构；单独复制 `SKILL.md` 会失去固定知识、实践资料和运行时工作流。

### 开始使用

第一次冲煮可以这样开始：

```text
使用 @pour-over-coffee-advisor 为这支咖啡设计第一次冲煮方案。

咖啡：产品名称、烘焙商、产地/生产者、品种、处理法、烘焙日期与包装描述
器材：可用滤杯和滤纸、磨豆机/刀盘、水壶与其他工具
用水：现成水或配水信息
粉量：如果已经确定，请直接说明
目标：希望获得的杯型，或暂时没有明确偏好
```

已有冲煮结果可以这样开始：

```text
使用 @pour-over-coffee-advisor 分析这支咖啡的冲煮记录，并设计下一杯。

咖啡与样品状态：……
本次或历次配方：……
冲煮过程与总时间：……
从热到冷的感官表现：……
下一杯已经确定的条件：……
当前目标：……
```

包装照片、产品链接、结构化记录和自然语言描述都可以作为输入。若用户只想询问某个参数的依据、来源或表达方式，可以直接追问，不需要重新粘贴全部信息。

### 适用边界

本项目不依赖预先训练的咖啡统计预测模型，也不会仅凭包装标签精确预测杯中风味。没有足够数据时，研磨刻度、预计总时、养豆状态和感官机制都应以条件化范围、证据强度和可观察验证方式表达。

不同 AI Agent 的联网搜索、图片读取、文件访问、上下文管理与推理能力存在差异，同一个 Skill 在不同模型中的执行完整度也可能不同。Skill 提供的是研究与分析工作流、固定资料和决策约束，具体建议仍需要用户根据实际冲煮过程和杯中结果判断。

### 参与改进与使用反馈

具体、能够复现的使用反馈会对后续改进非常有帮助。如果回答出现事实错误、分析依据不足、器材身份或滤纸适配错误、配方协同问题、预计总时明显偏离、上下文污染、来源错误或操作不便，欢迎通过仓库的 [Issue 表单](https://github.com/arriettyji/Pour-Over-Coffee-Advisor/issues/new/choose) 提交一个聚焦的问题报告。

反馈时请尽量提供所用模型与环境、任务类型、必要输入、实际表现、预期表现，以及最终回答是否可用。提交前请移除无需公开的私人档案、购买记录、完整冲煮数据库和其他个人信息。如果希望贡献资料、评测案例、文档修订或行为改进，请先阅读 [`CONTRIBUTING.md`](CONTRIBUTING.md)，并建立 Issue 说明范围和依据。

### 项目文档

- [`SKILL.md`](SKILL.md)：Agent 的运行入口与权威执行规则；
- [`CONTRIBUTING.md`](CONTRIBUTING.md)：反馈方式、Pull Request 流程与贡献授权；
- [`LICENSE`](LICENSE)：CC BY-NC-ND 4.0 完整法律文本；
- [`docs/agent-guide.md`](docs/agent-guide.md)：项目结构、运行顺序和维护者导览；
- [`references/research-status.md`](references/research-status.md)：研究覆盖、证据缺口与合理能力范围；
- [`references/evidence-policy.md`](references/evidence-policy.md)：证据分类、来源评价和迁移原则；
- [`evals/README.md`](evals/README.md)：评测方法、案例与评分入口。

### 关于这个 Skill

Pour-over Coffee Advisor 由 Arrietty Ji 设计、整理并持续维护，目前仍在根据实际使用情况不断测试和更新。

非常欢迎实际使用后的具体反馈。表现良好的案例、判断不准的结果、操作不便之处和值得增加的新功能，都可能帮助后续版本继续完善。提交的使用体验和改进建议可能被用于未来更新。

希望这个 Skill 能陪你更好地理解咖啡、器材与每一次冲煮，也希望你在使用过程中获得新的发现和好喝的咖啡。使用愉快！

本项目采用 [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International](LICENSE) 许可。欢迎分享[原始仓库链接](https://github.com/arriettyji/Pour-Over-Coffee-Advisor)，以便其他使用者获得作者维护的最新完整版本。

© 2026 Arrietty Ji

---

## English

Pour-over Coffee Advisor is a general-purpose Skill for AI agents working with pour-over and filter coffee. It can design a complete starting recipe for a specific coffee, diagnose brewing processes and sensory results, migrate recipes when equipment or conditions change, and compare alternative brewing routes. Recommendations are built around the coffee, roast and sample condition, brewer–filter system, grinder, water, dose, brewing process, sensory feedback, and the user's current goal.

This is not a collection of fixed recipes, nor does it treat any practitioner's method as the single correct answer. The project combines a fixed theory base, practice cases, runtime object research, and structured analysis to construct an executable recommendation for each case, explain the basis for major decisions, and let the next brew test the current reasoning.

> This project is still being tested and updated. Differences in model capability, web access, context length, and available tools can affect the completeness of research, reasoning, and output.

### What it can do

| Task | What the Skill does |
|---|---|
| First brew | Researches the coffee and brewing system, then designs a complete starting recipe across dose, ratio, grind, temperature, pours, flow, water level, agitation, and end condition |
| Brew diagnosis | Analyzes parameters, process, flow, and sensory patterns; compares the leading mechanism with alternatives; and produces a complete next-brew plan |
| Equipment or condition migration | Re-selects the system and rebuilds the recipe when the brewer, filter, grinder, burrs, water, dose, or other conditions change |
| Recipe analysis | Explains the structure, operating assumptions, parameter interactions, limitations, and adjustment space of an existing recipe |
| Method comparison | Compares brewer–filter systems, recipe structures, or cup-style directions under the current coffee, equipment, and goal |
| Iterative brewing | Uses the next cup both to improve the result and to test the current diagnosis, then updates the following route from new evidence |

The Skill can extract information from natural language, package photos, product names, roast dates, equipment details, existing recipes, brew-process descriptions, TDS/EY, and sensory feedback. When the available information supports a reasonable plan, it proceeds directly; it asks a focused question only when a missing fact could materially change the route.

### What a complete answer usually contains

A complete recommendation covers the following decisions, with the organization adapted to case complexity:

1. **Current-object research and analysis** confirms the coffee, roaster, green-coffee background, crop context, sample condition, equipment, and water, while identifying evidence gaps and transferable experience.
2. **Technical diagnosis and route selection** separates beverage strength, average extraction, local uniformity, bed flow, thermal state, sensory structure, and the user's current goal before choosing refinement, reconstruction, a new system, or parallel exploration.
3. **Complete executable recipe** uses a recipe summary table and pour timeline to specify dose, water, ratio, grind, temperature, brewer, exact filter, every pour, flow rate, water level, actions, expected total time, and end condition.
4. **Parameter interaction and evidence** explains how dose, equipment, paper, grind, heat, pouring, and time work together, while distinguishing established knowledge, practice observations, object facts, and current inference.
5. **Observation and follow-up logic** identifies the most informative flow and sensory observations and explains how different outcomes would update the current interpretation.

Simple cases may stay compact, while complex diagnoses may expand. The output contract defines the decisions that must be covered rather than forcing every answer into the same headings or length.

### Why equipment, dose, and time are solved together

The project treats brewer, filter, dose, grind, pouring, and water level as one brewing system. Brewer identity, filter shape and size, forming method, exact paper product, and effective bed geometry are resolved separately. Better-known equipment or equipment with more published material does not receive a higher fit score merely because it is easier to research.

Dose changes effective bed depth, bed resistance, thermal mass, total water, liquid head, the relative strength of pouring actions, and sensitivity to operational error. Its effects therefore propagate into brewer choice, grind, wetting, pours, water level, thermal management, expected total time, and end condition. When the user specifies a dose, the Skill treats it as a fixed input and rebuilds the system around it rather than changing only one row in a table.

Expected total time is a conditional prediction rather than the output of a universal formula or fixed brewer timetable. Each stage considers drainage occurring during the pour, end-of-stage water level, interstage drainage, and the next stage's starting state. Exact paper, brewer outlet, dose and bed depth, grind and fines, liquid head, temperature, degassing, and agitation all participate in the estimate. The time window is always paired with an observable end condition.

### How it works

The project uses three core layers and two supporting layers:

| Layer | Main role | Location |
|---|---|---|
| Fixed theory base | Mechanisms, methods, and evidence boundaries across green coffee, roasting, brewing, and sensory science | `references/theory/` |
| Runtime object research | Identity and current information for the coffee, roaster, production background, crop, equipment, paper, and water | `references/runtime-research/` |
| Structured analysis | Organizes inputs, research, theory, practice sources, and sensory results into a diagnosis, route, and complete recipe | `references/reasoning/` |
| Practice viewpoints and cases | Real methods, long-term observations, competition recipes, equipment experience, disagreements, and testable hypotheses | `references/practice/` |
| Personal-context specification | Boundaries and precedence for no-profile, session-level, and persistent-profile operation | `references/personal-profile.md` |

Current-object research remains a standalone part of every complete recipe answer. Even a detailed product page does not replace parallel research into the roaster, production background, region and crop, transferable experience, and brewing equipment.

### How evidence is used

Major decisions distinguish the following evidence types:

| Type | Meaning |
|---|---|
| Established knowledge | Peer-reviewed research, academic or technical books, standards, research reports, and methodologically sufficient sources |
| Practice observation | A practitioner's directly reported process or sensory result |
| Practice explanation | A practitioner's proposed mechanism for an observation |
| Object fact | Verifiable information about the current coffee, production, roast, sample, equipment, water, or user-provided state |
| Current inference | The agent's case-specific interpretation after integrating all available material, still open to testing in the next brew |

A specific coffee, device, or competition recipe does not automatically become a universal rule. Cross-object transfer must state the shared conditions, important differences, narrow supported conclusion, and transfer strength. A single brew record directly supports only the complete configuration and observed result of that brew; it does not isolate the independent effect of one parameter.

### Fixed research coverage

The fixed knowledge base uses two levels: detailed study records and cross-source decision cards.

- 7 required research or technical sources produced 203 detailed study records;
- 24 supplementary peer-reviewed studies, standards, or methodologically sufficient sources produced 86 records;
- the stable-theory layer currently contains 289 study records, synthesized into 49 cross-source decision cards;
- 2 broader reference and practice books produced another 42 source-study records;
- the practice layer contains independent records for 268 articles or videos, 51 complete competition cases with case-by-case transfer analysis, and 26 cross-source practice cards.

These counts describe indexed research records and runtime decision routes, not the total number of conclusions available for a topic. See [`references/research-status.md`](references/research-status.md) for coverage, source types, major gaps, and the reasonable capability boundary of the first release. The public package contains structured research results, concise synthesis, and source locators—not the original ebooks, paper attachments, or any user's private records used during development.

### Personal profiles and conversation context

The Skill works without a personal profile. A user can provide only the current coffee and brewing conditions, and the agent can proceed whenever the available information supports a reasonable plan.

Within one conversation, the Skill can reuse confirmed equipment, consumables, default operations, and preferences while keeping separate scopes for different coffees, brew attempts, and one-off follow-up questions. A brewer choice, remaining dose, recipe constraint, or isolated result from the previous coffee does not automatically become a global rule.

For continuity across conversations, a user may separately maintain a single `private-coffee-profile.md`. It can store canonical equipment identities, filter interfaces, water, stable defaults, and explicit preferences, but it is not included in this public project. The current request and the latest confirmed session information always take precedence over the profile.

### Download and installation

The project is hosted at [github.com/arriettyji/Pour-Over-Coffee-Advisor](https://github.com/arriettyji/Pour-Over-Coffee-Advisor). Use **Code → Download ZIP** on GitHub, or clone the complete repository with Git:

```bash
git clone https://github.com/arriettyji/Pour-Over-Coffee-Advisor.git
```

After extracting or cloning the repository, import the entire directory containing `SKILL.md` according to the Skill installation method supported by your AI agent. Keep the relative structure of `references/`, `agents/`, `assets/`, and `evals/`; copying `SKILL.md` alone removes the fixed knowledge, practice material, and runtime workflow.

### Getting started

For a first brew, start with:

```text
Use @pour-over-coffee-advisor to design a first-brew recipe for this coffee.

Coffee: product, roaster, origin/producer, variety, process, roast date, and package description
Equipment: available brewers and filters, grinder/burrs, kettle, and other tools
Water: bottled water or recipe information
Dose: specify it directly if already fixed
Goal: desired cup style, or no fixed preference yet
```

For an existing brew result, start with:

```text
Use @pour-over-coffee-advisor to analyze this coffee's brew history and design the next cup.

Coffee and sample condition: ...
Current or previous recipes: ...
Brewing process and total time: ...
Sensory result from hot to cool: ...
Conditions already fixed for the next cup: ...
Current goal: ...
```

Package photos, product links, structured logs, and natural-language descriptions can all be used as input. If the user only wants the rationale, source, or expression behind one parameter, they can ask a follow-up without pasting the entire case again.

### Boundaries

This project does not use a pretrained statistical coffee-prediction model and does not infer exact cup flavor from package labels alone. When the evidence is insufficient, grind, expected total time, resting state, and sensory mechanism should be expressed as conditional ranges with evidence strength and observable validation.

AI agents differ in web access, image reading, file access, context management, and reasoning capability. The same Skill may therefore be executed with different levels of completeness across models. The project supplies a research and analysis workflow, fixed references, and decision constraints; users still evaluate each recommendation against the actual brewing process and cup result.

### Contributing and feedback

Concrete, reproducible feedback is especially valuable while the Skill continues to be tested and refined. If a response contains a factual error, weak reasoning, an incorrect brewer or filter identity, poor parameter interaction, a materially inaccurate time estimate, context contamination, source problems, or operational friction, please submit one focused report through the repository's [Issue forms](https://github.com/arriettyji/Pour-Over-Coffee-Advisor/issues/new/choose).

Include the model and environment used, task type, minimum relevant input, what happened, what you expected instead, and whether the final answer was usable. Remove private profiles, purchase records, complete brew databases, and other personal information before posting. To contribute sources, evaluation cases, documentation changes, or behavior improvements, read [`CONTRIBUTING.md`](CONTRIBUTING.md) first and open an Issue explaining the scope and basis.

### Project documentation

- [`SKILL.md`](SKILL.md): the runtime entry point and authoritative execution rules;
- [`CONTRIBUTING.md`](CONTRIBUTING.md): feedback routes, pull request workflow, and contribution permission;
- [`LICENSE`](LICENSE): complete CC BY-NC-ND 4.0 legal text;
- [`docs/agent-guide.md`](docs/agent-guide.md): project structure, runtime sequence, and maintainer orientation;
- [`references/research-status.md`](references/research-status.md): research coverage, evidence gaps, and reasonable capability boundaries;
- [`references/evidence-policy.md`](references/evidence-policy.md): evidence classification, source evaluation, and transfer principles;
- [`evals/README.md`](evals/README.md): evaluation method, cases, and scoring entry point.

### About this Skill

Pour-over Coffee Advisor is designed, curated, and continuously maintained by Arrietty Ji. It remains under active testing and development based on real use.

Specific feedback from actual use is welcome. Strong outcomes, inaccurate judgments, operational difficulties, and worthwhile feature ideas may all help improve future versions. Submitted experiences and suggestions may inform later updates.

May this Skill help you understand coffee, equipment, and each brew more clearly—and help you discover some enjoyable cups along the way.

This project is licensed under the [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License](LICENSE). Please share the [original repository link](https://github.com/arriettyji/Pour-Over-Coffee-Advisor) so that others can obtain the latest complete version maintained by the author.

© 2026 Arrietty Ji
