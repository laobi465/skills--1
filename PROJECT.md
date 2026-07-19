# 项目文档（PROJECT）

> web-project-flow —— 网站项目开发全生命周期 Skill
> 当前版本：0.2.0 ｜ 最后更新：2026-07-19

---

## 1. 项目概述

### 1.1 目标

提供一套覆盖**网站项目开发全生命周期**的 TRAE Skill，把零散的提示词工程经验固化为可复用、可路由、可索引的标准能力模块。

### 1.2 背景

日常网站项目开发中，AI 经常出现以下问题：

- 硬编码密钥 / 配置参数 / 域名
- 编造不存在的 API、表名、字段
- 输出风格不稳定（一会儿极简一会儿炫技）
- 没有统一的交接文档格式
- 检查代码时维度不全（只看安全不看性能）

本 Skill 把这些问题对应的提示词收集起来，按阶段归类，通过 `SKILL.md` 路由表 + `/b` 快捷命令 + `/bhelp` 索引 三种方式调用。

### 1.3 适用范围

- 个人开发者从 0 到 1 起步网站项目
- 团队希望统一 AI 编码规范（铁律约束）
- 需要对现有项目做全方位审计
- 维护项目全生命周期文档
- 配置 GitHub 自动化部署

---

## 2. 架构总览

### 2.1 整体架构

```
web-project-flow/
├── SKILL.md          ← 主入口（路由 + 命令 + 铁律）
└── references/       ← 11 份提示词原文
    ├── 01 ~ 11       ← 按阶段编号
```

### 2.2 核心模块

| 模块 | 作用 | 关键文件 |
|---|---|---|
| 路由系统 | 根据用户意图匹配对应提示词 | [SKILL.md](./web-project-flow/SKILL.md) §2 路由表 |
| 命令系统 | `/b` 快捷命令 + `/bhelp` 索引 | [SKILL.md](./web-project-flow/SKILL.md) §3 |
| 铁律系统 | 三份硬约束文档，代码生成强制加载 | [references/04](./web-project-flow/references/04-no-hardcode-fake-data.md) + [05](./web-project-flow/references/05-config-to-backend.md) + [06](./web-project-flow/references/06-anti-hallucination.md) |
| 提示词库 | 11 份原文，按阶段分类 | [references/](./web-project-flow/references/) |
| 文档体系 | 四份核心文档联动维护 | [CHANGELOG.md](./CHANGELOG.md) + [PROJECT.md](./PROJECT.md) + [SPEC.md](./SPEC.md) + [TODO.md](./TODO.md) |

### 2.3 数据流

```
用户输入
  ↓
SKILL.md description 字段路由匹配
  ↓
┌─ 命令形式 (/bXXX)        → 直接 Read 对应 reference 并执行
├─ 自然语言 (我要做网站)    → 按路由表匹配并加载
└─ 索引形式 (/bhelp)       → 输出索引，不执行
  ↓
判断是否涉及代码生成
  ├─ 是 → 自动连带加载铁律三件套 04 + 05 + 06
  └─ 否 → 跳过铁律
  ↓
按提示词内指引开始执行
  ↓
若涉及需求变更 → 按 references/09 联动更新四份文档
```

---

## 3. 功能清单

### 3.1 已实现功能（v0.2.0）

#### 起步阶段
- ✅ 项目起步模板（完整版 + 精简版）
- ✅ 模糊想法落地 10 步流程（需求梳理 → 竞品 → 技术栈 → 模块 → 原型 → DB → UI → 工期 → 风险 → 需求说明书）

#### 设计阶段
- ✅ 现代简约 UI 设计规则（色彩 / 组件 / 排版 / 动效 / 禁用项）

#### 开发阶段（铁律）
- ✅ 禁硬编码假数据铁律（6 条规则）
- ✅ 配置后台化铁律（sys_config 表设计 + 缓存 + 后台可视化）
- ✅ 防 AI 幻觉铁律（基于事实 + 待核实 + 可信度）

#### AI 接入
- ✅ 新 AI 接手项目引导（README → PROMPT → 目录 → 路由表）

#### 检查阶段
- ✅ 项目全方位深度检查（安全 / 质量 / 性能 / 架构 / 运维 5 维度 + 分级标注 + 评分）

