# Skills

Claude Code 自定义 Skill 插件集合。所有安装均为**项目级**（仅当前项目可用）。

## Skills

| Skill | Type | Description |
|-------|------|-------------|
| Ga | Skill | Git 快捷操作（npx 安装） |
| Gamk | Command | Git 快捷操作（Marketplace 安装） |
| SDLC | Agent | Agentic SDLC 全流程智能体（Marketplace 安装） |
| Issue-Fix | Agent | 问题单开发流程（修复落地 + 自测报告，Marketplace 安装） |

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

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install gamk --scope project

# 3. 激活
/reload-plugins
```

### Uninstall

```bash
/plugin uninstall gamk
```

## SDLC

Agentic SDLC 全流程智能体 - 以规格（Spec）为中心的八环节流水线（需求→发布）。这是本仓库的**第一个 Agent**（子智能体），区别于 Ga/Gamk 的 Skill/Command。

### Install

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install sdlc --scope project

# 3. 激活
/reload-plugins
```

### Uninstall

```bash
/plugin uninstall sdlc
```

### 触发方式

当需要**端到端实现一个需求或功能**、走完整软件开发生命周期时，主 Claude 会自动委派给 SDLC 智能体（也可显式 `@sdlc` 或要求「走 SDLC 全流程」）。

| 环节 | 产物 | 门禁 |
|------|------|------|
| S1 需求分析 | `requirements/analysis.md` | 人工门禁 |
| S2 需求设计（Spec） | `specs/<feature>/spec.md` | **人工签署** ⚑ |
| S3 软件设计 | `specs/<feature>/design.md` + ADR | 人工门禁 |
| S4 任务分解编排 | `specs/<feature>/tasks.md` | 自动 + 抽查 |
| S5 编码 + 测试 | 源码 + 单测/集成测试 | 双层 Review |
| S6 集成验证 | E2E 测试 + 回归报告 | CI 门禁 |
| S7 文档 | API 文档 / CHANGELOG / 用户文档 | Agent 校对 |
| S8 发布 | 安全扫描 + 回归报告 + 发布记录 | **人工拍板** ⚑ |

> 每环节遵循「Agent 执行 → Agent Review → 人工 Review」三层模型，在 Spec 签署 / 架构批准 / 发布决策三个不可逆决策点停下交回用户。

## Issue-Fix

问题单开发流程智能体（轻量三段式）- 把一个 Jira 问题单从**根因**推进到**修复落地 + 自测**，全程只产一个文件。与 SDLC 互补：SDLC 管「造新功能」，Issue-Fix 管「修问题单」；上游「问题单分析技能」产出根因后由它接力。

### Install

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install issue-fix --scope project

# 3. 激活
/reload-plugins
```

### Uninstall

```bash
/plugin uninstall issue-fix
```

### 触发方式

当需要**修复一个问题单 / 出自测报告**时，主 Claude 会自动委派给 Issue-Fix 智能体（也可显式 `@issue-fix`）。

产物为单文件 `<目标仓库>/openspec/requirements/<ISSUE-KEY>.md`，格式严格按自测报告（问题单号 / Root Cause / 影响范围 / 修复方案 / 测试版本 / 测试人 + Test Points 表 + 测试步骤与结果）。四项交付映射：问题原因→Root Cause、修改范围→影响范围、修改方案→修复方案、修改分支→测试版本。

| 段 | 往文件里填 | 门禁 |
|----|-----------|------|
| F1 定位 | 问题单号 / Root Cause（问题原因）/ 影响范围（修改范围） | 干净上下文自审 |
| F2 方案 | 修复方案（修改方案）/ 测试版本（修改分支）/ 测试人 / Test Points | **人工门禁** ⚑ |
| F3 实施 | 测试环境 / 测试步骤与结果（修改前·修改后·保存·回显）/ Result | 停下汇报（不提交） |

## Usage

Ga 与 Gamk 功能相同（仅安装方式不同）：

| 命令 | 作用 | 等效 Git |
|------|------|----------|
| `/gamk` | 暂存所有变更 | `git add .` |
| `/gamk c 提交信息` | 暂存并提交 | `git add . && git commit -m "提交信息"` |
| `/gamk r` | 撤销上次提交（保留更改） | `git reset --soft HEAD~1` |

> **注意：** 安装或更新后需要重启 Claude Code 才能生效。
