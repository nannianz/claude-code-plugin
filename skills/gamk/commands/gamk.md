---
description: Git 快捷操作 - 暂存 / 提交 / 撤销提交。用法：/gamk（暂存）、/gamk c 提交信息（暂存并提交）、/gamk r（撤销上次提交）
allowed-tools: Bash(git add:*), Bash(git commit:*), Bash(git reset:*)
---

根据用户的输入参数执行对应的 Git 操作。

## 命令

### 无参数 → 暂存所有变更

执行 `git add .`，将工作目录中的所有变更添加到暂存区。

### `c xxx` → 暂存并提交

执行以下命令：

```bash
git add .
git commit -m "xxx"
```

xxx 为用户提供的提交信息。

### `r` → 撤销上次提交（保留更改）

执行 `git reset --soft HEAD~1`，撤销上一次 commit 但保留代码更改在暂存区。
