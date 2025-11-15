# 核心雪花写作法 Subagents

本目录包含雪花写作法 10 个核心步骤的专业 subagents。

## 使用顺序

按照雪花写作法的标准流程，建议按以下顺序使用：

### 第一阶段：故事框架（步骤 1-4）

| 步骤 | Subagent | 功能 | 预计耗时 |
|-----|---------|------|---------|
| 1 | [story-concept-designer](../../.claude/agents/story-concept-designer.md) | 提炼一句话核心概念 | 2-4小时 |
| 2 | [three-act-architect](../../.claude/agents/three-act-architect.md) | 设计三幕式结构 | 3-6小时 |
| 3 | [character-storyline-weaver](../../.claude/agents/character-storyline-weaver.md) | 编织人物故事线 | 1-2天 |
| 4 | [synopsis-writer](../../.claude/agents/synopsis-writer.md) | 撰写一页纸概要 | 4-8小时 |

**产出：** 完整的故事框架，可用于投稿或团队讨论

---

### 第二阶段：人物深化（步骤 5-7）

| 步骤 | Subagent | 功能 | 预计耗时 |
|-----|---------|------|---------|
| 5 | [character-profiler](../../.claude/agents/character-profiler.md) | 构建详细人物档案 | 2-3天 |
| 6 | [outline-expander](../../.claude/agents/outline-expander.md) | 扩展为四页大纲 | 3-5天 |
| 7 | [character-bible-creator](../../.claude/agents/character-bible-creator.md) | 创建人物宝典 | 1-2天 |

**产出：** 深度的人物体系和完整大纲

---

### 第三阶段：场景设计与创作（步骤 8-10）

| 步骤 | Subagent | 功能 | 预计耗时 |
|-----|---------|------|---------|
| 8 | [scene-planner](../../.claude/agents/scene-planner.md) | 规划全书场景 | 2-4天 |
| 9 | [scene-designer](../../.claude/agents/scene-designer.md) | 详细设计每个场景 | 5-10天 |
| 10 | [manuscript-writer](../../.claude/agents/manuscript-writer.md) | 撰写正文 | 30-60天 |

**产出：** 完整的小说正文

---

## 快速开始

### 最小可行流程（快速验证）

```
步骤1 → 步骤2 → 步骤10
```

适合：短篇小说、概念验证、快速原型

### 标准流程（中长篇）

```
步骤1 → 步骤2 → 步骤3 → 步骤4 → 步骤8 → 步骤9 → 步骤10
```

适合：3-10万字的中长篇小说

### 完整流程（严肃创作）

```
步骤1 → 步骤2 → 步骤3 → 步骤4 → 步骤5 → 步骤6 → 步骤7 → 步骤8 → 步骤9 → 步骤10
```

适合：10万字以上的长篇、系列小说、商业出版

---

## 使用示例

### 示例1：科幻小说创作

```
用户：请 story-concept-designer 帮我设计一个科幻小说的核心概念。
      主题是数字永生与人性。

Claude：[调用 story-concept-designer]
        核心概念："当人类意识可以上传云端时，一个黑客发现
        死去的人仍在数字世界中受苦。"

        三要素评估：
        - 有趣：5/5（数字永生是热门话题）
        - 突兀：5/5（永生变折磨的反转）
        - 合理：4/5（符合技术伦理困境）
        总分：14/15

用户：很好！请 three-act-architect 扩展为三幕结构。

Claude：[调用 three-act-architect]
        [输出五句话的完整三幕式结构...]
```

### 示例2：迭代优化

```
用户：我发现主角的动机不够强，请 character-storyline-weaver
      重新设计，加入"寻找已故女友"的个人动机。

Claude：[调用 character-storyline-weaver]
        已更新主角林昭的故事线：
        - 新增深层动机：寻找女友的意识碎片
        - 外部目标不变：揭露公司罪行
        - 新增核心冲突：拯救女友 vs 拯救所有人
        [完整输出...]
```

---

## 工具权限说明

| Subagent | 工具权限 | 说明 |
|---------|---------|------|
| 步骤1-10 | Read, Write, Edit, Glob, Grep | 创作型，需要读写能力 |

所有核心 subagents 都具有完整的创作权限，可以读取参考材料、编写输出文档。

---

## 配合辅助工具

在使用核心步骤时，可以随时调用辅助专家：

- **genre-specialist**：验证类型特征
- **dialogue-master**：优化对话
- **pacing-controller**：调整节奏
- **consistency-checker**：检查一致性
- **editor-reviewer**：审阅修改

详见 [辅助专家目录](../02-auxiliary-experts/)

---

## 常见问题

**Q: 必须全部10步都做吗？**
A: 不必须。根据项目规模选择：短篇可以只做1、2、10；中篇建议1-4、8-10；长篇建议全做。

**Q: 可以跳着做吗？**
A: 前4步建议按顺序，步骤5-7可以灵活调整，步骤8-10可以分批进行。

**Q: 每个步骤要多详细？**
A: 前期步骤宁粗勿细（避免过早陷入细节），后期步骤越详细越好（减少正文创作时的困惑）。

---

## 学习资源

- [快速开始指南](../../docs/quick-start.md)
- [科幻小说完整示例](../../examples/sci-fi-novel.md)
- [雪花写作法原理](https://www.advancedfictionwriting.com/articles/snowflake-method/)

---

返回 [项目主页](../../README.md)
