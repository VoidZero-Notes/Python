---
name: auto-commit
description: >-
  分析当前仓库改动并按 Conventional Commits 规范生成中文说明后提交。
  在用户明确说「提交」「commit」「自动提交」「帮我提交」时使用；
  未明确要求时禁止自动 commit。
---

# Auto Commit（笔记仓库）

仅在用户**明确要求提交**时执行。未要求则不要 commit。

## 流程

并行收集信息：

```bash
git status
git diff
git diff --staged
git log -5 --oneline
```

然后：

1. 若无改动（无 untracked、无 staged/unstaged 修改）→ 告知用户，结束，不空提交
2. 若当前目录不是 git 仓库 → 告知用户，结束
3. 根据改动起草 commit message（见下方格式）
4. 暂存相关文件并提交
5. 再跑一次 `git status` 确认成功
6. 向用户回报：完整 commit message + 简短结果

## Commit message 格式

使用 Conventional Commits，**type/scope 用英文，描述用中文**：

```text
<type>(<scope>): <中文简述>

<可选正文：1～2 句说明 why，中文>
```

- 第一行 ≤ 72 字符；用祈使语气概括「为什么改」
- `scope` 可选；笔记类可用目录或主题简写（如 `lambda`、`scope`、`core`）
- 有正文时，标题与正文之间空一行

### type 选用

| type | 何时用 |
|------|--------|
| `docs` | 笔记、说明、示例、对照表（本仓库默认） |
| `fix` | 纠正错误内容、错误示例、笔误导致的事实错误 |
| `refactor` | 结构调整、体例统一，不改变实质内容 |
| `chore` | 配置、脚本、`.cursor` 等非笔记内容 |
| `feat` | 新增一整篇笔记或新主题章节 |

### 示例

```text
docs(lambda): 补充闭包与默认参数的 JavaScript 类比
```

```text
docs(core): 统一函数章节体例并补齐对照表

对齐已优化笔记写法，便于前后对照阅读。
```

```text
chore(cursor): 新增笔记优化与自动提交相关配置
```

## 执行约束

- **禁止**修改 git config
- **禁止** `push`（除非用户另行明确要求）
- **禁止** `--amend`、`--no-verify`、force、interactive rebase 等危险操作
- **禁止**提交疑似密钥文件（`.env`、`credentials.json` 等）；若用户点名要提交，先警告
- 用 HEREDOC 传 message，避免转义问题：

```bash
git add <相关文件>
git commit -m "$(cat <<'EOF'
<type>(<scope>): <中文简述>

EOF
)"
git status
```

- 只 `git add` 与本次改动相关的文件；不要把无关脏文件一并塞进本次提交
- pre-commit 失败时：修复后**新建** commit，不要 amend
- 提交成功后回复用户：用了哪条 message、提交了哪些文件（可简写）
