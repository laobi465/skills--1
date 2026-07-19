# Web Project Flow

> 网站项目开发全生命周期 Skill —— 从模糊想法到上线交付的一站式提示词工程方案

[![Skill](https://img.shields.io/badge/Skill-web--project--flow-blue)](./web-project-flow/SKILL.md)
[![Constraints](https://img.shields.io/badge/Constraints-HARD-red)](./web-project-flow/references/04-no-hardcode-fake-data.md)
[![Stages](https://img.shields.io/badge/Stages-11-green)](./web-project-flow/references/)
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](#license)

---

## 简介

`web-project-flow` 是一套覆盖**网站项目开发全生命周期**的 Skill，内置 11 份提示词，按阶段分三类：

- **流程类（7 份）**：起步 → 设计 → 接入 → 检查 → 文档 → 交接 → 部署
- **铁律类（3 份，硬约束）**：禁硬编码假数据 / 配置后台化 / 防幻觉
- **辅助类（1 份）**：模糊想法落地完整方案

支持三种调用方式：**自然语言触发** + **`/b` 快捷命令** + **`/bhelp` 索引**。

---

## 目录结构

```
web-project-flow/
├── SKILL.md                              # 主入口：YAML frontmatter + 路由表 + /bhelp 命令 + 铁律
└── references/
    ├── 01-project-start.md               # 项目起步提示词（完整版 + 精简版）
    ├── 02-fuzzy-idea-to-plan.md          # 模糊想法落地 10 步流程
    ├── 03-ui-design-rules.md            # 现代简约 UI 设计规则
    ├── 04-no-hardcode-fake-data.md      # 铁律①：禁硬编码假数据
    ├── 05-config-to-backend.md          # 铁律②：配置后台化（sys_config 表）
    ├── 06-anti-hallucination.md         # 铁律③：防 AI 幻觉
    ├── 07-ai-onboarding.md              # AI 对接新项目引导
    ├── 08-project-audit.md              # 项目全方位深度检查（5 维度）
    ├── 09-docs-lifecycle.md            # 四份核心文档维护规范
    ├── 10-handover-docs.md              # 项目交接文档生成
    └── 11-github-auto-update.md         # GitHub 自动更新管理系统
```

---

## 11 份提示词一览

| # | 名称 | 阶段 | 触发场景 |
|---|---|---|---|
| 01 | [项目起步提示词](./web-project-flow/references/01-project-start.md) | 起步 | "我要做一个网站" + 网站类型 + 功能清单 |
| 02 | [模糊想法落地 10 步流程](./web-project-flow/references/02-fuzzy-idea-to-plan.md) | 起步 | "我有个想法 / 帮我落地" |
| 03 | [现代简约 UI 设计规则](./web-project-flow/references/03-ui-design-rules.md) | 设计 | "设计 UI / 配色 / 页面风格" |
| 04 | [禁硬编码假数据](./web-project-flow/references/04-no-hardcode-fake-data.md) | 铁律 HARD | 写业务代码前 / 检查硬编码 |
| 05 | [配置后台化 sys_config](./web-project-flow/references/05-config-to-backend.md) | 铁律 HARD | 新增配置项 / 系统配置后台化 |
| 06 | [防 AI 幻觉](./web-project-flow/references/06-anti-hallucination.md) | 铁律 HARD | 防止幻觉 / 待核实 |
| 07 | [AI 对接新项目引导](./web-project-flow/references/07-ai-onboarding.md) | 接入 | "让 AI 接手 / 读懂项目" |
| 08 | [项目全方位深度检查](./web-project-flow/references/08-project-audit.md) | 检查 | "项目检查 / 审计 / 安全扫描" |
| 09 | [四份核心文档维护规范](./web-project-flow/references/09-docs-lifecycle.md) | 文档 | 变更 / 加功能 → 同步文档 |
| 10 | [项目交接文档生成](./web-project-flow/references/10-handover-docs.md) | 交接 | "项目完成 / 生成 README / PROMPT" |
| 11 | [GitHub 自动更新管理系统](./web-project-flow/references/11-github-auto-update.md) | 部署 | "GitHub 自动更新 / Webhook" |

---

## 使用方式

### 方式一：自然语言触发（推荐）

直接说出对应阶段的意图即可，AI 会自动加载对应提示词：

- 「我要做一个博客网站」 → 自动加载 `01`
- 「我有个想法，能不能帮我落地」 → 自动加载 `02`
- 「设计一下 UI 风格」 → 自动加载 `03`
- 「帮我检查项目安全」 → 自动加载 `08`
- 「项目做完了，生成交接文档」 → 自动加载 `10`

### 方式二：`/b` 快捷命令

每个提示词对应一个独立 slash 命令，直接加载完整内容并执行：

| 命令 | 作用 |
|---|---|
| `/bstart` | 加载 01 项目起步提示词 |
| `/bfuzzy` | 加载 02 模糊想法落地 10 步 |
| `/bui` | 加载 03 UI 设计规则 |
| `/bhardcode` | 加载 04 铁律①禁硬编码 |
| `/bconfig` | 加载 05 铁律②配置后台化 |
| `/bhaluc` | 加载 06 铁律③防幻觉 |
| `/bonboard` | 加载 07 AI 对接引导 |
| `/baudit` | 加载 08 项目全方位检查 |
| `/bdocs` | 加载 09 文档维护规范 |
| `/bhandover` | 加载 10 交接文档生成 |
| `/bdeploy` | 加载 11 GitHub 自动更新 |

### 方式三：`/bhelp` 命令索引

输入 `/bhelp` 查看所有提示词清单，支持三种参数：

```
/bhelp              # 显示全部索引
/bhelp 05           # 显示编号 05 的完整内容
/bhelp 硬编码        # 按关键词搜索匹配的提示词
/bhelp all          # 同 /bhelp
```

### 命令组合与链式调用

```
/bstart /bui              # 起步 + UI 设计一次性加载
/bhardcode /bconfig /bhaluc   # 三铁律一次性加载
```

未识别的 `/bXXX` 命令 → 回复「未识别的命令，输入 `/bhelp` 查看所有可用命令」

---

## 核心铁律（HARD）

凡涉及代码生成的会话，以下三份铁律会**强制加载**到上下文，违反即重写：

1. **禁硬编码假数据** ([04](./web-project-flow/references/04-no-hardcode-fake-data.md))
   - 禁硬编码密钥、token、域名、IP、配置参数
   - 禁编造不存在的接口地址、表名、字段、JSON 结构
   - 测试数据必须标注 `// 仅本地测试模拟`，上线必须移除

2. **配置后台化** ([05](./web-project-flow/references/05-config-to-backend.md))
   - 所有可调参数走 `sys_config` 表（含 6 个字段）
   - 业务代码通过 `config('key', 'default')` 读取
   - 缓存机制 + 后台可视化编辑 + 恢复默认值

3. **防 AI 幻觉** ([06](./web-project-flow/references/06-anti-hallucination.md))
   - 不确定说"不知道"，不编造
   - 存疑标注「待核实」
   - 回答末尾说明可信度

---

## UI 设计约束

[03-ui-design-rules.md](./web-project-flow/references/03-ui-design-rules.md) 严格禁用：

- 禁 emoji / 表情符号 / 图标化装饰
- 禁毛玻璃效果（backdrop-filter）
- 禁暗黑风格（黑色 / 深灰 / 深紫主色）
- 禁夸张设计（大渐变 / 炫光 / 霓虹 / 3D 凸起）
- 禁过度装饰（多余线条 / 纹理 / 图案）

---

## 全流程示例

```
用户：我要做一个电商商城网站
  ↓ AI 加载 01-project-start.md（按完整版模板对齐需求）

用户：UI 风格帮我设计一下
  ↓ AI 加载 03-ui-design-rules.md（按现代简约规则）

用户：开始写代码吧
  ↓ AI 强制加载铁律三件套 04 + 05 + 06，然后写代码

用户：加一个新功能：会员等级
  ↓ AI 加载 09-docs-lifecycle.md，联动更新 CHANGELOG + PROJECT + SPEC + TODO

用户：检查一下整个项目
  ↓ AI 加载 08-project-audit.md，5 维度扫描输出分级报告

用户：项目做完了，生成交接文档
  ↓ AI 加载 10-handover-docs.md，输出 README + PROMPT + 文件注释

用户：配置 GitHub 自动部署
  ↓ AI 加载 11-github-auto-update.md，输出 Webhook 接收端 + 后台面板 + 弹窗
```

---

## 安装与注册

将 `web-project-flow/` 目录复制到 TRAE 的 Skill 加载路径下即可被自动识别：

```bash
# 假设 TRAE Skill 路径为 ~/.trae/skills/
cp -r web-project-flow/ ~/.trae/skills/web-project-flow/
```

注册后通过自然语言或 `/bhelp` 命令触发。

---

## 适用场景

- 个人开发者从 0 到 1 起步网站项目
- 团队希望统一 AI 编码规范（铁律约束）
- 需要对现有项目做全方位审计
- 配置 GitHub 自动化部署

---

## 项目导航

| 文档 | 给谁看 | 用途 |
|---|---|---|
| [README.md](./README.md) | 人类 | 项目介绍、目录结构、使用方式 |
| [PROMPT.md](./PROMPT.md) | AI | AI 对接引导、铁律、路由表、命令规范 |
| [web-project-flow/SKILL.md](./web-project-flow/SKILL.md) | AI | Skill 主入口（含 description、路由、命令清单） |
| [web-project-flow/references/](./web-project-flow/references/) | AI | 11 份提示词原文 |

---

## License

MIT
