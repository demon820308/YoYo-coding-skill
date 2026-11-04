# YoYo-coding-skill 使用说明

> 给**使用者（人）**看的说明书：这个 Skill 怎么启用、在什么时候起作用、派活时怎么开口。
> 给 Agent 看的规则本体在 `SKILL.md`，两者不要混用——不要把本文件当规则喂给 Agent 代替 `SKILL.md`。

## 一句话定位

它不是“开工前读一遍就放下”的说明书，而是一套**从立项跟到交付验收**的治理流程。只在项目开始时读、交付时不回头对门禁，等于只用了一半。

## 两种启用方式

### 方式 A：装进 Agent 的 Skill 目录（长期用）

把整个 `YoYo-coding-skill` 文件夹放入所用 Agent 平台的 Skill 目录并启用（各平台目录不同，以平台文档为准）。之后：

- 任务与 `SKILL.md` 头部 description 匹配时，Agent 应自行加载；
- 也可以点名触发：“按 YoYo-coding-skill 做这个任务。”
- 装好后不需要每次把文件再发给 Agent。

### 方式 B：不安装，手动交付（临时用 / 派给外部执行方）

把本文件夹（或 zip 解开后的文件夹）连同任务一起交给 Agent，并明确要求它先读 `SKILL.md`。适用于：给 Gemini、Codex 等执行方派一次性整改活、或在未安装本 Skill 的环境里临时使用。

> 注意：未安装时 Agent 不会自动想起它，每个新会话、新执行方都要重新交付一次。

## 四个使用时机

| 时机 | Agent 读什么 | 产出什么 | 你要做什么 |
|---|---|---|---|
| 1. 项目开始 / 接管 | `SKILL.md` 本体 + 对应模式的一个 workflow | 项目定级（P）、任务风险评级（R）、`PROJECT_PROFILE.yaml`、`PROJECT_RULES.md`、`AGENT_RULES.md`；接管时另出评估报告 | 确认定级与项目规则是否符合实际 |
| 2. 每个中型以上任务开工前 | `templates/TASK.md` + 相关 workflow | 工作单（目标、范围、范围外、验收条件、验证计划、回滚） | 中高风险任务先看计划再放行 |
| 3. 执行过程中 | 五条铁律（`SKILL.md` §2.1）+ 当前 workflow；具体技术标准按 §3.1 优先级查 `references/` 原文 | 受控的小步变更 | 只处理被点名的决策（架构变更、范围扩大、风险接受） |
| 4. 交付验收前 | `core/quality-gates.md` + 对应 checklist | 交付报告：完成项按 E0–E5 标证据等级、铁律门禁逐条核对结果、未验证项与回滚方法 | 按报告验收，不采信口头“已完成” |

关键纪律：**references 四份原文（约 2,000 行）永远按需查，不全量读**。全塞进上下文既费 token，又稀释注意力，与本 Skill 的设计相反。

## 按任务查表（该走哪个 workflow）

| 你要做的事 | 模式 | Workflow 文件 | 常用清单/模板 |
|---|---|---|---|
| 从零做一个新项目 | NEW_PROJECT | `workflows/new-project.md` | `checklists/initialization.md` |
| 接手一个已有仓库，先摸清 | PROJECT_TAKEOVER | `workflows/project-takeover.md` | `assessment/` 五份、`templates/PROJECT_ASSESSMENT.md` |
| 给现有系统加功能 / 改行为 | SECONDARY_DEVELOPMENT | `workflows/secondary-development.md` | `checklists/development.md`、`templates/TASK.md` |
| 不改行为，只改善结构 | REFACTORING | `workflows/refactoring.md` | `checklists/refactoring.md` |
| 修 Bug / 故障 / 常规升级 | MAINTENANCE | `workflows/maintenance.md` | `checklists/development.md` |
| 换框架 / 数据库 / 平台 / 运行时 | MIGRATION | `workflows/migration.md` | `checklists/release.md` |

## 派活句式（可直接复制）

