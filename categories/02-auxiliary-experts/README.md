# 辅助专家 Subagents

本目录包含 5 个辅助专家工具，用于在创作过程中提供专业支持。

## 专家列表

| Subagent | 功能 | 使用时机 | 工具权限 |
|---------|------|---------|---------|
| [genre-specialist](../../.claude/agents/genre-specialist.md) | 类型专家 | 验证类型特征和规范 | Read, Grep, Glob, WebFetch, WebSearch |
| [dialogue-master](../../.claude/agents/dialogue-master.md) | 对话大师 | 优化人物对话 | Read, Write, Edit, Glob, Grep |
| [pacing-controller](../../.claude/agents/pacing-controller.md) | 节奏控制师 | 调整叙事节奏 | Read, Write, Edit, Glob, Grep |
| [consistency-checker](../../.claude/agents/consistency-checker.md) | 一致性检查师 | 检查前后一致性 | Read, Grep, Glob |
| [editor-reviewer](../../.claude/agents/editor-reviewer.md) | 编辑审阅师 | 全面审阅修改 | Read, Grep, Glob |

---

## 使用场景

### 1. genre-specialist - 类型专家

**何时使用：**
- 步骤3后：验证故事是否符合类型规范
- 步骤6后：检查大纲是否满足类型读者期待
- 正文创作中：获取类型特定的写作建议

**支持类型：**
- 科幻（硬科幻、软科幻、赛博朋克等）
- 言情（现言、古言、甜宠、虐文等）
- 悬疑推理（本格、社会派、心理惊悚等）
- 奇幻（高魔、低魔、都市奇幻等）
- 历史、武侠、都市、网文等

**示例：**
```
请 genre-specialist 从科幻小说角度评估我的世界观设定，
指出硬伤和可能的读者槽点。
```

---

### 2. dialogue-master - 对话大师

**何时使用：**
- 步骤9（场景设计）时：设计关键对话
- 步骤10（正文创作）时：优化已写对话
- 修改阶段：批量优化全书对话

**核心功能：**
- 设计角色专属语言风格
- 增加潜台词和张力
- 控制对话节奏
- 修复常见对话问题

**示例：**
```
这段对话太平淡了：
"你好。"
"你好，你是谁？"
"我是新来的。"

请 dialogue-master 重写，要求：增加张力、体现人物性格、有潜台词。
```

---

### 3. pacing-controller - 节奏控制师

**何时使用：**
- 步骤6后：检查大纲的整体节奏
- 每写完一幕：评估节奏是否合理
- 完稿后：全书节奏优化

**控制维度：**
- **宏观节奏**：全书的起承转合
- **中观节奏**：章节的快慢搭配
- **微观节奏**：场景内的张弛有度

**示例：**
```
我写完了前10章，感觉节奏有问题但说不出哪里。
请 pacing-controller 分析节奏并给出调整建议。
```

---

### 4. consistency-checker - 一致性检查师

**何时使用：**
- 步骤4后：检查概念到大纲的一致性
- 每写5-10章：检查人物、情节一致性
- 第二幕中点：全面检查
- 完稿后：最终审查

**检查维度：**
- **人物一致性**：性格、能力、说话方式
- **情节一致性**：因果逻辑、伏笔回收
- **世界观一致性**：设定、规则
- **时间线一致性**：事件顺序、角色年龄
- **细节一致性**：地名、物品、描述

**示例：**
```
请 consistency-checker 检查全书，重点关注：
1. 主角的能力是否前后矛盾
2. 时间线是否有错误
3. 重要伏笔是否都回收了
```

---

### 5. editor-reviewer - 编辑审阅师

**何时使用：**
- 初稿完成后：第一轮审阅
- 每次大修后：验证修改效果
- 投稿前：最终审查

**审阅维度：**
- **结构完整性**：三幕式结构是否清晰
- **人物塑造**：角色是否立体
- **语言质量**：文字表达、语法错误
- **主题深度**：主题是否得到充分展现
- **市场潜力**：商业价值评估
- **技术规范**：格式、标点等

**示例：**
```
请 editor-reviewer 全面审阅我的小说初稿（15万字），
提供分级修改建议（A/B/C级）。
```