#### 文档维护
- ✅ 四份核心文档联动更新规范（CHANGELOG / PROJECT / SPEC / TODO）

#### 交接阶段
- ✅ 项目交接文档生成（README + PROMPT + 文件顶部注释）

#### 部署阶段
- ✅ GitHub 自动更新管理系统（Webhook + 自动重启 + 管理员弹窗 + 后台面板）

#### 调用方式
- ✅ 自然语言触发（按路由表自动匹配）
- ✅ `/b` 快捷命令（11 个单提示词命令）
- ✅ `/bhelp` 索引命令（默认索引 + 按编号查询 + 按关键词搜索）
- ✅ 链式调用（多命令空格分隔）
- ✅ 铁律自动叠加机制

---

## 4. 使用指南

### 4.1 安装

参考 [README.md 安装与注册章节](./README.md#安装与注册)。

### 4.2 三种调用方式

#### 方式一：自然语言触发

```
"我要做一个博客网站"        → 自动加载 01
"设计一下 UI 风格"          → 自动加载 03
"帮我检查项目安全"          → 自动加载 08
```

#### 方式二：`/b` 快捷命令

```
/bstart                    → 加载 01 项目起步
/bhardcode /bconfig /bhaluc → 三铁律一次性加载
/baudit                    → 加载 08 项目检查
```

#### 方式三：`/bhelp` 索引

```
/bhelp                     → 显示全部索引
/bhelp 05                  → 查看 05 号完整内容
/bhelp 硬编码               → 关键词搜索
```

### 4.3 全流程示例

```
1. /bstart                 → 起步对齐需求
2. /bui                     → 设计 UI 风格
3. /bhardcode /bconfig /bhaluc → 加载三铁律
4. （开始写代码）
5. /bdocs                   → 同步更新四份文档
6. /baudit                  → 项目检查
7. /bhandover               → 生成交接文档
8. /bdeploy                 → 配置 GitHub 自动部署
```

### 4.4 铁律强制加载时机

涉及代码生成的会话，以下三份铁律会**自动加载**到上下文：

1. [04 禁硬编码假数据](./web-project-flow/references/04-no-hardcode-fake-data.md)
2. [05 配置后台化](./web-project-flow/references/05-config-to-backend.md)
3. [06 防 AI 幻觉](./web-project-flow/references/06-anti-hallucination.md)

违反即重写。

---

## 5. 目录结构

```
skills--1/                                   ← 仓库根
├── README.md                                ← 项目介绍（给人类看）
├── PROMPT.md                                ← AI 对接引导（给 AI 看）
├── CHANGELOG.md                             ← 更新日志
├── PROJECT.md                               ← 本文件（项目文档）
├── SPEC.md                                  ← 规范文档
├── TODO.md                                  ← 待办清单
└── web-project-flow/                        ← Skill 本体
    ├── SKILL.md                             ← Skill 主入口
    └── references/                          ← 提示词库
        ├── 01-project-start.md
        ├── 02-fuzzy-idea-to-plan.md
        ├── 03-ui-design-rules.md
        ├── 04-no-hardcode-fake-data.md
        ├── 05-config-to-backend.md
        ├── 06-anti-hallucination.md
        ├── 07-ai-onboarding.md
        ├── 08-project-audit.md
        ├── 09-docs-lifecycle.md
        ├── 10-handover-docs.md
        └── 11-github-auto-update.md
```

---

## 6. 贡献指南

### 6.1 提交规范

按 [SPEC.md 提交规范章节](./SPEC.md#3-提交规范)：

```
<type>(<scope>): <subject>

<body>
```

### 6.2 版本号递增

按 [references/09](./web-project-flow/references/09-docs-lifecycle.md) 第 2 节：

- 重大功能 / 破坏性变更 → `X.0.0`
- 新增功能 / 向下兼容 → `0.X.0`
- 修复 / 小优化 → `0.0.X`

### 6.3 文档联动

任何变更必须按 [references/09](./web-project-flow/references/09-docs-lifecycle.md) 第 1 节联动更新：

| 变更类型 | 需更新的文档 |
|---|---|
| 功能新增 | CHANGELOG + PROJECT + TODO |
| 规则调整 | CHANGELOG + SPEC |
| 任务推进 | TODO + CHANGELOG |
| 架构变动 | 四份文档全部联动 |
