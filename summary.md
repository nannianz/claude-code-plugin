# Skills 发布、下载、更新指南

## 目录结构

```
claude-code-plugin/
├── .claude-plugin/
│   └── marketplace.json   # Marketplace 入口配置
├── README.md              # 项目首页，Skills 列表
├── summary.md             # 本文档
└── skills/
    ├── ga/                # npx 安装方式（Skill）
    │   ├── SKILL.md
    │   └── README.md
    ├── gamk/              # Marketplace 安装方式（Command）
    │   ├── .claude-plugin/
    │   │   └── plugin.json
    │   ├── commands/
    │   │   └── gamk.md    # 用户可调用的 /gamk 命令
    │   └── README.md
    └── sdlc/              # Marketplace 安装方式（Agent / 子智能体）
        ├── .claude-plugin/
        │   └── plugin.json
        ├── agents/
        │   └── sdlc.md    # SDLC 全流程子智能体定义
        └── README.md
```

> 类型差异：`ga` 是 **Skill**（SKILL.md），`gamk` 是 **Command**（commands/），`sdlc` 是 **Agent**（agents/）。

## 发布流程

### 1. 创建 Skill

在 `skills/` 下新建目录，放入 `SKILL.md` 文件：

```bash
mkdir -p skills/my-skill
npx skills init my-skill
```

`SKILL.md` 必须包含 `name` 和 `description` 字段：

```yaml
---
name: my-skill
description: 技能描述
user-invocable: true
allowed-tools:
  - Bash
---
```

> 若要发布的是 **Command**（slash 命令），改用 `commands/<name>.md`；若是 **Agent**（子智能体），改用 `agents/<name>.md`，frontmatter 用 `name` / `description`（触发条件）/ `tools` / `model`。参考 `skills/sdlc/agents/sdlc.md`。三种类型都需在 `.claude-plugin/marketplace.json` 注册。

### 2. 更新首页 README

在 `README.md` 的 Skills 表格中添加新条目。

### 3. 提交并推送

```bash
git add -A
git commit -m "feat: add my-skill"
git push origin master
```

## 下载安装

所有方式均为**项目级安装**（仅当前项目可用），需在目标项目目录下运行。

### Gamk（Marketplace）

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install gamk --scope project

# 3. 激活
/reload-plugins
```

卸载：

```bash
/plugin uninstall gamk
```

### SDLC（Marketplace，Agent）

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install sdlc --scope project

# 3. 激活
/reload-plugins
```

卸载：

```bash
/plugin uninstall sdlc
```

安装后，当需要端到端实现一个需求或功能时，主 Claude 会自动委派给 SDLC 子智能体（也可显式 `@sdlc` 或要求「走 SDLC 全流程」）。

### Ga（npx）

```bash
# 安装
npx skills add nannianz/skills --path skills/ga

# 更新
npx skills update ga

# 卸载
npx skills remove ga

# 查看仓库中有哪些 Skills
npx skills add nannianz/skills --list
```

## 更新

```bash
# 更新指定 Skill
npx skills update ga

# 更新所有已安装的 Skills
npx skills update

# 非交互式（自动检测范围）
npx skills update -y
```

> **注意：** 更新后需要重启 Claude Code 才能生效。
