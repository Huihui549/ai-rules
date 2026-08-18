# ai-rules — AI 编程协作规范库

集中管理所有"约束 AI 输出、提升协作质量"的文档。目标：让 AI 的输出符合预期、避免无用信息，且文档本身**结构规范、可演进**。

## 目录结构

| 路径 | 用途 | 何时新增/修改 |
|---|---|---|
| `README.md` | 本索引 + 使用说明 | 结构变化时 |
| `context/` | 项目上下文：技术栈、芯片、工具链、硬性约束，**每个项目一份** | 新项目启动时 |
| `rules/` | 约束规则：输出格式 / 负面清单 / 协作流程，**每条规则一个文件** | AI 反复犯同类错误时 |
| `templates/` | 可直接复制的模板：对话开场规则段、任务提示 | 需要复用模板时 |
| `logs/` | 踩坑沉淀区：记录 AI 不符合预期的行为 | 每次对话结束有教训时 |

## 使用流程（三层递进）

1. **每次对话**：打开 `templates/dialogue-opening.md`，复制规则段粘贴到对话开头（约束立刻生效，零成本）。
2. **发现新问题**：把"AI 又做了什么我不想要的"记入 `logs/lessons.md`；同类问题出现 2 次 → 提炼成 `rules/` 下的一条正式规则。
3. **跨项目复用**：当某条规则稳定且通用 → 打包升级为 `SKILL.md`（届时再创建 `skills/` 目录）。

## 命名与格式约定（"规范"所在）

- 文件名：`kebab-case`；**字母数字代指简称必须作为文件名前缀**（如 `R1-output-format.md`），见 R7
- 每个规则文件**必须**带 YAML frontmatter：`name` / `description` / `scope` / `priority`
- 规则编号：R1、R2……便于在 logs 和对话中引用
- 模板文件开头标注"复制即用"，规则文件标注"合并进 AGENTS.md 用"

## 规则索引（自动更新）

> 约定：**每次规则新增/修改/合并后，必须同步更新本索引**（R13）。一句话摘要，详见对应文件。

| 编号 | 文件 | 摘要 |
|---|---|---|
| R1 | `rules/R1-output-format.md` | 输出格式：结构/长度/精炼/语言/边界 |
| R2 | `rules/R2-negative-list.md` | 负面清单：禁止的输出内容 |
| R3 | `rules/R3-workflow.md` | 协作流程：git 前置检查、复述、计划、小步、验证 |
| R4 | `rules/R4-truthfulness.md` | 真实性与反驳：事实优先于顺应 |
| R5 | `rules/R5-git-policy.md` | git 跟踪策略：只跟文本，.gitignore 自忽略 |
| R6 | `rules/R6-self-check.md` | 输出自检：8 项检查清单 |
| R7 | `rules/R7-naming.md` | 命名：字母数字代指必须作文件名前缀 |
| R8 | `rules/R8-feature-docs.md` | 功能文档：自动编写/审查/总结/精简 |
| R9 | `rules/R9-confirmed-records.md` | 肯定内容记录 + 新会话启动读取一次 |
| R10 | `rules/R10-context-cost.md` | 上下文与成本：规则完整优先，省 token |
| R11 | `rules/R11-intent-boundary.md` | 意图边界：咨询只建议，修改需明确授权 |
| R12 | `rules/R12-rule-accumulation.md` | 规则自动积累：有用通用限制自动入库 |
| R13 | `rules/R13-conflict-resolution.md` | 整合与冲突裁决：合并检查、优先级裁决 |

## 与工具生态的对接

- **AGENTS.md / CLAUDE.md**：把 `context/` + `rules/` 的成熟内容合并生成，放项目根目录，支持自动加载的工具（Claude Code / Cursor 等）会每次自动读取——省去手动粘贴。
- **Skill**：稳定规则打包成 `SKILL.md` 指令包，跨项目复用。

## 迁移说明

根目录 `ai-dev-workflow-cheatsheet.md` 是早期平铺版本，内容已整合进本目录各文件，不再维护。`prompt01.txt` 属单任务需求书，可移入具体项目目录（如 `apple-evolution/`）归档。
