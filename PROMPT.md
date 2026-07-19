# PROMPT.md —— AI 对接新项目引导

> 这是给下一个 AI 看的开发规范和约定。任何接手本仓库的 AI 必须先完整读完本文档，再开始执行任务。

---

## 第一步：阅读顺序（强制）

请按以下顺序阅读，完全理解后再回答用户问题：

1. **先读 [README.md](./README.md)** —— 了解项目整体定位、目录结构、11 份提示词一览
2. **再读本文件 [PROMPT.md](./PROMPT.md)** —— 了解开发规范和约定（铁律 / 路由 / 命令）
3. **浏览 [web-project-flow/](./web-project-flow/)** 目录结构，搞清楚每个文件的作用
4. **根据用户意图**，从下方「路由表」找到对应 reference 并加载完整内容到上下文
5. **如果涉及代码生成**，必须主动加载「铁律三件套」`04 + 05 + 06`

---

## 项目核心定位

本仓库是一个 **TRAE Skill 包**，名为 `web-project-flow`，覆盖网站项目开发全生命周期。它**不是**一个可运行的网站项目本身，而是一套给 AI 使用的「提示词工程方案」。

- 入口文件：[web-project-flow/SKILL.md](./web-project-flow/SKILL.md)
- 提示词库：[web-project-flow/references/](./web-project-flow/references/)
- 提示词数量：11 份
- 约束强度：HARD（违反铁律需重写）

---

## AI 行为约定

### 1. 必须遵守的铁律（HARD，违反即重写）

涉及代码生成时，**强制加载**以下三份铁律到上下文：

| 文件 | 核心规则 |
|---|---|
| [04-no-hardcode-fake-data.md](./web-project-flow/references/04-no-hardcode-fake-data.md) | 禁硬编码（密钥/token/域名/IP/配置参数）；禁假数据；测试数据必须标注 `// 仅本地测试模拟` |
| [05-config-to-backend.md](./web-project-flow/references/05-config-to-backend.md) | 所有可调参数走 `sys_config` 表 + `config('key', 'default')` 读取 + 缓存 + 后台可视化 |
| [06-anti-hallucination.md](./web-project-flow/references/06-anti-hallucination.md) | 基于事实回答；存疑标注「待核实」；不确定的写法标注「需验证」；回答末尾说明可信度 |

### 2. 不要做的事

- **不要**主动重构已有功能，只做用户要求的改动
- **不要**瞎猜 —— 有疑问先问
- **不要**编造不存在的 API、表名、字段、配置项
- **不要**在 UI 中使用 emoji / 毛玻璃 / 暗黑风格 / 夸张渐变
- **不要**跳过铁律直接写代码
- **不要**创建与本 Skill 无关的文件（如 `.md` 文档、`README` 等），除非用户明确要求

### 3. 必须做的事

- 修改代码前先确认理解了原有逻辑
- 保持现有代码风格和命名规范
- 任何代码生成前先确认铁律已加载
- 涉及需求变更时，按 [09-docs-lifecycle.md](./web-project-flow/references/09-docs-lifecycle.md) 联动更新四份文档
- 完成任务后，主动告诉用户下一步可以做什么

---

## 路由表：根据用户意图加载对应提示词

| 阶段 | 触发关键词 | 调用文件 |
|---|---|---|
| 起步（明确需求） | 我要做一个网站 / 网站类型 + 功能清单 | [01-project-start.md](./web-project-flow/references/01-project-start.md) |
| 起步（模糊想法） | 我有个想法 / 帮我落地 / 模糊商业想法 | [02-fuzzy-idea-to-plan.md](./web-project-flow/references/02-fuzzy-idea-to-plan.md) |
| 设计 | UI 设计 / 配色 / 页面风格 | [03-ui-design-rules.md](./web-project-flow/references/03-ui-design-rules.md) |
| 铁律 ① | 写业务代码前 / 检查硬编码 | [04-no-hardcode-fake-data.md](./web-project-flow/references/04-no-hardcode-fake-data.md) |
| 铁律 ② | 新增配置项 / 系统配置后台化 | [05-config-to-backend.md](./web-project-flow/references/05-config-to-backend.md) |
| 铁律 ③ | 防止幻觉 / 待核实 | [06-anti-hallucination.md](./web-project-flow/references/06-anti-hallucination.md) |
| AI 接入 | 让 AI 接手 / 读懂项目 | [07-ai-onboarding.md](./web-project-flow/references/07-ai-onboarding.md) |
| 检查 | 项目检查 / 审计 / 安全扫描 | [08-project-audit.md](./web-project-flow/references/08-project-audit.md) |
| 文档 | 变更 / 加功能 → 同步四份文档 | [09-docs-lifecycle.md](./web-project-flow/references/09-docs-lifecycle.md) |
| 交接 | 项目完成 / 生成 README / PROMPT | [10-handover-docs.md](./web-project-flow/references/10-handover-docs.md) |
| 部署 | GitHub 自动更新 / Webhook | [11-github-auto-update.md](./web-project-flow/references/11-github-auto-update.md) |

