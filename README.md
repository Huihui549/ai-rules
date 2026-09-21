# ai-rules — AI 协作薄底座

跨项目、跨工具都成立的行为约束：管"**怎么和 AI 协作**"（输出、上报、授权边界、命令安全、git、注释纪律）。
不管"这个项目是什么"——那属于项目侧的 `AGENTS.md` 与 `dev-docs/`（见 R6）。

## 目录结构

| 路径 | 用途 |
|---|---|
| `workflow.md` | **用户手册**：分层分工（7 件）+ 开发新功能五步流程（先读这个） |
| `README.md` | 索引 + 命名约定 + 规则索引 |
| `rules/` | 行为规则 R1–R11，一条规则一个文件 |
| `roles/` | 角色档案（engineer / learner / consultant / friend），按交互模式自动切换 |
| `templates/` | `dialogue-opening.md`（开场规则段）、`project-skeleton/`（README.md 给出放置路径 + AGENTS.md、context.md、spec.md、verify.md、dev.md、pitfalls.md、adr.md；整目录复制） |
| `logs/` | 通用教训沉淀（项目专属的坑写各项目 `pitfalls.md`） |

## 使用流程

0. **先读** `workflow.md`（人读的用户手册：分层、步骤、你只需做什么）
1. **新项目**：复制 `templates/project-skeleton/` 到项目，生成根目录 `AGENTS.md` 与 `dev-docs/<项目名>/`；已有项目缺 `AGENTS.md` 时，首轮会话让 AI 按该骨架补齐
2. **每次对话**：工具支持自动加载就靠 `AGENTS.md`；不支持则粘贴 `templates/dialogue-opening.md`
3. **收尾**：AI 自动把坑/决策/验收回填到项目文档（R5、R6）；只有跨项目且出现 ≥2 次的才升格进 `rules/`（R7）

## 命名与格式约定

- 文件名 `kebab-case`；字母数字简称必须作前缀（如 `R1-output.md`），见 R7
- 规则文件必须带 frontmatter：`name` / `description` / `scope` / `priority`
- **单一事实源（SSOT）**：每条规则全文只在其归属文件，别处只引用编号（R7）

## 规则索引（规则变更后必须同步，R7）

| 编号 | 文件 | 摘要 |
|---|---|---|
| R1 | `rules/R1-output.md` | 输出：结构骨架/默认框架+按需展开/「存在问题建议修复」/问题分级与自治/自检与审查 |
| R2 | `rules/R2-truthfulness.md` | 真实性与反驳：事实优先，错误必指出，数据须实测 |
| R3 | `rules/R3-workflow.md` | 协作流程：意图边界/五步/批量逐条/注释保护 |
| R4 | `rules/R4-git.md` | git：前置检查/只读白名单/AI 不做任何写操作 |
| R5 | `rules/R5-session-memory.md` | 会话：新会话读一次/渐进式披露/肯定记录/收尾回填/压缩保规则 |
| R6 | `rules/R6-feature-docs.md` | 项目文档体系：AGENTS.md 分工/功能文档五件套/日志可重放/写法规范 |
| R7 | `rules/R7-rule-maintenance.md` | 规则维护：命名/归置判断/升格门槛/单一事实源/冲突裁决/索引同步 |
| R8 | `rules/R8-code-hygiene.md` | 代码卫生：改动边界/删除优先/YAGNI/过度抽象/诡代码/性能/P0–P3 |
| R9 | `rules/R9-command-safety.md` | 命令安全：破坏性命令先说明后果、获批准才执行 |
| R10 | `rules/R10-self-rebuttal.md` | 收敛分析：≤5 轮"完整分析+输出检查"；轮次三行必报 |
| R11 | `rules/R11-comment-doc.md` | 注释与文档分工：代码留路标、文档写全文 |

## 与工具生态对接

- **AGENTS.md / CLAUDE.md**：项目根放一份（由 `templates/project-skeleton/AGENTS.md` 生成），支持自动加载的工具每次自动读取
- **Skill**：稳定规则打包为 `SKILL.md`，跨项目复用（需要时再建 `skills/`）

## 状态

- `logs/lessons.md`：2 条待观察（其余已定稿为规则，或迁往项目侧 `pitfalls.md`）
- 历史：2026-08-18 原 R1–R13 合并为 R1–R7；2026-09-20 确立 SSOT；2026-09-20 薄底座重构——项目知识移出、模板补齐
