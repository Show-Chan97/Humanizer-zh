# Humanizer-zh

去除中文文本中的 AI 生成痕迹，使文字听起来更自然、更像人类书写。

## 核心功能

- 检测并修复 **29 种 AI 写作模式**，涵盖 5 个类别：内容模式、语言语法模式、风格模式、交流模式、填充词与回避
- **声音校准**：可提供个人写作风格样本，技能会匹配你的文风
- **Anti-AI 自审**：内置自问自答再修订的审查步骤
- 基于 Wikipedia "Signs of AI writing" 指南 v2.5.1（由 WikiProject AI Cleanup 维护）

## 常见 AI 词汇（部分）

`此外`、`至关重要`、`深入探讨`、`强调`、`持久的`、`增强`、`突出`、`格局`、`展示`、`证明`、`宝贵的`、`充渴活力的`……

## 适用场景

当你提到以下关键词时触发：
- "去 AI 味"
- "人性化"
- "更像人话"
- "听起来不像 AI"

## 安装方式

### 方式一：Claude Code Skills（推荐）

将仓库克隆到 `~/.claude/skills/`：

```bash
git clone https://github.com/Show-Chan97/Humanizer-zh ~/.claude/skills/Humanizer-zh
```

### 方式二：git clone

```bash
git clone https://github.com/Show-Chan97/Humanizer-zh
```

### 方式三：手动下载

下载本仓库，参考上方方式添加到你的工具目录。

## 核心原则

- **文本要"活"**，不只是"干净"
- 适当时候使用第一人称视角
- 变化句子节奏和长度
- 承认复杂性，不过度概括
- 允许一些"混乱"——跑题、题外话是人性的体现

## 工作原理

1. 识别 29 种 AI 写作模式
2. 用自然替代方案重写
3. 保留原文核心含义
4. 维持预期语气（正式/随意/技术等）
5. 注入真实个性
6. Anti-AI 自审（自问自答再修订）

## 参考

本技能基于 [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)（v2.5.1），由 WikiProject AI Cleanup 维护。

> "LLM 使用统计算法来猜测接下来应该是什么。结果倾向于适用于最广泛情况的统计上最可能的结果。"
