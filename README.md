# Python 技术笔记

面向有 JavaScript / TypeScript / Node.js 基础的 Python 学习笔记。仓库配置了两个 Cursor 工作流：**笔记体例优化（Command）** 与 **自动提交推送（Skill）**。

请在 Cursor 中打开本仓库**根目录**（含 `.cursor/` 的那一层）。只打开子目录时，Command / Skill 可能不会出现。

## 目录结构

```text
Python/
├── README.md
├── Python语言核心/          # 语言与运行时笔记
├── Python框架/              # 框架与工程实践
├── .cursor/
│   ├── commands/
│   │   └── optimize-py-js-note.md   # 笔记类比体例优化
│   └── skills/
│       └── auto-commit/             # 自动提交并推送
└── .gitignore
```

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

### Python框架

| 编号 | 主题 |
|------|------|
| 01 | Web 服务框架 |
| 02 | 优化包结构 |

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
