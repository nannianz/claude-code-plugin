---
# 技能名称，用于标识和调用
name: ga
# 技能描述，说明该技能的用途
description: Git 快捷操作 - 暂存 / 提交 / 撤销提交
# 别名列表，支持其他触发方式
aliases:
  - gc
  - gr
# 标记该技能可由用户直接调用
user-invocable: true
# 该技能允许使用的工具列表，这里仅需 Bash 执行 git 命令
allowed-tools:
  - Bash
---

# Git 快捷操作

根据用户输入的命令执行不同的 Git 操作。

## 命令速查表

| 命令 | 等效操作 | 说明 |
|------|---------|------|
| `/ga` | `git add .` | 暂存所有变更 |
| `/ga c xxx` | `git commit -m "xxx"` | 使用 xxx 作为提交信息 |
| `/ga r` | `git reset --soft HEAD~1` | 撤销上一次 commit（保留代码更改） |

## Execution（执行方式）

### 1. `/ga` → 暂存所有变更

```bash
# 将工作目录中的所有变更添加到暂存区
# 包括：新文件（untracked）、已修改文件（modified）、已删除文件（deleted）
git add .
```

### 2. `/ga c xxx` → 提交代码

xxx 作为提交信息：

```bash
# 使用用户提供的参数作为提交信息进行提交
git commit -m "xxx"
```

### 3. `/ga r` → 撤销上一次提交（保留代码更改）

```bash
# 撤销上一次 commit，但保留代码更改在暂存区
# HEAD~1 指向上一次 commit 的父提交，--soft 保留更改在 staged 状态
git reset --soft HEAD~1
```
