# Ga-mk

Git 快捷操作 - 暂存 / 提交 / 撤销提交。

## Install

**方式一：Claude Code Marketplace**

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install ga-mk --scope project

# 3. 激活
/reload-plugins
```

**方式二：npx skills（在目标项目目录下运行）**

```bash
npx skills add nannianz/skills --path skills/ga-mk
```

**方式三：手动安装**

将 `skills/ga-mk/` 目录复制到你项目的 `.claude/skills/ga-mk/` 下。

## Uninstall

**Marketplace 安装的：**

```bash
/plugin uninstall ga-mk
```

**npx 安装的（在项目目录下运行）：**

```bash
npx skills remove ga-mk
```

**手动删除（在项目目录下运行）：**

```bash
# Linux/Mac
rm -rf .claude/skills/ga-mk

# Windows PowerShell
Remove-Item -Recurse -Force .claude\skills\ga-mk
```

## Update

```bash
# 在项目目录下运行
npx skills update ga-mk
```

> **注意：** 安装或更新后需要重启 Claude Code 才能生效。

## Usage

| 命令 | 作用 | 等效 Git |
|------|------|----------|
| `/ga` | 暂存所有变更 | `git add .` |
| `/ga c 提交信息` | 暂存并提交 | `git add . && git commit -m "提交信息"` |
| `/ga r` | 撤销上次提交（保留更改） | `git reset --soft HEAD~1` |
