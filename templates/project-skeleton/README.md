# 项目文档骨架（project-skeleton）— 复制到项目后的放置路径

> 整目录复制到项目，然后按下表放置（**AI 会自动完成**，见 R6「自动创建与维护」）。

| 模板 | 目标路径 | 级别 |
|---|---|---|
| `AGENTS.md` | `<项目根>/AGENTS.md` | 项目级 |
| `context.md` | `dev-docs/<项目名>/context.md` | 项目级 |
| `pitfalls.md` | `dev-docs/<项目名>/pitfalls.md` | 项目级 |
| `adr.md` | `dev-docs/<项目名>/adr/0001-<主题>.md` | 项目级 |
| `spec.md` | `dev-docs/<项目名>/features/<功能名>/spec.md` | 功能级 |
| `verify.md` | `dev-docs/<项目名>/features/<功能名>/verify.md` | 功能级 |
| `dev.md` | `dev-docs/<项目名>/features/<功能名>/dev.md` | 功能级 |

```
<项目根>/
├── AGENTS.md
└── dev-docs/<项目名>/
    ├── context.md
    ├── pitfalls.md
    ├── adr/0001-<主题>.md
    ├── requirements/ design/ ops/
    └── features/<功能名>/
        ├── spec.md
        ├── verify.md
        └── dev.md
```

判据：**会跨功能复用 → 项目级；只描述本次做完没有 → 功能级**（坑、决策属项目级）。
