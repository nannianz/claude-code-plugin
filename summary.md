# claude-code-plugin 发布、下载、更新指南

## 目录结构

```
claude-code-plugin/
├── README.md              # 项目首页，Skills 列表
├── summary.md             # 本文档
└── skills/
    └── ga/
        ├── SKILL.md       # Skill 定义文件
        └── README.md      # Skill 说明文档
```

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

### 2. 更新首页 README

在 `README.md` 的 Skills 表格中添加新条目：

```markdown
| My Skill | 技能描述 | `npx skills add nannianz/skills --path skills/my-skill` |
```

### 3. 提交并推送

```bash
git add -A
git commit -m "feat: add my-skill"
git push origin master
```

## 下载安装

### 方式 1：npx 一键安装（推荐）

```bash
# 安装指定 Skill
npx skills add nannianz/skills --path skills/ga

# 查看仓库中有哪些 Skills
npx skills add nannianz/skills --list

# 安装到全局（所有项目可用）
npx skills add nannianz/skills --path skills/ga -g

# 指定只安装到 Claude Code
npx skills add nannianz/skills --path skills/ga -a claude-code
```

### 方式 2：手动安装

**Linux/Mac：**

```bash
mkdir -p ~/.claude/skills/ga
curl -s https://raw.githubusercontent.com/nannianz/skills/master/skills/ga/SKILL.md > ~/.claude/skills/ga/SKILL.md
```

**Windows PowerShell：**

```powershell
mkdir "$env:USERPROFILE\.claude\skills\ga" -Force
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/nannianz/skills/master/skills/ga/SKILL.md" -OutFile "$env:USERPROFILE\.claude\skills\ga\SKILL.md"
```

### 方式 3：复制到项目本地

将 `skills/ga/` 目录复制到你项目的 `.claude/skills/ga/` 下。

## 更新

```bash
# 更新指定 Skill
npx skills update ga

# 更新所有已安装的 Skills
npx skills update

# 只更新全局的
npx skills update -g

# 非交互式（自动检测范围）
npx skills update -y
```

> **注意：** 更新后需要重启 Claude Code 才能生效。
