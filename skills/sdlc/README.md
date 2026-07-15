# SDLC

Agentic SDLC 全流程智能体（面向**前后端全栈**）- 以规格（Spec）为中心的八环节流水线，驱动一个需求从「需求分析」一路推进到「发布」。

每个环节遵循「**Agent 执行 → Agent Review → 人工 Review**」三层模型，并在 **Spec 签署 / 架构批准 / 发布决策** 三个不可逆决策点停下交回用户。

## Install

```bash
# 1. 添加 marketplace 源（首次需要）
/plugin marketplace add nannianz/skills

# 2. 安装到当前项目
/plugin install sdlc --scope project

# 3. 激活
/reload-plugins
```

## Uninstall

```bash
/plugin uninstall sdlc
```

## Usage

当需要**端到端实现一个需求或功能**、走完整软件开发生命周期时，主 Claude 会自动委派给 SDLC 智能体（也可显式 `@sdlc` 或要求「走 SDLC 全流程」）。

SDLC 按以下八环节推进，每环节产物入 Git、过门禁后进入下一环节：

| 环节 | 产物 | 门禁 | 前后端要点 |
|------|------|------|-----------|
| S1 需求分析 | `requirements/analysis.md` | 人工门禁 | 前后端双视角质询；强制「开放问题」清单 |
| S2 需求设计（Spec） | `specs/<feature>/spec.md` | **人工签署** ⚑ | AC 分前后端两节 + 跨面契约 ID 关联；EARS 强制；NFR 可测阈值 |
| S3 软件设计 | `specs/<feature>/design.md` + `adr/` | **架构批准** ⚑ | FE↔BE 契约冻结（单一事实源 + codegen）；ADR 独立文件 |
| S4 任务分解编排 | `specs/<feature>/tasks.md` | 自动 + 抽查 | 接口先行（契约 + mock → 前后端并行 → 集成换真）；依赖图 + 关键路径 |
| S5 编码 + 测试 | 源码 + 测试（同一 PR） | 双层 Review | 严格 test-first；前后端分层金字塔（BE 含契约测试） |
| S6 集成验证 | E2E + 回归报告 | CI 门禁 | 全链路真实环境 E2E；与实现分离；收口跨面成对行为 |
| S7 文档 | API / CHANGELOG / 用户文档等 | Agent 校对 | 前后端文档矩阵 + 派生映射；文档-代码一致性校对 |
| S8 发布 | 安全扫描 + 回归报告 + 发布记录 | **人工拍板** ⚑ | 前后端发布清单；数据迁移 up/down + 回滚；全量发布 |

> 一条主线贯穿全流程：**S2 跨面成对 AC（`FE-AC ↔ BE-AC`）→ S3 冻结为接口契约 → S4 接口先行并行 → S6 端到端收口验证**。⚑ 为三个必守人类门禁。

> **注意：** 安装后需要重启 Claude Code 才能生效。
