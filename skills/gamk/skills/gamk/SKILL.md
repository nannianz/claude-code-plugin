---
name: gamk
description: Git 快捷操作 - 暂存 / 提交 / 撤销提交
version: 1.0.0
---

# Git 快捷操作

根据用户输入的命令执行不同的 Git 操作。

## 命令速查表

| 命令 | 等效操作 | 说明 |
|------|---------|------|
| `/gamk` | `git add .` | 暂存所有变更 |
| `/gamk c xxx` | `git add . && git commit -m "xxx"` | 暂存并提交 |
| `/gamk r` | `git reset --soft HEAD~1` | 撤销上一次 commit（保留代码更改） |

## Execution

### `/gamk` → 暂存所有变更

```bash
git add .
```

### `/gamk c xxx` → 暂存并提交

```bash
git add .
git commit -m "xxx"
```

### `/gamk r` → 撤销上次提交

```bash
git reset --soft HEAD~1
```
