# 雪花写作法 Claude Code Subagents

<div align="center">
    <strong>专为AI辅助小说创作设计的雪花写作法 Subagent 工具集</strong>
    <br />
    <br />
</div>

## 📖 项目简介

本项目基于 Randy Ingermanson 的**雪花写作法（Snowflake Method）**，为 Claude Code 设计了一套完整的小说创作 subagent 体系。通过将复杂的小说创作过程分解为 10 个渐进步骤，帮助作者系统化地构思、规划和撰写长篇小说。

### 什么是雪花写作法？

雪花写作法是一种从简单到复杂、层层递进的小说创作方法：
- 从**一句话概括**开始
- 逐步扩展为**完整大纲**
- 深入构建**人物档案**
- 最终完成**场景设计**和**正文写作**

就像雪花的形成过程一样，从简单的核心结构开始，通过不断迭代扩展，最终形成复杂而精美的完整形态。

## 🎯 为什么需要这个项目？

### 传统AI写作的痛点
- **缺乏整体规划**：直接让AI写小说往往导致情节混乱、人物崩坏
- **上下文丢失**：长篇创作中AI容易忘记前面的设定
- **风格不统一**：没有系统化流程，每次输出质量参差不齐

### 雪花写作法 Subagents 的优势
✅ **结构化创作流程**：10个专业 subagent 覆盖创作全流程
✅ **独立上下文管理**：每个 subagent 专注于特定任务，避免信息混乱
✅ **可复用性强**：一次创建，多个项目复用
✅ **循序渐进**：从概念到成稿，步步为营

## 🚀 快速开始

### 1. 安装使用

将 `.claude/agents/` 目录下的 subagent 文件复制到你的小说项目中：

```bash
# 复制所有 subagents 到你的项目
cp -r .claude/agents/* /your-novel-project/.claude/agents/

# 或者复制到全局配置（适用于所有项目）
cp -r .claude/agents/* ~/.claude/agents/
```

### 2. 创作流程

按照雪花写作法的 10 个步骤依次调用相应的 subagent：

```
第一阶段：故事框架（步骤 1-4）
→ 使用 story-concept-designer 提炼一句话故事梗概
→ 使用 three-act-architect 设计三幕式结构
→ 使用 character-storyline-weaver 编织人物故事线
→ 使用 synopsis-writer 生成一页纸大纲

第二阶段：人物深化（步骤 5-7）
→ 使用 character-profiler 创建详细人物档案
→ 使用 outline-expander 扩展四页完整大纲
→ 使用 character-bible-creator 建立人物宝典

第三阶段：场景设计（步骤 8-10）
→ 使用 scene-planner 规划所有场景
→ 使用 scene-designer 设计场景细节
→ 使用 manuscript-writer 开始正文写作
```

### 3. 示例对话

```
你：请 story-concept-designer 帮我提炼一个科幻小说的核心概念

Claude：[调用 story-concept-designer subagent]
已为您提炼核心概念：
"当人类意识可以上传云端时，一个黑客发现死去的人仍在数字世界中受苦。"
- ✅ 有趣：意识上传的设定引人入胜
- ✅ 突兀：死者受苦的反转出人意料
- ✅ 合理：符合科幻逻辑和伦理困境

你：很好！现在请 three-act-architect 帮我扩展成三幕结构

Claude：[调用 three-act-architect subagent]
...
```

## 📚 Subagent 列表

### 核心创作流程（10个）

| Subagent | 对应步骤 | 功能说明 | 输出内容 |
|---------|---------|---------|---------|
| **story-concept-designer** | 步骤1 | 故事核心概念设计 | 一句话梗概（<30字） |
| **three-act-architect** | 步骤2 | 三幕式结构设计 | 五句话的三幕结构 |
| **character-storyline-weaver** | 步骤3 | 人物故事线编织 | 各角色视角的故事线 |
| **synopsis-writer** | 步骤4 | 故事概要撰写 | 一页纸大纲 |
| **character-profiler** | 步骤5 | 人物档案构建 | 详细人物档案 |
| **outline-expander** | 步骤6 | 大纲扩展 | 四页完整大纲 |
| **character-bible-creator** | 步骤7 | 人物宝典编纂 | 五维度人物百科 |
| **scene-planner** | 步骤8 | 场景规划 | 场景列表与信息 |
| **scene-designer** | 步骤9 | 场景设计 | 场景详细设计 |
| **manuscript-writer** | 步骤10 | 正文撰写 | 小说正文 |

