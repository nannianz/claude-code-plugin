# Gamk

Git 快捷操作 - 暂存 / 提交 / 撤销提交。

## Install

**方式一：Claude Code Marketplace**

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install gamk --scope project

# 3. 激活
/reload-plugins
```

**方式二：npx skills（在目标项目目录下运行）**

```bash
npx skills add nannianz/skills --path skills/gamk
```

**方式三：手动安装**

将 `skills/gamk/` 目录复制到你项目的 `.claude/skills/gamk/` 下。

## Uninstall

**Marketplace 安装的：**

```bash
/plugin uninstall gamk
```

**npx 安装的（在项目目录下运行）：**

```bash
npx skills remove gamk
```

**手动删除（在项目目录下运行）：**

```bash
# Linux/Mac
rm -rf .claude/skills/gamk

# Windows PowerShell
Remove-Item -Recurse -Force .claude\skills\gamk
```

## Update

```bash
# 在项目目录下运行
npx skills update gamk
```

> **注意：** 安装或更新后需要重启 Claude Code 才能生效。

## Usage

| 命令 | 作用 | 等效 Git |
|------|------|----------|
| `/gamk` | 暂存所有变更 | `git add .` |
| `/gamk c 提交信息` | 暂存并提交 | `git add . && git commit -m "提交信息"` |
| `/gamk r` | 撤销上次提交（保留更改） | `git reset --soft HEAD~1` |
