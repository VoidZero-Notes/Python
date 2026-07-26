# Python 技术笔记

面向有 JavaScript 基础的 Python 学习笔记。仓库内配置了两个 Cursor 工作流：**笔记体例优化（Command）** 与 **自动提交推送（Skill）**。

工作区请打开本目录根：

```text
/Users/sheng/Documents/技术笔记/Python
```

只打开子目录（如 `Python语言核心`）时，`.cursor/` 下的 Command / Skill 可能不会出现。

## 目录结构

```text
Python/
├── README.md
├── Python语言核心/          # 笔记正文
├── .cursor/
│   ├── commands/
│   │   └── optimize-py-js-note.md   # 笔记 JS 类比优化命令
│   └── skills/
│       └── auto-commit/             # 自动提交并推送 Skill
└── .gitignore
```

---

## 1. 笔记 JS 类比优化（Command）

| 项 | 说明 |
|----|------|
| 类型 | Cursor **Command**（不是 Skill / Rule） |
| 文件 | `.cursor/commands/optimize-py-js-note.md` |
| 聊天触发 | `/optimize-py-js-note` |

### 做什么

把指定笔记改成与已优化样本一致的「Python + JavaScript 类比」体例，并统一代码格式：

- 文首补 `| Python | JavaScript 对应 |` 对照表
- 主要 Python 示例后补 `JavaScript 类比` + `js` 代码块
- **代码缩进统一为 2 空格**，去掉 Tab，不混用 4 空格
- 去掉多余的 `---` 章节分隔线
- 作业保持 Python，不为作业补 JS

体例锚点（优先对照这些已优化笔记）：

- `Python语言核心/2. 基本语法.md`
- `Python语言核心/3. 容器类型.md`
- `Python语言核心/4. 函数.md`
- `Python语言核心/5. 作用域.md`

### 怎么用

1. 打开 Agent / Chat
2. 输入 `/`，选择 `optimize-py-js-note`
3. `@` 要优化的笔记后回车，例如：

```text
/optimize-py-js-note @Python语言核心/6. Lambda表达式.md
```

可一次多个：

```text
/optimize-py-js-note @Python语言核心/6. a.md @Python语言核心/7. b.md
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
