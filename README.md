# YoYo｜项目级工程治理 Skill

版本：**1.5.0**  
定位：**仅当前项目工作区生效，不做全局安装**  
受众：个人开发者及其 AI Agent

> 📖 **使用手册**：[YoYo V1.5.0 使用手册](YoYo_V1.5.0.md) — 安装步骤、六种工作流用法与常见问题，看这一份即可上手。

## 这是什么

YoYo 是当前项目唯一的工程治理 Skill 入口，内部包含六种工作流：新建、接管、二次开发、重构、维护、迁移。它不把六种模式拆成六个独立 Skill，也不把一个项目的技术规则扩散到其他项目。

## 安装

按 Agent 平台选择 `install/` 中的说明：
- Claude Code：`.claude/skills/yoyo/`
- Codex：`.agents/skills/yoyo/`
- 其他平台：必须先确认官方支持的项目级发现目录；不猜路径。

**禁止全局安装**：不放入 `~/.claude/skills/`、`~/.agents/skills/` 或系统级目录。

项目级安装限定 Skill 的适用/发现范围，不等于安全沙箱；实际文件、命令和网络权限仍由平台 sandbox/permission 控制。

## 项目状态

项目专属状态放在项目根目录 `.yoyo/`，与 Skill 本体分离。Skill 升级不得覆盖 `.yoyo/`。新项目按需创建；旧项目先读取已有资料，不强迫迁移目录或重建项目。

## 六种工作流

| 目标 | 模式 | 入口文件 |
|---|---|---|
| 从零建设 | NEW_PROJECT | `workflows/new-project.md` |
| 接手并理解旧项目 | PROJECT_TAKEOVER | `workflows/project-takeover.md` |
| 增加功能/改变行为 | SECONDARY_DEVELOPMENT | `workflows/secondary-development.md` |
| 保持行为、改善结构 | REFACTORING | `workflows/refactoring.md` |
| 修复缺陷/稳定性 | MAINTENANCE | `workflows/maintenance.md` |
| 更换技术/平台/数据 | MIGRATION | `workflows/migration.md` |

工作流可以串联，但要拆清阶段和验收目标，例如 TAKEOVER → REFACTORING → SECONDARY_DEVELOPMENT。

## 规范架构

- `SKILL.md`：唯一入口和核心规则。
- `core/`：工作区边界、路由、规范调度和质量门禁。
- `workflows/`：六种任务流程。
- `references/`：选定的原始规范，按需读取。
- `templates/project-state/`：复制到项目 `.yoyo/` 的档案模板。
- `templates/`：任务、评估、风险和交付模板。

## 使用示例

- “按 YoYo 新建流程初始化当前工作区，先确定骨架，再做最小可运行基线。”
- “按 YoYo 接管流程只读评估当前仓库，不改业务代码。”
- “按 YoYo 二开流程增加这个功能，先给影响分析和验收计划。”
- “按 YoYo 重构流程改善这个模块，保持外部行为不变。”
- “按 YoYo 维护流程修复这个 Bug，先复现和定位根因。”
- “按 YoYo 迁移流程制定分阶段方案，先给备份、校验、切换和回滚计划。”

## 升级原则

升级 Skill 本体与迁移项目档案是两件事。更新 Skill 时先比较文件差异；`.yoyo/` 中的项目规则、决策、例外和历史报告不由 Skill 包覆盖。