---

## 组合使用示例

### 场景1：完稿后的全面优化

```bash
# 第一步：一致性检查
请 consistency-checker 全面检查一致性问题

# 第二步：修复问题后，优化对话
请 dialogue-master 优化第5、12、28章的对话场景

# 第三步：调整节奏
请 pacing-controller 评估全书节奏，重点看第二幕是否拖沓

# 第四步：最终审阅
请 editor-reviewer 进行最终审阅，提供修改建议

# 第五步：类型验证
请 genre-specialist 从科幻类型角度验证是否符合市场期待
```

### 场景2：单章优化流程

```bash
# 写完一章后
请依次执行：
1. consistency-checker 检查本章与前文的一致性
2. dialogue-master 优化本章对话
3. pacing-controller 评估本章节奏

然后告诉我需要修改的要点。
```

---

## 工具权限说明

### 研究型（有网络搜索）
- **genre-specialist**: `Read, Grep, Glob, WebFetch, WebSearch`
  - 可以查阅类型规范、市场趋势
  - 可以对比同类型作品

### 创作辅助型（可编辑）
- **dialogue-master**: `Read, Write, Edit, Glob, Grep`
- **pacing-controller**: `Read, Write, Edit, Glob, Grep`
  - 可以直接修改文本
  - 可以生成优化版本

### 只读审查型（不修改）
- **consistency-checker**: `Read, Grep, Glob`
- **editor-reviewer**: `Read, Grep, Glob`
  - 只分析不修改
  - 提供建议由作者决定

---

## 使用建议

### 频率建议

| 工具 | 建议频率 |
|-----|---------|
| genre-specialist | 步骤3后、步骤6后、完稿前 |
| dialogue-master | 每写重要对话场景 |
| pacing-controller | 每完成一幕（约3-5章） |
| consistency-checker | 每5-10章 + 完稿后 |
| editor-reviewer | 初稿后、每次大修后 |

### 优先级建议

**必用工具：**
- consistency-checker（避免低级错误）
- editor-reviewer（完稿前必审）

**强烈推荐：**
- pacing-controller（节奏是长篇小说的命门）

**按需使用：**
- dialogue-master（如果对话是弱项）
- genre-specialist（如果不熟悉该类型）

---

## 常见问题

**Q: 这些工具会不会让创作失去个性？**
A: 不会。这些是**辅助工具**，提供建议而非替代决策。你可以：
- 只采纳部分建议
- 要求调整建议方向
- 完全忽略某些建议

**Q: 检查出很多问题怎么办？**
A: 按**优先级修复**：
1. A级（必须修）：逻辑漏洞、重大矛盾
2. B级（应该修）：节奏问题、人物塑造
3. C级（可选修）：文字润色、细节优化

**Q: 多久用一次 consistency-checker？**
A: **越长的作品越频繁**：
- 短篇（<3万字）：完稿后1次
- 中篇（3-10万字）：中期1次 + 完稿1次
- 长篇（>10万字）：每5-10章 + 完稿1次

**Q: 可以让工具直接修改文本吗？**
A: **dialogue-master 和 pacing-controller 可以**，但建议：
1. 先看工具的修改建议
2. 选择性采纳
3. 保留原始版本以便回退

---

## 配合核心步骤使用

辅助专家最好与核心10步骤配合：

```
步骤1-2（框架）
    ↓
[genre-specialist 验证]
    ↓
步骤3-4（概要）
    ↓
[consistency-checker 检查]
    ↓
步骤5-7（人物深化）
    ↓
[genre-specialist 再次验证]
    ↓
步骤8-9（场景设计）
    ↓
[pacing-controller 评估节奏]
    ↓
步骤10（正文创作）
    ↓
[dialogue-master 优化对话]
[pacing-controller 调整节奏]
[consistency-checker 持续检查]
    ↓
完稿
    ↓
[editor-reviewer 全面审阅]
[genre-specialist 市场评估]
    ↓
定稿
```

---

## 学习资源

- [快速开始指南](../../docs/quick-start.md)
- [科幻小说示例](../../examples/sci-fi-novel.md)（展示了辅助工具的实际应用）

---

返回 [项目主页](../../README.md)
