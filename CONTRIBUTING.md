# Contributing and Feedback / 参与贡献与反馈

[中文](#中文) | [English](#english)

## 中文

感谢你愿意帮助改进 Pour-over Coffee Advisor。实际使用中的正面结果、判断失误、器材身份错误、参数协同问题、来源问题、上下文污染、操作不便，以及值得增加的新功能，都具有参考价值。

### 可以提交什么

- **使用反馈**：记录 Skill 在真实咖啡和冲煮条件下的表现，无论结果好坏。
- **问题报告**：提供能够复现的事实错误、研究缺口、推理问题或不可执行方案。
- **资料与功能建议**：推荐新的研究资料、实践案例、器材研究方向、评测案例或工作流改进。
- **Pull Request**：修正文档、研究记录、评测、运行规则或其他项目文件。

### 提交 Issue

请从 [Issue 表单](https://github.com/arriettyji/Pour-Over-Coffee-Advisor/issues/new/choose) 中选择最接近的类型。为了让问题能够被有效判断，请尽量提供：

1. 使用的模型、平台以及是否具备联网或文件读取能力；
2. 任务类型和足以复现问题的最小输入；
3. 实际输出或行为，以及你认为不准确或不便之处；
4. 预期行为、实际冲煮过程与杯中结果；
5. 如涉及来源，提供原始链接、作者、日期和准确位置。

提交前请移除私人档案、购买记录、完整冲煮数据库、账号信息和其他无需公开的个人内容。咖啡包装、配方和冲煮记录只需保留判断当前问题所必需的部分。

### 提交 Pull Request

1. 先建立一个 Issue，说明拟解决的问题、依据与修改范围；小型拼写或链接修正可以直接提交。
2. 每个 Pull Request 聚焦一个问题，避免同时混入无关重写或大范围格式变化。
3. 修改运行行为时，说明受影响的决策链，并在 `evals/` 中补充或更新能够观察成功与失败的案例。
4. 修改理论或实践资料时，保留来源位置、方法、适用条件、限制和证据性质；不要把实践解释改写成稳定机制。
5. 不要提交原始电子书、付费课程、未经授权的论文附件、大段受版权保护的转载内容或任何用户私人资料。
6. 在说明中列出你完成的检查，以及仍然存在的不确定性或未覆盖范围。

提交并不保证修改会被采用。维护者会根据项目范围、证据质量、可迁移性、运行成本、许可证和现有架构决定是否整合，并可能对文字、结构或实现继续编辑。

### 贡献授权与项目许可证

仓库现有内容采用 [CC BY-NC-ND 4.0](LICENSE)。该许可证允许在署名、非商业且不公开传播改编版本的条件下使用项目内容。

为了允许公开提交 Pull Request，维护者另行授予贡献者一项有限许可：可以仅为向本仓库提出贡献而创建并公开相应修改。此许可不允许在贡献流程之外公开发布修改后的完整项目。

提交 Issue、Pull Request 或其他材料即表示你确认有权提交这些内容，并同意 Arrietty Ji 可以审阅、编辑、改编、整合、复制和发布你的贡献，包括将被接受的部分纳入本项目并按照本项目当前许可证发布。你仍然保留自己原创贡献依法享有的权利。

## English

Thank you for helping improve Pour-over Coffee Advisor. Positive outcomes, inaccurate judgments, equipment-identification errors, weak parameter interaction, source problems, context contamination, operational friction, and useful feature ideas are all valuable forms of feedback.

### What you can contribute

- **Use feedback** describing how the Skill performed under real coffee and brewing conditions, whether the result was strong or weak.
- **Problem reports** with reproducible factual errors, research gaps, reasoning failures, or unusable recipes.
- **Source and feature proposals** covering research material, practice cases, equipment research, evaluation cases, or workflow improvements.
- **Pull requests** that revise documentation, research records, evaluations, runtime rules, or other project files.

### Opening an Issue

Choose the closest form from the [Issue form selector](https://github.com/arriettyji/Pour-Over-Coffee-Advisor/issues/new/choose). To make a report actionable, include where possible:

1. the model and platform used, including whether web or file access was available;
2. the task type and the minimum input required to reproduce the behavior;
3. the actual output or behavior and what appeared inaccurate or inconvenient;
4. the expected behavior, actual brewing process, and cup result;
5. for source-related reports, the original link, author, date, and precise location.

Before submitting, remove private profiles, purchase history, complete brew databases, account information, and other personal material that does not need to be public. Include only the package, recipe, and brew-record details needed to evaluate the report.

### Opening a Pull Request

1. Open an Issue first to explain the problem, evidence, and intended scope. Small spelling or broken-link fixes may be submitted directly.
2. Keep each pull request focused on one problem and avoid unrelated rewrites or large formatting changes.
3. When changing runtime behavior, identify the affected decision chain and add or update an observable success and failure case under `evals/`.
4. When changing theory or practice material, preserve source location, method, conditions, limitations, and evidence type. Do not rewrite a practice explanation as an established mechanism.
5. Do not submit original ebooks, paid-course material, unauthorized paper attachments, substantial copyrighted reproductions, or any user's private records.
6. Describe the checks you completed and any remaining uncertainty or uncovered scope.

Submission does not guarantee acceptance. The maintainer may accept, decline, or further edit a contribution based on project scope, evidence quality, transferability, runtime cost, licensing, and the existing architecture.

### Contribution permission and project license

Existing repository content is licensed under [CC BY-NC-ND 4.0](LICENSE). It may be used with attribution for noncommercial purposes, but adapted versions may not be publicly distributed under that license.

To make public pull requests possible, the maintainer separately grants contributors limited permission to create and publish modifications solely for the purpose of proposing them to this repository. This permission does not authorize public distribution of a modified complete project outside the contribution process.

By submitting an Issue, pull request, or other material, you confirm that you have the right to submit it and agree that Arrietty Ji may review, edit, adapt, integrate, reproduce, and publish your contribution, including incorporating accepted portions into this project and distributing them under the project's current license. You retain any rights you hold in your original contribution.
