# Python 笔记「JS 类比优化」用法

本目录用 **Cursor Command**（不是 Skill / Rule）做这件事：一键把笔记补成「Python + JavaScript 类比」体例，并统一 2 空格缩进。

命令文件位置：

```text
.cursor/commands/optimize-py-js-note.md
```

聊天里对应命令名：`/optimize-py-js-note`

## 使用前：工作区要开对

Cursor 只会扫描**当前工作区根目录**下的 `.cursor/commands/`。

请用 Cursor 打开：

```text
/Users/sheng/Documents/技术笔记/Python
```

不要只打开子目录 `Python语言核心`，否则列表里看不到该命令。

## 下次怎么用

1. 打开 Agent / Chat
2. 输入 `/`，选择 `optimize-py-js-note`
3. 再 `@` 要优化的笔记，例如：

```text
/optimize-py-js-note @Python语言核心/6. xxx.md
```

也可以一次多个：

```text
/optimize-py-js-note @Python语言核心/6. a.md @Python语言核心/7. b.md
```

4. 回车，等 Agent 直接改文件

## 它会做什么

相对已优化样本（`2/3/4/5`）：

- 补文首 `Python | JavaScript 对应` 表
- 主要示例后补 `JavaScript 类比` + ` ```js `
- 代码缩进统一 2 空格，去掉 Tab
- 去掉多余的 `---` 分隔
- 作业保持 Python，不补 JS

## 改命令本身

要调整规范，直接编辑：

```text
/Users/sheng/Documents/技术笔记/Python/.cursor/commands/optimize-py-js-note.md
```

保存后下次 `/optimize-py-js-note` 即生效，无需额外安装。
