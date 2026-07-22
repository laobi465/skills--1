# Web Project Flow

> 网站项目开发全生命周期 Skill —— 从模糊想法到上线交付的一站式提示词工程方案

[![Skill](https://img.shields.io/badge/Skill-web--project--flow-blue)](./web-project-flow/SKILL.md)
[![Constraints](https://img.shields.io/badge/Constraints-HARD-red)](./web-project-flow/references/04-no-hardcode-fake-data.md)
[![Stages](https://img.shields.io/badge/Stages-12-green)](./web-project-flow/references/)
[![License](https://img.shields.io/badge/License-MIT-lightgrey)](#license)

---

## 简介

`web-project-flow` 是一套覆盖**网站项目开发全生命周期**的 Skill，内置 12 份提示词，按阶段分三类：

- **流程类（8 份）**：起步 → 设计 → 接入 → 检查 → 文档 → 交接 → 部署 → 记忆
- **铁律类（3 份，硬约束）**：禁硬编码假数据 / 防幻觉 / 严格遵循项目文档规范
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
    ├── 06-anti-hallucination.md         # 铁律②：防 AI 幻觉
    ├── 07-ai-onboarding.md              # AI 对接新项目引导
    ├── 08-project-audit.md              # 项目全方位深度检查（5 维度）
    ├── 09-docs-lifecycle.md            # 两份核心文档维护规范
    ├── 10-handover-docs.md              # 项目交接文档生成
    ├── 11-github-auto-update.md         # GitHub 自动更新管理系统
    ├── 12-long-term-memory.md          # 长期编程记忆方案（L1/L2/L3 三层架构）
    └── 13-strict-doc-compliance.md     # 铁律③：严格遵循项目文档规范
```

---

## 12 份提示词一览

| # | 名称 | 阶段 | 触发场景 |
|---|---|---|---|
| 01 | [项目起步提示词](./web-project-flow/references/01-project-start.md) | 起步 | "我要做一个网站" + 网站类型 + 功能清单 |
| 02 | [模糊想法落地 10 步流程](./web-project-flow/references/02-fuzzy-idea-to-plan.md) | 起步 | "我有个想法 / 帮我落地" |
| 03 | [现代简约 UI 设计规则](./web-project-flow/references/03-ui-design-rules.md) | 设计 | "设计 UI / 配色 / 页面风格" |
| 04 | [禁硬编码假数据](./web-project-flow/references/04-no-hardcode-fake-data.md) | 铁律 HARD | 写业务代码前 / 检查硬编码 |
| 06 | [防 AI 幻觉](./web-project-flow/references/06-anti-hallucination.md) | 铁律 HARD | 防止幻觉 / 待核实 |
| 07 | [AI 对接新项目引导](./web-project-flow/references/07-ai-onboarding.md) | 接入 | "让 AI 接手 / 读懂项目" |
| 08 | [项目全方位深度检查](./web-project-flow/references/08-project-audit.md) | 检查 | "项目检查 / 审计 / 安全扫描" |
| 09 | [两份核心文档维护规范](./web-project-flow/references/09-docs-lifecycle.md) | 文档 | 变更 / 加功能 → 同步文档 |
| 10 | [项目交接文档生成](./web-project-flow/references/10-handover-docs.md) | 交接 | "项目完成 / 生成 README / PROMPT" |
| 11 | [GitHub 自动更新管理系统](./web-project-flow/references/11-github-auto-update.md) | 部署 | "GitHub 自动更新 / Webhook" |
| 12 | [长期编程记忆方案](./web-project-flow/references/12-long-term-memory.md) | 记忆 | "长期记忆 / 跨会话 / 用户偏好 / `/bmem`" |
| 13 | [严格遵循项目文档规范](./web-project-flow/references/13-strict-doc-compliance.md) | 铁律 HARD | "按项目文档开发 / 严格遵循规范 / 对标源码风格" |

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
| `/bhaluc` | 加载 06 铁律②防幻觉 |
| `/bonboard` | 加载 07 AI 对接引导 |
| `/baudit` | 加载 08 项目全方位检查 |
| `/bdocs` | 加载 09 文档维护规范 |
| `/bhandover` | 加载 10 交接文档生成 |
| `/bdeploy` | 加载 11 GitHub 自动更新 |
| `/bmem` | 加载 12 长期编程记忆（show/add/clean/audit/export） |
| `/bstrict` | 加载 13 铁律③严格遵循项目文档规范 |

### 方式三：`/bhelp` 命令索引

输入 `/bhelp` 查看所有提示词清单，支持三种参数：

```
/bhelp              # 显示全部索引
/bhelp 06           # 显示编号 06 的完整内容
/bhelp 硬编码        # 按关键词搜索匹配的提示词
/bhelp all          # 同 /bhelp
```

### 命令组合与链式调用

```
/bstart /bui              # 起步 + UI 设计一次性加载
/bhardcode /bhaluc /bstrict   # 三铁律一次性加载
/bstart                   # 起步命令后自动连带加载除 /bonboard 外所有指令（详见 SKILL.md §3.8.2）
```

未识别的 `/bXXX` 命令 → 回复「未识别的命令，输入 `/bhelp` 查看所有可用命令」

---

## 核心铁律（HARD）

### 自动加载机制

- **每次对话开始**：自动加载铁律三件套 `04 + 06 + 13` + `08`（审计）+ `09`（文档维护），无需用户提示
- **`/bstart` / `/bfuzzy` 后**：除 `/bonboard`（07）外，自动连带加载所有其他指令（03/04/06/08/09/10/11/12/13）
- **涉及代码生成的命令**（`/bstart`、`/bui`、`/bdeploy` 等）：自动连带加载铁律三件套 `04 + 06 + 13`

### 三份铁律

凡涉及代码生成的会话，以下三份铁律会**强制加载**到上下文，违反即重写：

1. **禁硬编码假数据 / 禁占位符** ([04](./web-project-flow/references/04-no-hardcode-fake-data.md))
   - 禁硬编码密钥、token、域名、IP、配置参数
   - 禁编造不存在的接口地址、表名、字段、JSON 结构
   - 禁占位符（`// TODO`、`pass`、`...`、`Lorem Ipsum`、`your_api_key_here` 等）
   - 缺资料时必须显式失败（`throw new Error('待接入：XXX')`），不得用占位符糊弄
   - 测试数据必须标注 `// 仅本地测试模拟`，上线必须移除

2. **防 AI 幻觉** ([06](./web-project-flow/references/06-anti-hallucination.md))
   - 不确定说"不知道"，不编造
   - 存疑标注「待核实」
   - 回答末尾说明可信度

3. **严格遵循项目文档规范** ([13](./web-project-flow/references/13-strict-doc-compliance.md))
   - 写代码前必须读完 README / 接口文档 / 数据库结构 / 编码规范
   - 命名、分层、注释、异常格式、响应体完全对标现有源码
   - 错误码沿用项目已定义的枚举，禁止自创数字状态码
   - 新增功能兼容旧逻辑，改动旧逻辑前必须告知风险
   - 完成后主动自检合规校验清单
   - 操作流程：**读文档 → 提问补缺 → 再写代码**

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
  ↓ AI 强制加载铁律三件套 04 + 06 + 13，并按 13 号"读文档→提问→写代码"流程执行

用户：加一个新功能：会员等级
  ↓ AI 加载 09-docs-lifecycle.md，提醒用户按规范同步项目文档

用户：检查一下整个项目
  ↓ AI 加载 08-project-audit.md，5 维度扫描输出分级报告

用户：项目做完了，生成交接文档
  ↓ AI 加载 10-handover-docs.md，输出 README + PROMPT + 文件注释

用户：配置 GitHub 自动部署
  ↓ AI 加载 11-github-auto-update.md，输出 Webhook 接收端 + 后台面板 + 弹窗

用户：把这次的项目经验和我的偏好记下来，方便下次接手
  ↓ AI 加载 12-long-term-memory.md，写入 L3 全局记忆 + L2 项目记忆
```

---

## 长期记忆方案（L1/L2/L3 三层架构）

[12-long-term-memory.md](./web-project-flow/references/12-long-term-memory.md) 实现跨会话/跨项目/全局的长期编程记忆：

| 层级 | 范围 | 载体 | 失效 |
|---|---|---|---|
| **L1 即时** | 当前会话 | 对话历史 | 会话结束 |
| **L2 项目** | 当前项目 | README / PROMPT / 文件注释 / `.trae/skills/` | 项目删除 |
| **L3 全局** | 跨项目 | `~/.trae/skills/` / `~/.trae/rules/` / `~/.trae/config` | 永久 |

**核心机制**：

- **写入时机**：6 类触发事件（偏好 / 纠正 / 里程碑 / 铁律 / 代码 / 风格）
- **读取顺序**：L3 全局 → L2 项目 → L1 即时
- **冲突优先级**：用户最新指令 > L3 > L2 > L1
- **失效策略**：半年未触发归档 / 项目删除清理 / 规则覆盖保留 1 版本

**配套命令**（`/bmem` 前缀）：

| 命令 | 作用 |
|---|---|
| `/bmem show` | 显示当前所有记忆（L2 + L3） |
| `/bmem show global` | 仅显示全局记忆（L3） |
| `/bmem show project` | 仅显示项目记忆（L2） |
| `/bmem add <内容>` | 手动添加记忆（默认全局） |
| `/bmem add project <内容>` | 添加项目级记忆 |
| `/bmem clean` | 清理过期记忆（半年未触发） |
| `/bmem audit` | 审计记忆质量，输出报告 |
| `/bmem export` | 导出全部记忆为单个 md 文件 |

---

## 安装与注册

将 `web-project-flow/` 目录复制到 TRAE 的 Skill 加载路径下即可被自动识别：

```bash
# 假设 TRAE Skill 路径为 ~/.trae/skills/
cp -r web-project-flow/ ~/.trae/skills/web-project-flow/
```

注册后通过自然语言或 `/bhelp` 命令触发。

### 一键安装提示词（喂给 AI / AI Agent）

把下面这段提示词**完整复制粘贴**给 TRAE / Claude / Cursor / Codex 等任意支持 Skill 的 AI，AI 会自动拉取仓库并完成注册：

````markdown
请帮我安装 web-project-flow Skill，按以下步骤执行：

1. 克隆仓库到临时目录：
   ```bash
   git clone https://github.com/laobi465/skills--1.git /tmp/skills--1
   ```

2. 将 Skill 目录复制到 TRAE Skill 加载路径（如目录不存在则创建）：
   ```bash
   mkdir -p ~/.trae/skills/
   cp -r /tmp/skills--1/web-project-flow/ ~/.trae/skills/web-project-flow/
   ```

3. 验证安装是否成功：
   ```bash
   ls -la ~/.trae/skills/web-project-flow/
   ```
   预期输出：`SKILL.md` + `references/` 目录（含 12 份 .md 提示词文件）。

4. 清理临时文件：
   ```bash
   rm -rf /tmp/skills--1
   ```

5. 安装完成后，向我确认：
   - 已成功加载 web-project-flow Skill（12 份提示词，3 份铁律 HARD）
   - 铁律三件套 04 + 06 + 13 已自动加载到本次会话上下文
   - 可用 `/bhelp` 查看索引，或直接说「我要做一个 XX 网站」触发起步流程

执行过程中如有任何步骤失败，立即停止并报告错误原因，不要继续后续步骤，不要自行编造修复方案。
````

> **说明**：该提示词可直接粘贴给 AI Agent 执行；执行成功后无需额外配置，AI 会自动识别 Skill 并按 [PROMPT.md](./PROMPT.md) 约定加载铁律三件套。

---

## 适用场景

- 个人开发者从 0 到 1 起步网站项目
- 团队希望统一 AI 编码规范（铁律约束）
- 需要对现有项目做全方位审计
- 配置 GitHub 自动化部署
- **跨会话保留 AI 上下文和用户偏好（长期记忆）**

---

## 项目导航

| 文档 | 给谁看 | 用途 |
|---|---|---|
| [README.md](./README.md) | 人类 | 项目介绍、目录结构、使用方式 |
| [PROMPT.md](./PROMPT.md) | AI | AI 对接引导、铁律、路由表、命令规范 |
| [web-project-flow/SKILL.md](./web-project-flow/SKILL.md) | AI | Skill 主入口（含 description、路由、命令清单） |
| [web-project-flow/references/](./web-project-flow/references/) | AI | 13 份提示词原文 |

---

## License

MIT
