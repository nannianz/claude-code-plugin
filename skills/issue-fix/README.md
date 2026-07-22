# Issue-Fix

问题单开发流程智能体（轻量三段式）- 把一个 Jira 问题单从**根因**推进到**修复落地 + 自测**，全程只产一个文件。

与 **SDLC**（端到端新功能，8 环节重型）互补：SDLC 管「造新功能」，issue-fix 管「修问题单」。上游的「问题单分析技能」（esp/dac/tmac/ac/esg-analysis）已产出根因 + 引入提交 + 目标分支，issue-fix 从这里接力。

## 流程（定位 → 方案 → 实施）

全程写入同一个文件 `<目标仓库>/openspec/requirements/<ISSUE-KEY>.md`，三段渐进填充，**格式严格按自测报告**（问题单号 / Root Cause / 影响范围 / 修复方案 / 测试版本 / 测试人 + Test Points 表 + 测试步骤与结果[修改前/修改后/保存/回显]）。

| 段 | 往文件里填 | 门禁 |
|----|-----------|------|
| F1 定位 | 问题单号 / **Root Cause（问题原因）** / **影响范围（修改范围）** | 干净上下文自审 |
| F2 方案 | **修复方案（修改方案）** / **测试版本（修改分支）** / 测试人 / Test Points | ⚑ **人工门禁（唯一必守点）** |
| F3 实施 | 测试环境 / 测试步骤与结果（修改前·修改后·保存·回显）/ Result | 停下汇报（不提交） |

> 四项交付与自测报告字段的映射：**问题原因→Root Cause**、**修改范围→影响范围**、**修改方案→修复方案**、**修改分支→测试版本**。

## Install

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install issue-fix --scope project

# 3. 激活
/reload-plugins
```

## Uninstall

```bash
/plugin uninstall issue-fix
```

## Usage

当需要**修复一个问题单、出自测报告**时，主 Claude 会自动委派给 issue-fix 智能体（也可显式 `@issue-fix` 或要求「修这个问题单 / 出自测报告」）。

触发后按三段推进：F1 定位根因与范围 → F2 出修复方案与修改分支并在该处**停下等用户放行** → 放行后 F3 编码 + 自测，写完**停下汇报（不提交）**。

> **注意：** 安装后需要重启 Claude Code 才能生效。