### 辅助专家工具（5个）

| Subagent | 功能说明 | 应用场景 |
|---------|---------|---------|
| **genre-specialist** | 类型专家 | 针对不同小说类型提供专业建议 |
| **dialogue-master** | 对话大师 | 打磨人物对话的真实感 |
| **pacing-controller** | 节奏控制师 | 调整叙事节奏 |
| **consistency-checker** | 一致性检查师 | 检查情节、人物、设定的一致性 |
| **editor-reviewer** | 编辑审阅师 | 审阅完成稿并提供修改建议 |

## 🛠️ Subagent 技术细节

### 工具权限设计

每个 subagent 根据其职能分配了最小必要权限：

**只读型 subagents**（一致性检查、编辑审阅）
```yaml
tools: Read, Grep, Glob
```

**创作型 subagents**（概念设计、大纲、人物、场景）
```yaml
tools: Read, Write, Edit, Glob, Grep
```

**研究型 subagents**（类型专家）
```yaml
tools: Read, Grep, Glob, WebFetch, WebSearch
```

### 标准结构

```yaml
---
name: subagent-name
description: 触发时机和功能描述
tools: Read, Write, Edit, Bash, Glob, Grep
---

你是一个 [角色描述]...

## 核心职责
- 职责1
- 职责2

## 工作流程
1. 步骤1
2. 步骤2

## 输出标准
- 标准1
- 标准2

## 质量检查清单
- [ ] 检查项1
- [ ] 检查项2
```

## 📖 使用示例

详细的使用示例请参见 [examples](./examples/) 目录：

- [科幻小说完整创作流程](./examples/sci-fi-novel.md)
- [言情小说创作示例](./examples/romance-novel.md)
- [悬疑推理创作指南](./examples/mystery-novel.md)

## 🎨 支持的小说类型

- 🚀 科幻小说
- 💖 言情小说
- 🔍 悬疑推理
- ⚔️ 奇幻冒险
- 📚 现实主义
- 🏛️ 历史小说
- 😊 轻小说
- 🌟 网络文学

## 🤝 贡献指南

欢迎贡献新的 subagent 或改进现有设计！

### 如何贡献

1. Fork 本项目
2. 创建特性分支 (`git checkout -b feature/AmazingSubagent`)
3. 提交更改 (`git commit -m 'Add some AmazingSubagent'`)
4. 推送到分支 (`git push origin feature/AmazingSubagent`)
5. 创建 Pull Request

### 贡献方向

- 新增更多辅助 subagent（如：世界观构建师、时间线管理器等）
- 针对特定类型优化的专业 subagent（如：武侠小说专家）
- 改进现有 subagent 的提示词质量
- 添加更多实战案例

## 📚 学习资源

- [雪花写作法官方网站](https://www.advancedfictionwriting.com/articles/snowflake-method/)
- [《雪花写作法：10步写出一篇好小说》](https://book.douban.com/subject/35931497/)
- [Claude Code 官方文档](https://docs.anthropic.com/claude-code)
- [VoltAgent 框架](https://github.com/voltagent/voltagent)

## 🙏 致谢

- **Randy Ingermanson** - 雪花写作法创始人
- **VoltAgent 社区** - awesome-claude-code-subagents 项目灵感来源
- **Anthropic** - Claude Code 工具支持

## 📄 开源协议

MIT License - 详见 [LICENSE](LICENSE)

## 🔗 相关项目

- [awesome-claude-code-subagents](https://github.com/VoltAgent/awesome-claude-code-subagents) - 软件开发 subagents 合集
- [VoltAgent](https://github.com/voltagent/voltagent) - AI Agent 框架

---

<p align="center">
  用 AI 和雪花写作法，让小说创作更系统、更高效 ❄️✨
</p>
