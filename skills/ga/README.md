# Ga

Git 快捷操作 - 暂存 / 提交 / 撤销提交。

## Install

**方式一：npx skills（在目标项目目录下运行）**

```bash
npx skills add nannianz/skills --path skills/ga
```

**方式二：手动安装**

将 `skills/ga/` 目录复制到你项目的 `.claude/skills/ga/` 下。

## Uninstall

**npx 安装的（在项目目录下运行）：**

```bash
npx skills remove ga
```

**手动删除（在项目目录下运行）：**

```bash
# Linux/Mac
rm -rf .claude/skills/ga

# Windows PowerShell
Remove-Item -Recurse -Force .claude\skills\ga
```

## Update

```bash
# 在项目目录下运行
npx skills update ga
```

> **注意：** 安装或更新后需要重启 Claude Code 才能生效。

## Usage

| 命令 | 作用 | 等效 Git |
|------|------|----------|
| `/ga` | 暂存所有变更 | `git add .` |
| `/ga c 提交信息` | 暂存并提交 | `git add . && git commit -m "提交信息"` |
| `/ga r` | 撤销上次提交（保留更改） | `git reset --soft HEAD~1` |
