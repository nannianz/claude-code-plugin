# Ga

Git 快捷操作 - 暂存 / 提交 / 撤销提交。

## Install

```bash
npx skills add nannianz/claude-code-plugin --path skills/ga
```

## Update

```bash
npx skills update ga
```

## Usage

| 命令 | 作用 | 等效 Git |
|------|------|----------|
| `/ga` | 暂存所有变更 | `git add .` |
| `/ga c 提交信息` | 暂存并提交 | `git add . && git commit -m "提交信息"` |
| `/ga r` | 撤销上次提交（保留更改） | `git reset --soft HEAD~1` |