---

## `/bhelp` 命令规范

用户输入 `/bhelp` 时，按 [SKILL.md 第 3 章](./web-project-flow/SKILL.md) 规范输出索引：

| 输入 | 行为 |
|---|---|
| `/bhelp` | 输出 11 份提示词完整索引表 |
| `/bhelp all` | 同 `/bhelp` |
| `/bhelp <编号>` | 输出对应编号的提示词完整内容（调用 Read 读取文件） |
| `/bhelp <关键词>` | 按关键词命中表输出匹配清单 |

**规则**：
- 不调用业务工具，不修改文件，不启动开发流程
- 仅展示索引或对应提示词内容
- 输出完成后主动询问：「需要我加载哪一份提示词并开始执行吗？」

---

## 文档体系维护

仓库维护以下核心文档，按 [09-docs-lifecycle.md](./web-project-flow/references/09-docs-lifecycle.md) 规范联动更新：

| 文档 | 路径 | 作用 |
|---|---|---|
| `README.md` | 仓库根 | 项目介绍、目录结构、使用方式（给人类看） |
| `PROMPT.md` | 仓库根 | AI 对接引导、开发规范、路由表（给 AI 看） |
| `CHANGELOG.md` | （按需创建） | 更新日志 |
| `PROJECT.md` | （按需创建） | 项目文档 |
| `SPEC.md` | （按需创建） | 规范文档 |
| `TODO.md` | （按需创建） | 待办清单 |

---

## 文件顶部注释规范

新增 `.py` / `.js` / `.ts` / `.go` / `.php` 等代码文件时，顶部必须加注释：

```python
# -*- coding: utf-8 -*-
# File: <文件名>
# Description: <一句话功能描述>
# Author: web-project-flow
# Created: <YYYY-MM-DD>
# Stage: <阶段名，如 起步/设计/铁律/检查/文档/交接/部署>
# Reference: <对应 references/XX-xxx.md，如有>
```

Markdown 文件不加顶部注释，但 reference 文件保留 HTML 注释头：

```markdown
<!--
reference: <文件名>
source: <原始来源>
stage: <阶段>
constraint_level: HARD（仅铁律类标注）
-->
```

---

## 提交规范（Commit Message）

按 [09-docs-lifecycle.md](./web-project-flow/references/09-docs-lifecycle.md) 第 3 节规范：

```
<type>(<scope>): <subject>

<body>
```

`type` 取值：`feat` / `fix` / `docs` / `style` / `refactor` / `test` / `chore` / `security`

例：

```
feat(06-anti-hallucination): 新增防幻觉铁律提示词
fix(03-ui-design-rules): 修正暗黑风格禁用项描述
docs(README): 更新项目介绍与使用方式
security(05-config-to-backend): 强制 sys_config 缓存键隔离
```

---

## 版本号规范（语义化）

按 [09-docs-lifecycle.md](./web-project-flow/references/09-docs-lifecycle.md) 第 2 节：

- 重大功能 / 破坏性变更 → 主版本号 +1（`X.0.0`）
- 新增功能 / 向下兼容 → 次版本号 +1（`0.X.0`）
- 修复 / 小优化 → 修订号 +1（`0.0.X`）

当前版本：`0.1.0`（首版）

---

## 启动检查清单（接手前必读）

新 AI 接手本仓库时，确认以下事项：

- [ ] 已读 README.md，了解项目定位
- [ ] 已读本文件 PROMPT.md，了解开发规范
- [ ] 已浏览 [web-project-flow/](./web-project-flow/) 目录结构
- [ ] 知道铁律三件套 `04 + 05 + 06` 的存在和强制加载时机
- [ ] 知道 `/bhelp` 命令的输出格式
- [ ] 知道路由表如何根据用户意图加载对应 reference
- [ ] 知道禁止主动重构、禁止瞎猜、禁止编造

**确认完毕后回复用户：**

> 已理解项目结构，可以开始开发。

---

## 联系与反馈

- 仓库：[github.com/laobi465/skills--1](https://github.com/laobi465/skills--1)
- License：MIT
