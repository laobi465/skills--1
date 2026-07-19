# 更新日志（CHANGELOG）

> 本文件记录 web-project-flow Skill 的所有版本变更。
> 格式：语义化版本号 + 日期 + 分类条目（[新增] / [修改] / [修复] / [移除] / [废弃] / [安全]）
> 按版本倒序排列，最新版本置顶。

---

## [0.2.0] - 2026-07-19

### 新增
- **快捷命令系统**：为 11 份提示词新增 `/b` 前缀快捷命令（`/bstart`、`/bfuzzy`、`/bui`、`/bhardcode`、`/bconfig`、`/bhaluc`、`/bonboard`、`/baudit`、`/bdocs`、`/bhandover`、`/bdeploy`）
- **SKILL.md §3.5 快捷命令清单章节**：含命令表、执行规则、铁律叠加规则、链式调用、未识别命令处理、命令速查示例
- **链式调用支持**：空格分隔多个命令一次性加载（如 `/bhardcode /bconfig /bhaluc`）
- **铁律自动叠加机制**：涉及代码生成的命令自动连带加载铁律三件套（04 + 05 + 06）
- **CHANGELOG.md**：本文件（按 references/09 规范维护）
- **PROJECT.md**：项目文档（架构、功能、使用指南）
- **SPEC.md**：规范文档（代码/架构/接口/提交/测试/安全）
- **TODO.md**：待办清单（P0-P3 优先级）

### 修改
- **README.md**：使用方式从两种扩展为三种（自然语言 / `/b` 快捷命令 / `/bhelp` 索引），新增命令组合与链式调用示例
- **PROMPT.md**：「`/bhelp` 命令规范」章节升级为「`/b` 快捷命令规范」，含单提示词命令表、执行规则、命令速查
- **SKILL.md description 字段**：新增 11 个快捷命令清单，便于 AI 自动路由匹配

---

## [0.1.0] - 2026-07-19

### 新增
- **web-project-flow Skill 初版**：网站项目开发全生命周期 Skill，内置 11 份提示词
- **SKILL.md 主入口**：YAML frontmatter（name + description）、路由表、`/bhelp` 命令、铁律强制加载机制
- **references/01-project-start.md**：项目起步提示词（完整版 + 精简版）
- **references/02-fuzzy-idea-to-plan.md**：模糊想法落地 10 步流程
- **references/03-ui-design-rules.md**：现代简约 UI 设计规则（含禁用项）
- **references/04-no-hardcode-fake-data.md**：铁律①禁硬编码假数据
- **references/05-config-to-backend.md**：铁律②配置后台化（sys_config 表设计）
- **references/06-anti-hallucination.md**：铁律③防 AI 幻觉
- **references/07-ai-onboarding.md**：AI 对接新项目引导
- **references/08-project-audit.md**：项目全方位深度检查（5 维度 + 分级标注）
- **references/09-docs-lifecycle.md**：四份核心文档维护规范
- **references/10-handover-docs.md**：项目交接文档生成
- **references/11-github-auto-update.md**：GitHub 自动更新管理系统
- **README.md**：项目介绍（含目录结构、11 份提示词一览、使用方式、铁律、UI 约束、全流程示例）
- **PROMPT.md**：AI 对接引导文档（含阅读顺序、铁律三件套、路由表、`/bhelp` 命令规范、文件顶部注释规范、提交规范、版本号规范、启动检查清单）
- **`/bhelp` 命令**：提示词索引（支持默认索引、按编号查询、按关键词搜索）

### 安全
- **铁律强制加载**：references/04、05、06 三份硬约束文档，所有代码生成必须满足，违反即重写
- **UI 禁用项**：禁 emoji / 禁毛玻璃 / 禁暗黑风格 / 禁夸张渐变 / 禁过度装饰

---

## 版本号规则

按 [references/09-docs-lifecycle.md](./web-project-flow/references/09-docs-lifecycle.md) 第 2 节：

- **主版本号 X.0.0**：重大功能 / 破坏性变更
- **次版本号 0.X.0**：新增功能 / 向下兼容
- **修订号 0.0.X**：修复 / 小优化

## 分类说明

| 标签 | 含义 |
|---|---|
| `[新增]` | 新增功能 / 文件 / 能力 |
| `[修改]` | 对已有功能的调整 / 优化 |
| `[修复]` | Bug 修复 |
| `[移除]` | 删除功能 / 文件 |
| `[废弃]` | 标记即将移除 |
| `[安全]` | 安全相关变更 |
