# Skills

Claude Code 自定义 Skill 插件集合。所有安装均为**项目级**（仅当前项目可用）。

## Skills

| Skill | Description |
|-------|-------------|
| Ga | Git 快捷操作（npx 安装） |
| Gamk | Git 快捷操作（Marketplace 安装） |

## Ga

### Install

在目标项目目录下运行：

```bash
npx skills add nannianz/skills --path skills/ga
```

### Update

```bash
npx skills update ga
```

### Uninstall

```bash
npx skills remove ga
```

## Gamk

### Install

**方式一：Marketplace**

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install gamk --scope project

# 3. 激活
/reload-plugins
```

**方式二：npx（在目标项目目录下运行）**

```bash
npx skills add nannianz/skills --path skills/gamk
```

### Update

```bash
npx skills update gamk
```

### Uninstall

```bash
/plugin uninstall gamk
```

或：

```bash
npx skills remove gamk
```

## Usage

两个插件功能相同：

| 命令 | 作用 | 等效 Git |
|------|------|----------|
| `/gamk` | 暂存所有变更 | `git add .` |
| `/gamk c 提交信息` | 暂存并提交 | `git add . && git commit -m "提交信息"` |
| `/gamk r` | 撤销上次提交（保留更改） | `git reset --soft HEAD~1` |

> **注意：** 安装或更新后需要重启 Claude Code 才能生效。