- **新项目**：“用 YoYo-coding-skill 初始化这个项目：先定级、定项目规则，只搭最小可运行基线，不堆功能。”
- **接管**：“按 YoYo-coding-skill 的接管流程评估这个仓库：只读检查，不改业务代码，交付评估报告和基线验证结果。”
- **二开**：“按 YoYo-coding-skill 做这张工作单（附工作单）；先给影响分析和计划，我确认后再动手。”
- **重构**：“按 YoYo-coding-skill 的重构流程拆分这个模块：先钉特征测试再动结构，拆分提交里测试零修改，外部行为不变。”
- **修 Bug**：“按 YoYo-coding-skill 的维护流程修这个 Bug：先复现、定位根因，不许症状式补丁，交付时附回归证据。”
- **迁移**：“按 YoYo-coding-skill 的迁移流程制定分阶段计划：含备份、校验、切换与回滚条件；计划经我批准前不执行任何生产操作。”
- **验收（对执行方的交付）**：“按 YoYo-coding-skill 的质量门禁验收这批交付：铁律五条逐条核对、结论标证据等级、无证据的项一律记为未验证。”

## 项目级沉淀：规矩只定一次

时机 1 产出的 `PROJECT_PROFILE.yaml`、`PROJECT_RULES.md`、`AGENT_RULES.md` 应放进项目仓库根目录长期保存。之后同一项目的后续任务，Agent 先读这三份项目文件，再按需查 Skill——不需要每次重读 Skill 全文，更不需要重读 references。项目事实变了，就更新这三份文件，不要另起一份并行文档。

**AGENT_RULES.md 和 AGENTS.md 是什么关系？** `AGENT_RULES.md` 是 Skill 定的事实源名字，但不少平台只自动读自己的文件名（Codex 读 `AGENTS.md`、Claude Code 读 `CLAUDE.md`），不认它。所以初始化时会按 `SKILL.md` §9.1 做桥接：平台文件里只放一行指针（指向 AGENT_RULES.md）＋五条铁律的摘要，**不复制全文**——全文永远只有一份，改规矩只改事实源。只有一个例外：如果这个项目永远只用一个平台，可以直接把规则写进那个平台文件当本体，就不再另建 AGENT_RULES.md。验收时打开平台实际会读的那个文件，确认指针和铁律摘要在，就说明桥接上了。

## 常见误用

- **把包里全部文件一次性全贴给 Agent**：错误。正确入口永远只有 `SKILL.md`，其余按它指引按需加载。
- **只在开工时用**：错误。开工定规则、交付对门禁，缺一头都不完整。
- **P 分级和 R 分级混着说**：P0–P4 是项目级长期定级，只在立项/接管定一次；R0–R3 是任务级风险，每个任务单独评。报告里必须注明是哪一套。
- **把 Markdown 规则当强制力**：本 Skill 是流程约束，不是权限沙箱。真正拦得住人的，是平台权限、Git、CI 和你的确认环节；规则的作用是让 Agent 知道该在何处停下来问你。
- **小任务也走全套**：不需要。R0/R1 轻流程即可——本 Skill 的比例原则管流程重量；但五条铁律不因任务小而豁免，它们管的是正确性，不是流程。
- **项目已有的规矩和 Skill 冲突时各执一词**：项目具体事实（技术栈、命令、契约）以项目仓库里的 `PROJECT_RULES.md` 为准；正确性底线（五条铁律）以 Skill 为准；其余冲突由 Agent 点名交你裁定，不许静默选边。

## 常见问题

**项目做到一半才想起来用，来得及吗？** 来得及。先按“接管”模式补一轮只读评估和基线，把项目三件套文件补齐，之后的任务再按正常流程走。不要为了补流程去改已有代码。

**给执行方派活，要把整个 Skill 都发吗？** 发整个文件夹最稳妥，但要在指令里写明“先读 SKILL.md，其余按需”。只发 `SKILL.md` 一个文件也能跑主流程，但查不到 references 原文和模板，交付质量会打折。

**怎么知道 Agent 真的照做了？** 看交付报告三样东西：实际执行的命令与结果、铁律门禁的逐条核对、每条结论的证据等级。三样缺任何一样，都按“未验证”处理。
