# Python 技术笔记

面向有 JavaScript / TypeScript / Node.js 基础的 Python 学习笔记。仓库配置了两个 Cursor 工作流：**笔记体例优化（Command）** 与 **自动提交推送（Skill）**。

请在 Cursor 中打开本仓库**根目录**（含 `.cursor/` 的那一层）。只打开子目录时，Command / Skill 可能不会出现。

## 目录结构

```text
Python/
├── README.md
├── Python语言核心/          # 语言、运行时、工程工具
├── Python框架/              # Web 框架与包结构
├── 数据库/                  # PostgreSQL 为主
├── OAuth2/                  # 授权协议（Postman 先行）
├── RBAC/                    # 权限模型与落地设计
├── .cursor/
│   ├── commands/
│   │   └── optimize-py-js-note.md   # 笔记类比体例优化
│   └── skills/
│       └── auto-commit/             # 自动提交并推送
└── .gitignore
```

建议阅读顺序：`Python语言核心` → `Python框架` → `数据库` → `OAuth2` → `RBAC`。后两套偏协议与权限设计，不绑定单一语言实现。

### Python语言核心

| 编号 | 主题 |
|------|------|
| 01 | 环境搭建 |
| 02 | 基本语法 |
| 03 | 容器类型 |
| 04 | 函数 |
| 05 | 作用域 |
| 06 | Lambda 表达式 |
| 07 | 类和对象 |
| 08 | 对象模型 |
| 09 | 元类 |
| 10 | 抽象类 |
| 11 | 装饰器 |
| 12 | 魔术方法 |
| 13 | 描述符 |
| 14 | 异常处理 |
| 15 | 迭代器与生成器 |
| 16 | 上下文管理器 |
| 17 | 类型标注 |
| 18 | 模块与包管理 |
| 19 | 事件循环 |
| 20 | Future 类 |
| 21 | 协程 Coroutine |
| 22 | 异步编程 |
| 23 | 多线程和多进程 |
| 24 | 构建发布 |
| 25 | 项目管理工具 |
| 26 | Monorepo |
| 27 | 断点调试 |

### Python框架

| 编号 | 主题 |
|------|------|
| 01 | Web 服务框架 |
| 02 | 优化包结构 |

### 数据库

以 PostgreSQL 实操为主；开篇先建立数据库整体认知。

| 编号 | 主题 |
|------|------|
| 01 | 数据库概述 |
| 02 | 环境搭建 |
| 03 | DDL |
| 04 | 表间关系 |
| 05 | DML |
| 06 | 事务 |
| 07 | 索引 |
| 08 | 进阶能力 |

### OAuth2

协议优先：用 Postman 走通握手与令牌流转，再落到具体语言实现。

| 编号 | 主题 |
|------|------|
| 01 | OAuth2 是什么：问题与需求 |
| 02 | OAuth2 怎么工作：核心概念和角色 |
| 03 | OAuth2 的授权模式与选型 |
| 04 | 授权码模式：流程、参数与设计 |
| 05 | 授权码模式 + PKCE：移动端安全增强 |
| 06 | OIDC：在 OAuth2 上加一层身份认证 |
| 07 | 令牌的生命周期管理和最佳实践 |
| 08 | OAuth2 收官实战 |

### RBAC

从权限需求与模型演进，到核心模型、库表、API 与收官实战。

| 编号 | 主题 |
|------|------|
| 01 | 权限控制的需求和实现模型 |
| 02 | RBAC 核心模型：用户、角色和权限 |
| 03 | RBAC 数据库设计 |
| 04 | RBAC API 接口层设计 |
| 05 | RBAC 收官实战 |

---

## 1. 笔记类比体例优化（Command）

| 项 | 说明 |
|----|------|
| 类型 | Cursor **Command**（不是 Skill / Rule） |
| 文件 | `.cursor/commands/optimize-py-js-note.md` |
| 聊天触发 | `/optimize-py-js-note` |

### 做什么

把指定笔记改成与已优化样本一致的「Python + 前端/运行时侧类比」体例，并统一代码格式：

- 每个概念只选 **一种** 对照侧：`JavaScript` / `TypeScript` / `Node.js`（按语义匹配，不硬凑）
- 文首对照表列名形如 `| Python | JavaScript 对应 |`（一张表只对应一种语言）
- 主要 Python 示例后补对应侧类比代码块；无靠谱对应则写「无 xxx 对应」，不补误导代码
- **代码缩进统一为 2 空格**，去掉 Tab，不混用 4 空格
- 去掉多余的 `---` 章节分隔线；连续空行默认压成 1 个
- 作业保持 Python，不为作业补类比

体例锚点（优先对照这些已优化笔记）：

- `Python语言核心/02. 基本语法.md`
- `Python语言核心/03. 容器类型.md`
- `Python语言核心/04. 函数.md`
- `Python语言核心/05. 作用域.md`

> 该 Command 面向 `Python语言核心` / `Python框架` 等「Python ↔ 前端/运行时」类笔记。`OAuth2`、`RBAC`、`数据库` 等协议/SQL 系列一般不必套用。

### 怎么用

1. 打开 Agent / Chat
2. 输入 `/`，选择 `optimize-py-js-note`
3. `@` 要优化的笔记后回车，例如：

```text
/optimize-py-js-note @Python语言核心/06. Lambda表达式.md
```

可一次多个：

```text
/optimize-py-js-note @Python语言核心/06. a.md @Python语言核心/07. b.md
```

Agent 会**直接改文件**，不只输出 Diff。

### 改规范

编辑 `.cursor/commands/optimize-py-js-note.md`，保存后下次 `/optimize-py-js-note` 即生效。

---

## 2. 自动提交并推送（Skill）

| 项 | 说明 |
|----|------|
| 类型 | Cursor **Skill** |
| 文件 | `.cursor/skills/auto-commit/SKILL.md` |
| 触发话术 | `提交` / `commit` / `自动提交` / `帮我提交` |

### 做什么

用户明确要求提交时，Agent 会：

1. 查看 `git status` / `diff` / 近期 commit 风格
2. 按 **Conventional Commits** 起草中文说明并 `commit`
3. **默认 `git push` 到 `origin`**（首次分支用 `git push -u origin HEAD`）
4. 回报 commit message、涉及文件、push 结果

未明确要求提交时，**不会**自动 commit / push。

### Commit message 格式

```text
<type>(<scope>): <中文简述>

<可选正文：1～2 句说明 why，中文>
```

常用 `type`：

| type | 用途 |
|------|------|
| `docs` | 笔记、说明、示例（本仓库默认） |
| `fix` | 纠正错误内容或错误示例 |
| `refactor` | 结构调整、体例统一 |
| `chore` | `.cursor`、`.gitignore` 等配置 |
| `feat` | 新增一整篇笔记或新主题 |

### 推送规则

- 提交成功后**默认 push**，不必再单独说 push
- 说「只提交不推送 / 不要 push」时跳过 push
- 不 force push；不改 git config；不提交 `.env` 等密钥文件

### 改行为

编辑 `.cursor/skills/auto-commit/SKILL.md` 即可。
