# Humanizer-zh: AI 写作去痕工具（中文版）

> **声明：**
> - 本项目的核心文件基于 [blader/humanizer](https://github.com/blader/humanizer/tree/main) 翻译并升级至 v2.5.1
> - 实用工具部分（核心规则、快速检查清单）参考了 [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop)
> - 原项目基于维基百科的 [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) 指南

---

## 项目简介

Humanizer-zh 是一个用于去除文本中 AI 生成痕迹的工具，帮助你将 AI 生成的内容改写得更自然、更像人类书写的文本。

本项目适用于：
- 编辑和审阅 AI 生成的内容
- 提升文章的人性化程度
- 学习识别 AI 写作的常见模式

## 安装

### 方法一：通过 Git 克隆（推荐）

```bash
# Claude Code 用户
mkdir -p ~/.claude/skills
git clone https://github.com/Show-Chan97/Humanizer-zh.git ~/.claude/skills/Humanizer-zh

# OpenCode 用户
mkdir -p ~/.config/opencode/skills
git clone https://github.com/Show-Chan97/Humanizer-zh.git ~/.config/opencode/skills/Humanizer-zh
```

### 方法二：通过 npx 一键安装

```bash
npx skills add https://github.com/Show-Chan97/Humanizer-zh.git
```

注：此方法需要系统中已安装 Node.js 且能正常运行 npx。如果失败，请使用方法一。

### 方法二：通过 Git 克隆

```bash
# 克隆到 Claude Code 的 skills 目录
git clone https://github.com/Show-Chan97/Humanizer-zh.git ~/.claude/skills/Humanizer-zh
```

### 方法三：手动安装

1. 下载本项目的 ZIP 文件或克隆到本地
2. 将 `Humanizer-zh` 文件夹复制到 Claude Code 的 skills 目录：
   - **macOS/Linux**: `~/.claude/skills/`
   - **Windows**: `%USERPROFILE%\.claude\skills\`

### 文件结构

```
~/.claude/skills/Humanizer-zh/
├── SKILL.md       # 技能定义文件（核心，AI 读取此文件）
├── README.md      # 说明文档（面向人类）
└── WARP.md        # Warp 终端 AI 上下文
```

### 验证安装

重启 Claude Code 或重新加载 skills 后，在对话中输入：

```
/Humanizer-zh
```

如果安装成功，该技能将被激活。

## 使用

### 基础用法

在 Claude Code 中，你可以通过以下方式使用 Humanizer：

#### 1. 直接调用技能

```
/Humanizer-zh 请帮我人性化以下文本：

[粘贴你的 AI 生成文本]
```

#### 2. 在对话中使用

```
请用 humanizer 帮我改写这段话，让它更自然：

这个项目作为我们团队致力于创新的证明。此外，它展示了我们在不断演变的技术格局中的关键作用。
```

#### 3. 处理文件内容

```
/Humanizer-zh 请人性化 article.md 文件中的内容
```

#### 4. 提供写作风格样本（声音校准）

```
/Humanizer-zh 请人性化这段文字。我的写作风格参考：https://example.com/my-writing.md
```

## 检测的 AI 写作模式

本工具能够识别并修复 **29 种** AI 写作痕迹，分为五大类。

> **注：** 中文版按模式分类进行了分组显示，其编号顺序与英文原版 [blader/humanizer](https://github.com/blader/humanizer) 略有不同，但包含的 29 种模式完全一致。

### 📝 内容模式（7种）
1. 过度强调意义、遗产和更广泛的趋势
2. 过度强调知名度和媒体报道
3. 以 -ing 结尾的肤浅分析
4. 宣传和广告式语言
5. 模糊归因和含糊措辞
6. 提纲式的"挑战与未来展望"部分
7. **连字符词组过度使用**（新增）

### 🔤 语言和语法模式（6种）
8. 过度使用的"AI 词汇"
9. 避免使用"是"（系动词回避）
10. 否定式排比和尾部否定
11. 三段式法则过度使用
12. 刻意换词（同义词循环）
13. 虚假范围

### 🎨 风格模式（8种）
14. 破折号过度使用
15. 粗体过度使用
16. 内联标题垂直列表
17. 标题中的标题大写
18. 表情符号
19. 弯引号
20. **说服性权威措辞**（新增）
21. **预告性和声明性语句**（新增）

### 💬 交流模式和填充词（8种）
22. 协作交流痕迹
23. 知识截止日期免责声明
24. 谄媚/卑躬屈膝的语气
25. 填充短语
26. 过度限定
27. 通用积极结论
28. **被动语态和无主语片段**（新增）
29. **标题后的碎片化引导句**（新增）

## 核心功能

### 声音校准

Humanizer-zh 支持**声音校准**——你可以提供自己的写作风格样本，技能会匹配你的文风而非通用 AI 风格。

- **先读样本**：分析句子长度、用词水平、段落开头方式、标点习惯、过渡处理
- **匹配声音**：用样本中的模式来替换 AI 模式
- **回退行为**：未提供样本时，回退到自然、多样、有观点的默认声音

### Anti-AI 自审

Humanizer-zh 内置**自问自答审查步骤**：

1. 自问："这段文字哪里明显是 AI 写的？"
2. 简短回答剩余的 AI 痕迹
3. 自答："现在让它不再像 AI。"并修订

## 使用场景示例

#### 场景 1：改写营销文案

**输入：**
> 坐落在风景如画的杭州市中心，这家咖啡馆拥有丰富的文化底蕴和令人叹为观止的装饰。它作为城市咖啡文化的焦点，为顾客提供无缝、直观和充满活力的体验。

**输出：**
> 这家咖啡馆在杭州市中心开了三年，以手冲咖啡和老建筑改造的空间出名。

#### 场景 2：改写学术摘要

**输入：**
> 本研究深入探讨了机器学习在医疗诊断中的关键作用，突出了其在不断演变的医疗格局中的重要性。此外，它为该领域的未来发展奠定了坚实的基础。

**输出：**
> 本研究分析了机器学习在医疗诊断中的应用，重点是肺癌早期筛查。研究使用了 2019-2023 年间 5000 例病历数据。

#### 场景 3：改写博客文章

**输入：**
> 人工智能不仅仅是一种技术，它是我们思考未来的方式的革命。行业专家认为这将对整个社会产生持久影响。

**输出：**
> 我一直在想 AI 会怎么改变我们的工作方式。上周和几个做产品的朋友聊，有人觉得很兴奋，有人担心失业，大概率真相在中间某个无聊的地方。

## 关键原则

### ✨ 不仅要"干净"，更要"鲜活"

避免 AI 模式只是基础，好的写作需要真实的人类声音：

- **有观点** - 不要只报告事实，要对它们做出反应
- **变化节奏** - 混合使用长短句
- **承认复杂性** - 真实的人有复杂感受
- **适当使用"我"** - 第一人称是诚实的表现
- **允许一些混乱** - 完美的结构反而显得机械
- **对感受要具体** - 用具体细节替代抽象概括

## 常见 AI 词汇警示列表

以下词汇在 AI 生成文本中出现频率异常高：

`此外`、`至关重要`、`深入探讨`、`强调`、`持久的`、`增强`、`培养`、`获得`、`突出`、`相互作用`、`复杂/复杂性`、`格局`、`关键性的`、`展示`、`织锦`、`证明`、`宝贵的`、`充满活力的`……

## 文件说明

- **`SKILL.md`** - 中文版技能定义文件（完整指南）
- **`README.md`** - 本说明文档

**注：** 英文原版请参考 [blader/humanizer](https://github.com/blader/humanizer)

## 参考资源

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) - 原始指南来源（v2.5.1）
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) - 维基百科 AI 清理项目
- [blader/humanizer](https://github.com/blader/humanizer) - 原始英文版项目
- [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) - 实用工具部分的灵感来源

## 版本历史

- **2.5.1-zh** - 基于 blader/humanizer v2.5.1 重新翻译，合并 op7418 的核心规则和评分标准，目前支持 29 种模式。
- **2.5.0-zh** - 早期中文版，基于 blader v2.4.0（25 种模式）。
- **上游更新**：持续跟进 blader/humanizer 的模式增加与逻辑优化。

## 许可

本项目遵循 MIT 许可协议。


---

**提示：** 这个工具不是为了"欺骗" AI 检测器，而是为了真正提升写作质量。最好的"去 AI 化"方法是让文字有真实的人类思考和声音。
