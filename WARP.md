# WARP.md

为 WARP (warp.dev) 提供仓库上下文。

## 这个仓库是什么

这是一个 **Claude Code / OpenCode 技能**，纯 Markdown 实现，用于去除文本中的 AI 生成痕迹。

"运行时"文件是 `SKILL.md`：Claude Code 读取 YAML frontmatter（元数据 + 允许的工具）和后面的提示词/指令。

`README.md` 是面向人类的文档：安装、使用方法和模式概览。

## 关键文件

- `SKILL.md`
  - 技能定义文件（核心）。
  - 以 YAML frontmatter (`---` … `---`) 开头，包含 `name`、`version`、`description` 和 `allowed-tools`。
  - Frontmatter 之后是编辑器提示词：完整的模式列表和示例。
- `README.md`
  - 安装和使用说明。
  - 包含 29 种模式的分类列表和版本历史。

修改行为/内容时，以 `SKILL.md` 为准，同步更新 `README.md` 保持一致。

## 常用命令

### 安装技能到 Claude Code

推荐方式（通过 npx 一键安装）：

```bash
npx skills add https://github.com/Show-Chan97/Humanizer-zh.git
```

备选方式（如果 npx 不可用，通过 Git 克隆）：

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Show-Chan97/Humanizer-zh.git ~/.claude/skills/Humanizer-zh
```

手动安装/更新（仅复制技能文件）：

```bash
mkdir -p ~/.claude/skills/Humanizer-zh
cp SKILL.md ~/.claude/skills/Humanizer-zh/
```

## 如何使用（Claude Code）

调用技能：

```
/Humanizer-zh [粘贴你的文本]
```

## 安全修改指南

### 版本号（保持同步）

- `SKILL.md` 的 YAML frontmatter 中有 `version:` 字段。
- `README.md` 有"版本历史"部分。

如果更新版本号，两处都要同步修改。

### 编辑 `SKILL.md`

- 保持有效的 YAML frontmatter 格式和缩进。
- 保持模式编号一致（README 的列表引用相同的编号）。

### 记录非显而易见的修复

如果修改提示词以处理某个棘手的失败情况（如反复出错或意外的语气变化），在 `README.md` 的版本历史中添加简短说明，描述修复了什么以及原因。

## 与上游的关系

本项目基于 [blader/humanizer](https://github.com/blader/humanizer)（英文版 v2.5.1）翻译，并合并了 [op7418/Humanizer-zh](https://github.com/op7418/Humanizer-zh) 的核心规则和检查清单。
