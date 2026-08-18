---
name: naming
description: R7 命名约定——字母数字代指简称必须作为文件名前缀
scope: 本仓库所有文档
priority: medium
---

# R7 命名约定

## 规则

- 任何"字母数字代指简称"（如 R1、R2、SKILL-A）一旦用于指代某文件，**必须**作为该文件名的前缀
- 目的：打开目录即识别文件身份，无需打开文件才知道简称含义
- 示例：`R1-output-format.md`；不得命名为 `output-format.md` 再仅在文档内部标注 R1

## 适用范围

- `rules/` 下所有规则文件（当前：R1–R6）
- 未来新增的任何带编号/简称的文档，一律适用
- 无简称的文件不受影响（如 `context/project-context.md`）
